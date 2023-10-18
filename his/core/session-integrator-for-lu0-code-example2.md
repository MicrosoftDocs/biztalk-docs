---
description: "Learn more about: Session Integrator for LU0 Code Example"
title: "Session Integrator for LU0 Code Example"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Session Integrator for LU0 Code Example
The following code example shows how to use the primary techniques for creating an LU0 connection, logging on to the LU0 session, sending and receiving information, and terminating the connection.  
  
 For the complete code sample, see the \\\Microsoft Host Integration Server\SDK\Samples\AppInt\COMLU0 directory.  
  
## Example  
 The following example is from the CSClient.Form1 file in the COMLU0 sample.  
  
```  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Text;  
using System.Windows.Forms;  
using Microsoft.HostIntegration.SNA.Session;  
  
namespace CSClient  
{  
    public partial class Form1 : Form  
    {  
        private SessionLU0 _session = null;  
  
        // As the LU0 managed wrapper does no tracing  
        // we will trace the data contents to the provided text box.  
        private TextBox m_TextBox = null;  
        private Font m_FixedFont;  
  
        public Form1()  
        {  
            InitializeComponent();  
        }  
  
        private void SetOpeningState()  
        {  
            DisableEverything();  
  
            // Only the LU Name and Create Session are enabled.  
            this.CreateSession.Enabled = true;  
            this.LUName.Enabled = true;  
  
            m_TextBox = this.ScreenText;  
  
            // If we should trace, we need a fixed width font.  
            FontFamily fontFamily = new FontFamily("Courier New");  
            m_FixedFont = new Font(fontFamily, 10, FontStyle.Regular, GraphicsUnit.Pixel);  
  
            // Set up some things.  
            m_TextBox.WordWrap = false;  
            m_TextBox.Multiline = true;  
  
            // Find a fixed font.  
            m_TextBox.Font = m_FixedFont;  
        }  
  
        private void DisableEverything()  
        {  
            // All buttons are disabled.  
            this.CreateSession.Enabled = false;  
            this.InsertUserId.Enabled = false;  
            this.EnterDirector.Enabled = false;  
            this.Disconnect.Enabled = false;  
  
            // All text boxes are disabled.  
            this.LUName.Enabled = false;  
        }  
  
        private void EnableDisconnect()  
        {  
            // Just allow the Disconnect.  
            this.Disconnect.Enabled = true;  
        }  
  
        private void EnableInsertUserId()  
        {  
            // Enable the cics name / connect.  
            this.InsertUserId.Enabled = true;  
  
            // Enable the disconnect.  
            EnableDisconnect();  
        }  
  
        private void EnableEnterDirector()  
        {  
            // Enable clear screen.  
            this.EnterDirector.Enabled = true;  
  
            // Enable the disconnect.  
            EnableDisconnect();  
        }  
  
        private void Form1_Load(object sender, EventArgs e)  
        {  
            // Enable only the LU Name and Create.  
            SetOpeningState();  
        }  
  
        private void CreateSession_Click(object sender, EventArgs e)  
        {  
            try  
            {  
                LUName.Text = LUName.Text.Trim();  
                if (LUName.Text.Length == 0)  
                {  
                    MessageBox.Show("You must fill out the LU or Pool Name");  
                    return;  
                }  
  
                _session = new SessionLU0();  
                _session.Connect("LogicalUnitName=" + LUName.Text, SessionLU0InitType.SSCP);  
  
                // Receive the logon screen.  
                SessionLU0Data receivedData = _session.Receive(20000, true);  
  
                // Trace out the received data.  
                TraceData(false, receivedData.Data, receivedData.Indication);  
  
                // Disable every button and text box.  
                DisableEverything();  
  
                // Insert User/Password.  
                EnableInsertUserId();  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show(ex.Message);  
            }  
        }  
  
        private void InsertUserId_Click(object sender, EventArgs e)  
        {  
            try  
            {  
                // Disable every button and text box.  
                DisableEverything();  
  
                // Enter UserName (SNA200 is what is in the script).  
                // AID = 7D - Enter  
                byte AID = 0x7D;  
                // Cursor address.  
                byte ca1 = 0x5B;  
                byte ca2 = 0x6B;  
                // SBA  
                byte SBA = 0x11;  
                byte fa1 = 0x5B;  
                byte fa2 = 0xE5;  
  
                byte[] sna200 = HostStringConverter.ConvertUnicodeToEbcdic("SNA200");  
  
                byte sixD = 0x6D;  
  
                byte [] message = new byte [8 + sna200.Length ];  
                message[0] = AID;  
                message[1] = ca1;  
                message[2] = ca2;  
                message[3] = SBA;  
                message[4] = fa1;  
                message[5] = fa2;  
  
                Array.Copy(sna200, 0, message, 6, sna200.Length);  
  
                message[6 + sna200.Length] = sixD;  
                message[7 + sna200.Length] = sixD;  
  
                // Send the data.  
                SessionLU0Data data = new SessionLU0Data();  
                data.Data = message;  
  
                // Trace out the data to send.  
                TraceData(true, message, 0);  
  
                _session.Send(data);  
  
                // Allow entering director.  
                EnableEnterDirector();  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show(ex.Message);  
            }  
        }  
  
        private void EnterDirector_Click(object sender, EventArgs e)  
        {  
            try  
            {  
                // Disable every button and text box.  
                DisableEverything();  
  
                // Receive the Director screen.  
                SessionLU0Data receivedData = _session.Receive(20000, true);  
  
                // Trace out the received data.  
                TraceData(false, receivedData.Data, receivedData.Indication);  
  
                EnableDisconnect();  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show(ex.Message);  
            }  
        }  
  
        private void Disconnect_Click(object sender, EventArgs e)  
        {  
            // Disable every button and text box.  
            DisableEverything();  
  
            _session.Disconnect();  
  
            // Go back to the original state of buttons.  
            SetOpeningState();  
        }  
  
        // Print out the Data to a provided text box.  
        private void TraceData(bool sent, byte[] data, int indication)  
        {  
            if (m_TextBox == null)  
                return;  
  
            // Was the last thing sent or received?  
            if (sent)  
                m_TextBox.Text += "====>> Sent to Host" + Environment.NewLine;  
            else  
                m_TextBox.Text += "<<==== Received from Host" + Environment.NewLine;  
  
            // How much is there to trace.  
            int traceLength = data.Length;  
  
            m_TextBox.Text += "Size = " + traceLength.ToString();  
  
            if (!sent)  
                m_TextBox.Text += String.Format(", Indication = {0:X}", indication);  
  
            m_TextBox.Text += Environment.NewLine;  
  
            int numberTraced = 0;  
            while (numberTraced < traceLength)  
            {  
                string hexLine = "";  
                for (int i = 0; i < 16; i++)  
                {  
                    if (numberTraced + i >= traceLength)  
                        hexLine += "   ";  
                    else  
                        hexLine += String.Format("{0:x2} ", data[numberTraced + i]);  
                }  
  
                m_TextBox.Text += hexLine + Environment.NewLine;  
  
                numberTraced += 16;  
            }  
        }  
    }  
}  
```  
  
## See Also  
 [Session Integrator for LU0](../core/session-integrator-for-lu02.md)
