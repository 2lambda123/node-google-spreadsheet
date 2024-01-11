
2. Define the required scopes:
   ```javascript
   const SCOPES = ['https://www.googleapis.com/auth/spreadsheets', 'https://www.googleapis.com/auth/drive.file'];
   ```

3. Create a new instance of `GoogleSpreadsheet` with the API Key:
   ```javascript
   const doc = new GoogleSpreadsheet('<YOUR-DOC-ID>', { apiKey: process.env.GOOGLE_API_KEY });
