# idp-attr-rename-poc
This is a very simple PoC that allows renaming of a SAML attribute 
at runtime using Gluu SAML IDP scripting capabilities. It will take 
a source attribute (e.g. mail) and rename it to a target attribute 
(e.g. loginName) , while copying/maintaining the associated attribute 
value.

# Installation 

  Installation is pretty straightforward and consists of the following steps:

1 - Make sure the target SAML Attribute exists in Gluu as an attribute itself, and add it if it's not. 
    That can be done in oxTrust under `Configuration` > `Attributes`. 
    In case adding a Gluu attribute is not possible or desired, at the very least, a custom 
    attribute translation property file needs to be created in the Gluu Instance under 
    `/opt/shibboleth-idp/conf/attributes/custom`. An example is provided in the file 
    `loginName.properties` which will be used for the target attribute of the same name. It can be copied
    to the specified directory for test. 
    
2 - Add an IDP script in oxTrust under `Configuration` > `Other Authentication scripts`. Select the `Idp Extension`
    tab and click the `Add custom script` button. 
    Copy the contents of the file `idp_script.py` to the `Script` section. In the `Custom Property (key/value)`, add
    two entries. 
    The first will be `saml_source_attribute` and will have as value the name of the attribute to rewrite 
    The second will be `saml_target_attribute` and will have as value the new name of the attribute. 
    Make sure the script is enabled. Save the changes. 
    

# Usage  

  Simply set the script properties `saml_source_attribute` and `saml_target_attribute` to their appropriate values, and 
  make sure the script is enabled.
