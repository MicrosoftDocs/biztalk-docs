---
title: "Custom Modal Dialog Editor for Adapter Configuration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 213d5d47-80c1-4b2d-8194-1426982be137
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Custom Modal Dialog Editor for Adapter Configuration
The code for the custom editor shows an editor derived from the **System.Drawing.Design.UITypeEditor** class that displays a modal pop-up dialog box for entering a password. The **GetEditStyle** method override returns **UIEditorEditStyle.Modal** to indicate a modal form subcontrol. The service method **ShowDialog** manages the control created with **CreatePassword**. **ShowDialog** returns a **DialogResult** that is handled in the usual way (for example, a switch statement) with the **DialogResult.OK** case changing value only.  
  
 The following code is the class definition for the custom modal editor:  
  
```  
/*************************************************************************  
 * Copyright (c) 1999-2004 Microsoft Corporation. All rights reserved.   *  
 *                                                                       *  
 * THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF ANY *  
 * KIND, WHETHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE  *  
 * IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A PARTICULAR *  
 * PURPOSE. THE ENTIRE RISK OF USE OR RESULTS IN CONNECTION WITH THE USE *  
 * OF THIS CODE AND INFORMATION REMAINS WITH THE USER.                   *  
 *************************************************************************/  
  
using System;  
using System.ComponentModel;  
using System.Drawing.Design;  
using System.Windows.Forms;  
using System.Windows.Forms.Design;  
using System.Security;  
using System.Security.Permissions;  
using Microsoft.BizTalk.Adapter.Framework;  
using Microsoft.BizTalk.Adapter.Framework.Forms;  
  
namespace AdapterManagement.ComponentModel  
{  
    /// <summary>  
    /// PasswordUITypeEditor implements a user interface for acquiring passwords  
    /// within a visual designer.  
    /// </summary>  
    public class PasswordUITypeEditor : UITypeEditor  
    {  
        public const char PasswordChar = '\u25cf';  
        private IWindowsFormsEditorService _service = null;  
        private PasswordForm _password = null;  
  
        [SecurityPermissionAttribute(SecurityAction.LinkDemand)]  
        public override UITypeEditorEditStyle GetEditStyle(ITypeDescriptorContext context)  
        {  
            if (null != context && null != context.Instance)  
            {  
                return UITypeEditorEditStyle.Modal;  
            }  
            return base.GetEditStyle(context);  
        }  
  
        [SecurityPermissionAttribute(SecurityAction.LinkDemand)]  
        public override object EditValue(ITypeDescriptorContext context,  
                                 IServiceProvider provider,  
                                 object value)  
        {  
            if (null != context && null != context.Instance && null != provider)  
            {  
                this._service = (IWindowsFormsEditorService)provider.GetService  
                            (typeof(IWindowsFormsEditorService));  
                if (null != this._service)  
                {  
                    if (null == this._password)  
                    {  
                        this._password = CreatePassword();  
                    }  
                    switch (this._service.ShowDialog(this._password))  
                    {  
                        case DialogResult.OK:  
                            value = this._password;  
                            break;  
                        case DialogResult.Cancel:  
                            break;  
                    }  
                }  
            }  
            return value;  
        }  
  
        private PasswordForm CreatePassword()  
        {  
            return new PasswordForm(PasswordUITypeEditor.PasswordChar);  
```  
  
 The following code is the class definition for the custom dialog box:  
  
