---
title: "Session Integrator for LU2 Code Example2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d6a8230-3bd3-412e-8710-c8445c584196
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Session Integrator for LU2 Code Example
The following code is from the 3270 application in the samples directory of the Host Integration Server SDK.  
  
## Example  
  
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
        private System.Drawing.Font m_FixedFont;  
        private SessionDisplay m_Handler = null;  
        private short m_row;  
        private short m_column;  
  
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
        }  
  
        private void DisableEverything()  
        {  
            // All Buttons are disabled.  
            this.CreateSession.Enabled = false;  
            this.ConnectCICS.Enabled = false;  
            this.SendCCLI.Enabled = false;  
            this.ClearScreen.Enabled = false;  
            this.FillIPAddress.Enabled = false;  
            this.FillPort.Enabled = false;  
            this.PerformTX.Enabled = false;  
            this.Disconnect.Enabled = false;  
  
            // All Text Boxes are disabled.  
            this.LUName.Enabled = false;  
            this.CICSName.Enabled = false;  
            this.IPAddress.Enabled = false;  
            this.PortNumber.Enabled = false;  
        }  
  
        private void EnableDisconnect()  
        {  
            this.Disconnect.Enabled = true;  
        }  
  
        private void EnableCICSElements()  
        {  
            // Enable the cics name / connect.  
            this.ConnectCICS.Enabled = true;  
            this.CICSName.Enabled = true;  
  
            // Enable the disconnect.  
            EnableDisconnect();  
        }  
  
        private void EnableClearScreen()  
        {  
            // Enable clear screen.  
            this.ClearScreen.Enabled = true;  
  
            // Enable the disconnect.  
            EnableDisconnect();  
        }  
  
        private void EnableCCLI()  
        {  
            // Enable Send CCLI.  
            this.SendCCLI.Enabled = true;  
  
            // Enable clear screen (and disconnect).  
            EnableClearScreen();  
        }  
  
        private void EnableIPInfo()  
        {  
            // Enable IP Address, Port Number and Fill Buttons.  
            this.IPAddress.Enabled = true;  
            this.PortNumber.Enabled = true;  
            this.FillIPAddress.Enabled = true;  
            this.FillPort.Enabled = true;  
  
            this.PerformTX.Enabled = true;  
  
            // Enable clear screen (and disconnect).  
            EnableClearScreen();  
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
                m_Handler = new SessionDisplay();  
  
                m_Handler.Connect("TRANSPORT=SNA;LOGICALUNITNAME=" + LUName.Text);  
                m_Handler.Connection.HostCodePage = 37;  
  
                FontFamily fontFamily = new FontFamily("Courier New");  
                m_FixedFont = new Font(fontFamily, 10, FontStyle.Regular, GraphicsUnit.Pixel);  
                ScreenText.Font = m_FixedFont;  
                TraceScreen();  
  
                // Disable every button and text box.  
                DisableEverything();  
  
                m_Handler.WaitForContent("TERM NAME", 20000);  
                TraceScreen();  
  
                // Enable Connect to CICS and Disconnect Session.  
                EnableCICSElements();  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show(ex.Message);  
            }  
        }  
  
        private void ConnectCICS_Click(object sender, EventArgs e)  
        {  
            try  
            {  
                CICSName.Text = CICSName.Text.Trim();  
                if (CICSName.Text.Length == 0)  
                {  
                    MessageBox.Show("You must fill out the CICS Name");  
                    return;  
                }  
  
                // Disable every button and text box.  
                DisableEverything();  
  
                m_Handler.SendKey(CICSName.Text + "@E");  
                TraceScreen();  
  
                m_Handler.WaitForSession (SessionDisplayWaitType.PLUSLU, 5000);  
                TraceScreen();  
  
                m_Handler.WaitForContent(@"DEMONSTRATION", 20000);  
                TraceScreen();  
  
                // Enable clear screen.  
                EnableClearScreen();  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show(ex.Message);  
            }  
        }  
  
        private void ClearScreen_Click(object sender, EventArgs e)  
        {  
            try  
            {  
                // Disable every button and text box.  
                DisableEverything();  
  
                m_Handler.SendKey("@C");  
                TraceScreen();  
  
                m_Handler.WaitForSession(SessionDisplayWaitType.NotBusy, 5000);  
                TraceScreen();  
  
                // Enable enter ccli.  
                EnableCCLI();  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show(ex.Message);  
            }  
        }  
  
        private void SendCCLI_Click(object sender, EventArgs e)  
        {  
            try  
            {  
                // Disable every button and text box.  
                DisableEverything();  
  
                m_Handler.SendKey("CCLI@E");  
                TraceScreen();  
  
                m_Handler.WaitForContent("Call duration in milliseconds", 20000);  
                TraceScreen();  
  
                // Get the Jane Doe cursor Position.  
                m_row = m_Handler.Cursor.Row;  
                m_column = m_Handler.Cursor.Column;  
  
                // Enable IP Address, Port and Perform Transaction.  
                EnableIPInfo();  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show(ex.Message);  
            }  
        }  
  
        private void FillIPAddress_Click(object sender, EventArgs e)  
        {  
            try  
            {  
                IPAddress.Text = IPAddress.Text.Trim();  
                if (IPAddress.Text.Length == 0)  
                {  
                    MessageBox.Show("You must fill out the IP Address");  
                    return;  
                }  
  
                // Tab to the correct place from First Field.  
                m_Handler.Cursor.Row = m_row;  
                m_Handler.Cursor.Column = m_column;  
                m_Handler.SendKey("@T@T");  
                TraceScreen();  
  
                m_Handler.SendKey(IPAddress.Text);  
                TraceScreen();  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show(ex.Message);  
            }  
        }  
  
        private void FillPort_Click(object sender, EventArgs e)  
        {  
            try  
            {  
                PortNumber.Text = PortNumber.Text.Trim();  
                if (PortNumber.Text.Length == 0)  
                {  
                    MessageBox.Show("You must fill out the Port Number");  
                    return;  
                }  
  
                // Tab to the correct place from First Field.  
                m_Handler.Cursor.Row = m_row;  
                m_Handler.Cursor.Column = m_column;  
                m_Handler.SendKey("@T@T@T");  
                TraceScreen();  
  
                m_Handler.SendKey(PortNumber.Text);  
                TraceScreen();  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show(ex.Message);  
            }  
        }  
  
        private void PerformTX_Click(object sender, EventArgs e)  
        {  
            try  
            {  
                // Disable every button and text box.  
                DisableEverything();  
  
                m_Handler.SendKey("@E");  
                TraceScreen();  
  
                // Wait for screen to calm down.  
                m_Handler.WaitForSession(SessionDisplayWaitType.NotBusy, 5000);  
                TraceScreen();  
  
                // See if the Balance Field is filled out.  
                m_Handler.Cursor.Row = m_row;  
                m_Handler.Cursor.Column = m_column;  
                TraceScreen();  
                // Tab to the Account Number field.  
                m_Handler.SendKey("@T");  
                TraceScreen();  
                // Move to the Next Field (Empty Stuff after 123456).  
                m_Handler.MoveNextField();  
                TraceScreen();  
                // Move to the Next Field (Title, Account Balance).  
                m_Handler.MoveNextField();  
                TraceScreen();  
                // Move to the Next Field (Account Balance).  
                m_Handler.MoveNextField();  
                TraceScreen();  
  
                // Extract Data from this field.  
                string accountBalance = m_Handler.CurrentField.Data;  
  
                // Trim the string.  
                accountBalance = accountBalance.Trim();  
  
                // Only things to do now are clear screen or disconnect.  
                EnableClearScreen();  
  
                // If we failed (not Abended) then this field will be blank.  
                if (accountBalance.Length == 0)  
                    throw new Exception("Failed to get Account Balance");  
                else  
                    MessageBox.Show(accountBalance, "Account Balance");  
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
  
            m_Handler.Disconnect();  
  
            // Go back to the original state of buttons.  
            SetOpeningState();  
        }  
  
        // Get the Unicode version of the Screen.  
        public String CurrentScreen()  
        {  
            if (m_Handler == null)  
                throw new Exception("C3270_E_NOT_CONNECTED");  
  
            String screen = null;  
  
            ScreenData screenData = m_Handler.GetScreenData(1, 1, -1);  
  
            // Convert the EBCDIC to Unicode.  
            screen = HostStringConverter.ConvertEbcdicToUnicode(screenData.Data);  
  
            return screen;  
        }  
  
        // Print out the 3270 screen to a provided text box.  
        private void TraceScreen()  
        {  
            // If we are not connected, no info.  
            if (m_Handler == null)  
            {  
                ScreenText.ResetText();  
                return;  
            }  
  
            string screen = CurrentScreen();  
            short rows = m_Handler.Rows;  
            short columns = m_Handler.Columns;  
  
            ScreenText.ResetText();  
            for (int i = 0; i < rows; i++)  
            {  
                ScreenText.Text += (i != 0 ? Environment.NewLine : "") + screen.Substring(columns * i, columns);  
            }  
  
            // Add a divider.  
            ScreenText.Text += Environment.NewLine + new string('-', (int)columns);  
  
            ScreenText.Refresh();  
        }  
    }  
}  
```