# IIS SAML Configuration

## IIS Configuration in Windows 7

1. Start --> Control Panel --> Programs --> "Turn Windows features on or off"

2. Select (i) IIS (ii) Web Management Tools (iii) II6 Management Compatiability (iv) IIS Management Console (v) IIS Management Scripts and Tools (vi) IIS Management Service

3. Select (i) World Wide Web Services (ii) CGI (iii) ISAPI Filters (iv) ISAPI Extensions --> Press OK.
![IIS 7 Setup](https://raw.githubusercontent.com/GluuFederation/docs/master/sources/img/sp_setup/admin_sp_iis7setup.png)

4. Test IIS to see if it is installed in your system with "127.0.0.1" in the web browser. For our test case, we used IIS7.
![Test IIS](https://raw.githubusercontent.com/GluuFederation/docs/master/sources/img/sp_setup/admin_sp_iis7test.png)

## ISAPI Filter Configuration

1. Open IIS Manager (Start --> Administrative Tools --> Internet Information Service/IIS Manager)

2. Double click on "ISAPI and CGI Restrictions"
![ISAPI and CGI](https://raw.githubusercontent.com/GluuFederation/docs/master/sources/img/sp_setup/admin_sp_isapicgi.png)

3. Add a new Filter

  a. Click Actions --> Add (upper right corner)

  b. Select "\opt\shibboleth-sp\lib\shibboleth\isapi_shib.dll"

  c. Description: "Shibboleth"

  d. Click "Allow" (from the right hand side)

![ISAPI Path](https://raw.githubusercontent.com/GluuFederation/docs/master/sources/img/sp_setup/apache_sp_isapipath.png)

  e. Back to IIS Manager --> ISAPI Filters

![ISAPI Filters](https://raw.githubusercontent.com/GluuFederation/docs/master/sources/img/sp_setup/apache_sp_isapifilter.png)

        1. Click "Add" (upper right corner)

        2. Filter Name: Shibboleth

        3. Executable: "\opt\shibboleth-sp\lib\shibboleth\isapi_shib.dll"

![ISAPI Edit](https://raw.githubusercontent.com/GluuFederation/docs/master/sources/img/sp_setup/apache_sp_isapiedit.png)

  f. SSO file extension mapping

        1. Click on "Handler Mapping" from main page

![SP Handler](https://raw.githubusercontent.com/GluuFederation/docs/master/sources/img/sp_setup/admin_sp_handlermapping.png)

        2. Click "Add Script Map" from Action
![Script Map](https://raw.githubusercontent.com/GluuFederation/docs/master/sources/img/sp_setup/admin_sp_addscriptmap.png)

        3. Request Path :".sso"

        4. Executable should be pointed to "isapi_shib.dll"
![Executable](https://raw.githubusercontent.com/GluuFederation/docs/master/sources/img/sp_setup/admin_sp_executable.png)

  g. Restart IIS

  h. Check Status

  Check Status by typing in "http://127.0.0.1/Shibboleth.sso/Status" in the web browser. If it displays an XML document, then the Shibboleth SP Installation in Windows IIS7 in complete.
![Status Check](https://raw.githubusercontent.com/GluuFederation/docs/master/sources/img/sp_setup/admin_sp_checkstatus.png)

## Shibboleth SP Setup in Windows 2008 R2 with IIS7	