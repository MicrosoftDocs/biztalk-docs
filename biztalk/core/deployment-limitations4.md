---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone/
redirect_document_id: TRUE

ROBOTS: NOINDEX
--- 

# Deployment Limitations
The Transport Adapter password is stored as stars (******) in the binding file that is exported by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and it passes to the management component in the same format. Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).  
  
 When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports. This prevents password information from appearing in clear text. The next time you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.  
  
 Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it. In this case, you must delete the passwords from the binding file after the import operation successfully completes.  
  
## Password Limitation Workaround  
 To work around the password limitation, you can do the following.  
  
#### To work around the password limitation  
  
1.  Use Enterprise Single Sign-On instead of using passwords. Using the SSO option requires no extra work; only an import of the binding file.  
  
2.  Verify the Logical system and the Transmit and Receive services.  
  
## See Also  
 [Import the JD Edwards EnterpriseOne app](../core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone.md)