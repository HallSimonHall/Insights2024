# Bartender REST API
 This presentation details the steps for creating a Bartender label using the Bartender REST API.  It also compares the other methods that you have available for creating labels using the standard Epicor methods and using the Bartender Integration Web Services.

# 1. Bartender REST API (POST)
    - Requires Print Portal to be installed
    - Can use BTXML, YAML and JSON payloads
    - Use Named Data sources in the label

# 2. Bartender Inegration Web Service (GET/POST)
    - Requires a web service integration to be built
    - Can send data in the url (GET) however limited to amount of data that can be sent
    - Can send data in body of the request (unlimited Data), csv appears to be the most succesful
    - Use Named Data sources in the label

# 3. Epicor Standard File Drop. UBAQ file Drop, Function File Drop methods
- Use database source for label
- require the creation of a file with BT command script in the first row of the file.
 

