# Bartender REST API - Bartender 2022 R8 and Epicor Kinetic (2022.1)
 This presentation details the steps for creating a Bartender label using the Bartender REST API.  It also compares the other methods that you have available for creating labels using the standard Epicor methods and using the Bartender Integration Web Services.

# 1. Bartender REST API (POST)
- Requires Print Portal to be installed.
- Can use BTXML, YAML and JSON payloads.
- Use Named Data sources in the label.

# 2. Bartender Inegration Web Service (GET/POST)
- Requires a web service integration to be built.
- Can send data in the url (GET) however limited to amount of data that can be sent.
- Can send data in body of the request (unlimited Data), csv appears to be the most succesful.
- Use Named Data sources in the label.

# 3. Epicor Standard File Drop. UBAQ file Drop, Function File Drop methods
- Use database source for label.
- require the creation of a file with BT command script in the first row of the file.
 
# 4. Additional Misc
- Operating Bartender independently of the App server modify your /net6.0/appsettings.json if not yuou will receive 403 "Remote Access not allowed" errors
-    "RemoteAccess": {
      "Allowed":  true
   }
- Note NTLM is depricated in Server 2025 and Windows 11 24H2 at this stage seagull only use Token auth on Bartender cloud.
- By default the REST API print jobs only exist for 60 minutes so if you attempt to query the API with the generated GUID response to review the status of the job after that period you will get no result (or possibly an error).

# 5. Functions
- Helpers-Demo/ExecuteBAQ. Accepts BAQ name and delimited parameters pair list eg JobNum:1234~Plant:MAIN
  
- BTREST/BTRESTDirect-OneLabel Prints one label only given the signature.  Uses one PrintBTWAction
  - labelName: Label template file name eg.REST_DIRECT_Label.btw
  - BAQParams: Tilde Delimitted : pair delimitted baq parameters eg. CustID:1234~PartNum:1034Knut
  - BAQName: BAQ ID
  - IsAction: Set to false if you wish to try and modify for Integration Web Services.

- BTREST/BTRESTDirect-ManyLabel Prints many labels given the sigunature and uses Action groups
  - labelName: Label template file name eg.REST_DIRECT_Label.btw
  - BAQParams: Tilde Delimitted : pair delimitted baq parameters eg. CustID:1234~PartNum:1034Knut
  - BAQName: BAQ ID
  - IsAction: Set to false if you wish to try and modify for Integration Web Services.

# 6. Future Enhancements
- Making more use of User codes to store the label template file names and the related BAQ to be executed within them rather that passing into the function.
- Improved internal logging rather that relying on the excellent History Explorer
- Improved Error handling.

# 7. Authors Note
Feel free to modify to suit your needs. I hope you find this useful.

  
