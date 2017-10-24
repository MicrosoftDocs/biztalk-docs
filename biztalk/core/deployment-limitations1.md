---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-tibco-enterprise-message-service/
redirect_document_id: TRUE

ROBOTS: NOINDEX
--- 

# Deployment Limitations
The Transport Adapter password is stored as stars (\*\*\*\*\*\*) in the binding file that is exported by BizTalk Server, and it passes to the management component in the same format. Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password). Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.  
  
 This is a known limitation. When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports. This prevents password information from appearing in clear text. The next time that you use the file to import the binding information, you must enter the passwords by using transport property pages user interface. Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it. In this case, you must delete the passwords from the binding file after the import operation successfully finishes.  
  
  
## Password Limitation Workaround  
 To work around this password limitation, you can use one of the following methods:  
  
-   Edit the binding file before importing by replacing the stars with plain text.  
  
> [!CAUTION]
>  This is not recommended for security reasons.  
  
-   Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password). Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.  
  
> [!NOTE]
>  This work-around can be used only if Visual Studio is installed on the target computer, or if you develop a custom tool.  
  
-   Verify the Logical system and the Transmit and Receive services.  
  
