# OAuth 2.0 Authentication

To authenticate with the Google Sheets API using OAuth 2.0, follow these steps:

1. Import the necessary modules:
   ```javascript
   const { OAuth2Client } = require('google-auth-library');
   const { GoogleSpreadsheet } = require('google-spreadsheet');
   ```

2. Define the required scopes:
   ```javascript
   const SCOPES = ['https://www.googleapis.com/auth/spreadsheets', 'https://www.googleapis.com/auth/drive.file'];
   ```

3. Create an OAuth2Client object with your app's OAuth credentials:
   ```javascript
   const oauthClient = new OAuth2Client({
     clientId: process.env.GOOGLE_OAUTH_CLIENT_ID,
     clientSecret: process.env.GOOGLE_OAUTH_CLIENT_SECRET,
   });
   ```

4. Pre-configure the OAuth2Client with the user's tokens:
   ```javascript
   const { accessToken, refreshToken, expiryDate } = await fetchUserGoogleCredsFromDatabase();
   oauthClient.credentials.access_token = accessToken;
   oauthClient.credentials.refresh_token = refreshToken;
   oauthClient.credentials.expiry_date = expiryDate; // Unix epoch milliseconds
   ```

5. Listen for token events to handle token refresh:
   ```javascript
   oauthClient.on('tokens', (credentials) => {
     console.log(credentials.access_token);
     console.log(credentials.scope);
     console.log(credentials.expiry_date);
     console.log(credentials.token_type); // will always be 'Bearer'
   });
   ```

6. Create a new GoogleSpreadsheet object with the OAuth2Client:
   ```javascript
   const doc = new GoogleSpreadsheet('<YOUR-DOC-ID>', oauthClient);
   ```

7. Include the necessary code snippets and instructions for setting up OAuth 2.0 credentials, generating authorization URLs, exchanging authorization codes for access tokens, and storing and refreshing tokens.

For more information on OAuth 2.0 authentication, refer to the [Google Identity documentation](https://developers.google.com/identity/protocols/oauth2).

Remember to handle token storage securely and refresh tokens when necessary to ensure uninterrupted access to the Google Sheets API.
