---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: TRUE

ROBOTS: NOINDEX
--- 

# Deployment Limitations
The Transport Adapter password is stored as asterisks (\*\*\*\*\*\*) in the binding file that is exported by BizTalk Deployment Wizard, and is passed to the management component in the same format. Edit the binding file before importing by replacing the asterisks with random alphanumeric values (that is, not the correct password). Then enter the correct password using the **Transport Properties** page after importing the binding file.  
  
 When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports. This prevents password information from appearing in clear text. The next time you use the file to import the binding information, you must enter the passwords by using transport property pages user interface. Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it. In this case, you must delete the passwords from the binding file after the import operation successfully completes.  
  

## Password Limitation Workaround  
 Use one of the following as a work-around for the password limitation.  
  
#### To work around the password limitation  
  
1. Edit the binding file before importing by replacing the stars with plain text.  
  
   > [!CAUTION]
   >  This is not recommended for security reasons.  
  
2. Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password). Enter the correct password using the **Transport Properties** page after importing the binding file.  
  
   > [!NOTE]
   >  This work-around can be used only if Microsoft Visual Studio is installed on the target computer or by developing a custom tool.  
  
   **-OR-**  
  
#### To work around the password limitation  
  
1.  Use Enterprise Single Sign-On instead of using passwords.  
  
     Using the SSO option requires no extra work; only an import of the binding file.  
  
2.  Verify the Logical system and the Transmit and Receive services.  
  
## See Also  
 [Add the artifacts to BizTalk Administration](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)   
 [Import the JD Edwards OneWorld app](deploying-biztalk-adapter-for-jd-edwards-oneworld.md)