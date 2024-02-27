import { JWT } from 'google-auth-library';

import creds from './config/myapp-1dd646d7c2af.json'; // Replace with your JSON key file

const SCOPES = [
  'https://www.googleapis.com/auth/spreadsheets',
  'https://www.googleapis.com/auth/drive.file',
];

const jwt = new JWT({
  email: creds.client_email,
  key: creds.private_key,
  scopes: SCOPES,
});

const doc = new GoogleSpreadsheet('<YOUR-DOC-ID>', jwt);
```

### Loading Credentials from Environment Variables

To load the service account credentials from environment variables, you can modify the code as follows:

```javascript
const jwtFromEnv = new JWT({
  email: process.env.GOOGLE_SERVICE_ACCOUNT_EMAIL,
  key: process.env.GOOGLE_PRIVATE_KEY,
  scopes: SCOPES,
});
```

### Impersonation

If you need to connect on behalf of users only within your organization, you can enable "domain-wide delegation" for your service account. To use impersonation, modify the `JWT` object as follows:

```javascript
const jwtWithImpersonation = new JWT({
  email: process.env.GOOGLE_SERVICE_ACCOUNT_EMAIL,
  key: process.env.GOOGLE_PRIVATE_KEY,
  subject: 'user.to.impersonate@mycompany.com',
  scopes: SCOPES,
});