```  
/*************************************************************************  
 * Copyright (c) 1999-2004 Microsoft Corporation. All rights reserved.   *  
 *                                                                       *  
 * THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF ANY *  
 * KIND, WHETHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE  *  
 * IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A PARTICULAR *  
 * PURPOSE. THE ENTIRE RISK OF USE OR RESULTS IN CONNECTION WITH THE USE *  
 * OF THIS CODE AND INFORMATION REMAINS WITH THE USER.                   *  
 *************************************************************************/  
using System;  
using System.ComponentModel;  
using System.Drawing.Design;  
using System.Windows.Forms;  
using System.Windows.Forms.Design;  
using System.Security;  
using System.Security.Permissions;  
  
namespace Microsoft.BizTalk.Samples.CustomUITypeEditors  
{  
    public class PasswordUITypeEditor : UITypeEditor  
    {  
        public const char PasswordChar = '\u25cf';  
        private IWindowsFormsEditorService _service = null;  
        private PasswordForm _password = null;  
  
        [SecurityPermissionAttribute(SecurityAction.LinkDemand)]  
        public override UITypeEditorEditStyle GetEditStyle(ITypeDescriptorContext context)  
        {  
            if (null != context && null != context.Instance)  
            {  
                return UITypeEditorEditStyle.Modal;  
            }  
            return base.GetEditStyle(context);  
        }  
  
        [SecurityPermissionAttribute(SecurityAction.LinkDemand)]  
        public override object EditValue(ITypeDescriptorContext context,  
                                 IServiceProvider provider,  
                                 object value)  
        {  
            if (null != context && null != context.Instance && null != provider)  
            {  
                this._service = (IWindowsFormsEditorService)provider.GetService  
                            (typeof(IWindowsFormsEditorService));  
                if (null != this._service)  
                {  
                    if (null == this._password)  
                    {  
                        this._password = new PasswordForm();  
                    }  
                    switch (this._service.ShowDialog(this._password))  
                    {  
                        case DialogResult.OK:  
                            value = this._password.Password;  
                            break;  
                        case DialogResult.Cancel:  
                            break;  
                    }  
                }  
            }  
            return value;  
        }  
    }   
}  
  
      namespace Microsoft.BizTalk.Samples.CustomUITypeEditors  
{  
    partial class PasswordForm  
    {  
        /// <summary>  
        /// Required designer variable.  
        /// </summary>  
        private System.ComponentModel.IContainer components = null;  
  
        /// <summary>  
        /// Clean up any resources being used.  
        /// </summary>  
        /// <param name="disposing">true if managed resources should be disposed; otherwise, false.</param>  
        protected override void Dispose(bool disposing)  
        {  
            if (disposing && (components != null))  
            {  
                components.Dispose();  
            }  
            base.Dispose(disposing);  
        }  
  
        #region Windows Form Designer generated code  
  
        /// <summary>  
        /// Required method for Designer support - do not modify  
        /// the contents of this method with the code editor.  
        /// </summary>  
        private void InitializeComponent()  
        {  
            this.passwordTextBox = new System.Windows.Forms.TextBox();  
            this.confirmTextBox = new System.Windows.Forms.TextBox();  
            this.passwordLabel = new System.Windows.Forms.Label();  
            this.confirmLabel = new System.Windows.Forms.Label();  
            this._separator = new System.Windows.Forms.GroupBox();  
            this.okButton = new System.Windows.Forms.Button();  
            this.cancelButton = new System.Windows.Forms.Button();  
            this.SuspendLayout();  
            //   
            // passwordTextBox  
            //   
            this.passwordTextBox.Location = new System.Drawing.Point(106, 16);  
            this.passwordTextBox.Name = "passwordTextBox";  
            this.passwordTextBox.PasswordChar = '*';  
            this.passwordTextBox.Size = new System.Drawing.Size(189, 20);  
            this.passwordTextBox.TabIndex = 0;  
            //   
            // confirmTextBox  
            //   
            this.confirmTextBox.Location = new System.Drawing.Point(106, 58);  
            this.confirmTextBox.Name = "confirmTextBox";  
            this.confirmTextBox.PasswordChar = '*';  
            this.confirmTextBox.Size = new System.Drawing.Size(189, 20);  
            this.confirmTextBox.TabIndex = 1;  
            //   
            // passwordLabel  
            //   
            this.passwordLabel.AutoSize = true;  
            this.passwordLabel.Font = new System.Drawing.Font("Microsoft Sans Serif", 9.75F, System.Drawing.FontStyle.Regular, System.Drawing.GraphicsUnit.Point, ((byte)(0)));  
            this.passwordLabel.Location = new System.Drawing.Point(19, 17);  
            this.passwordLabel.Name = "passwordLabel";  
            this.passwordLabel.Size = new System.Drawing.Size(71, 16);  
            this.passwordLabel.TabIndex = 2;  
            this.passwordLabel.Text = "Password:";  
            //   
            // confirmLabel  
            //   
            this.confirmLabel.AutoSize = true;  
            this.confirmLabel.Font = new System.Drawing.Font("Microsoft Sans Serif", 9.75F, System.Drawing.FontStyle.Regular, System.Drawing.GraphicsUnit.Point, ((byte)(0)));  
            this.confirmLabel.Location = new System.Drawing.Point(34, 58);  
            this.confirmLabel.Name = "confirmLabel";  
            this.confirmLabel.Size = new System.Drawing.Size(56, 16);  
            this.confirmLabel.TabIndex = 3;  
            this.confirmLabel.Text = "Confirm:";  
            //   
            // _separator  
            //   
            this._separator.Anchor = ((System.Windows.Forms.AnchorStyles)(((System.Windows.Forms.AnchorStyles.Bottom | System.Windows.Forms.AnchorStyles.Left)  
                        | System.Windows.Forms.AnchorStyles.Right)));  
            this._separator.Location = new System.Drawing.Point(12, 84);  
            this._separator.Name = "_separator";  
            this._separator.Size = new System.Drawing.Size(287, 10);  
            this._separator.TabIndex = 7;  
            this._separator.TabStop = false;  
            //   
            // okButton  
            //   
            this.okButton.Location = new System.Drawing.Point(123, 113);  
            this.okButton.Name = "okButton";  
            this.okButton.Size = new System.Drawing.Size(75, 23);  
            this.okButton.TabIndex = 8;  
            this.okButton.Text = "OK";  
            this.okButton.UseVisualStyleBackColor = true;  
            this.okButton.Click += new System.EventHandler(this.okButton_Click);  
            //   
            // cancelButton  
            //   
            this.cancelButton.DialogResult = System.Windows.Forms.DialogResult.Cancel;  
            this.cancelButton.Location = new System.Drawing.Point(220, 113);  
            this.cancelButton.Name = "cancelButton";  
            this.cancelButton.Size = new System.Drawing.Size(75, 23);  
            this.cancelButton.TabIndex = 9;  
            this.cancelButton.Text = "Cancel";  
            this.cancelButton.UseVisualStyleBackColor = true;  
            //   
            // PasswordForm  
            //   
            this.AutoScaleDimensions = new System.Drawing.SizeF(6F, 13F);  
            this.AutoScaleMode = System.Windows.Forms.AutoScaleMode.Font;  
            this.ClientSize = new System.Drawing.Size(311, 141);  
            this.Controls.Add(this.cancelButton);  
            this.Controls.Add(this.okButton);  
            this.Controls.Add(this._separator);  
            this.Controls.Add(this.confirmLabel);  
            this.Controls.Add(this.passwordLabel);  
            this.Controls.Add(this.confirmTextBox);  
            this.Controls.Add(this.passwordTextBox);  
            this.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedSingle;  
            this.Name = "PasswordForm";  
            this.Text = "PasswordForm";  
            this.ResumeLayout(false);  
            this.PerformLayout();  
  
        }  
  
        #endregion  
  
        private System.Windows.Forms.TextBox passwordTextBox;  
        private System.Windows.Forms.TextBox confirmTextBox;  
        private System.Windows.Forms.Label passwordLabel;  
        private System.Windows.Forms.Label confirmLabel;  
        private System.Windows.Forms.GroupBox _separator;  
        private System.Windows.Forms.Button okButton;  
        private System.Windows.Forms.Button cancelButton;  
  
    }  
}  
```  
  
## See Also  
 [Custom Adapter Configuration Designer](../core/custom-adapter-configuration-designer.md)   
 [Custom Drop-Down Editor for Adapter Configuration](../core/custom-drop-down-editor-for-adapter-configuration.md)   
 [Custom Type Converter for Adapter Configuration](../core/custom-type-converter-for-adapter-configuration.md)   
 [Advanced Configuration Components for Adapters](../core/advanced-configuration-components-for-adapters.md)