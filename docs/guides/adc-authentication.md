# ADC Authentication

To authenticate with the Google Sheets API using Application Default Credentials (ADC), follow these steps:

1. Import the necessary modules:
   ```javascript
   const { GoogleAuth } = require('google-auth-library');
   const { GoogleSpreadsheet } = require('google-spreadsheet');
   ```

2. Define the required scopes:
   ```javascript
   const SCOPES = ['https://www.googleapis.com/auth/spreadsheets', 'https://www.googleapis.com/auth/drive.file'];
   ```

3. Create a new instance of `GoogleAuth` with the defined scopes:
   ```javascript
   const adcAuth = new GoogleAuth({
     scopes: SCOPES,
   });
   ```

4. Create a new instance of `GoogleSpreadsheet` with the ADC authentication:
   ```javascript
   const doc = new GoogleSpreadsheet('<YOUR-DOC-ID>', adcAuth);
   ```

5. Include the necessary code snippets and instructions for setting up ADC credentials, initializing the `GoogleAuth` object, and creating the `GoogleSpreadsheet` object.

6. Remember to handle token storage securely and refresh tokens when necessary to ensure uninterrupted access to the Google Sheets API.

For more information on ADC authentication, refer to the [Google Identity documentation](https://developers.google.com/identity/protocols/oauth2#application-default-credentials).
