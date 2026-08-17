# Firebase Setup Guide for MeetMedia

## Step 1: Create a Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com)
2. Click "Add Project"
3. Enter your project name: `MeetMedia`
4. Accept the terms and create the project
5. Wait for the project to be created

## Step 2: Enable Authentication

1. In Firebase Console, go to **Authentication** (left sidebar)
2. Click on **Get Started**
3. Enable the following sign-in methods:
   - **Email/Password**: Click the Email/Password provider, enable it, and save
   - **Google**: Click the Google provider, enable it, enter your email, and save

## Step 3: Create Firestore Database

1. Go to **Firestore Database** (left sidebar)
2. Click **Create database**
3. Choose **Start in production mode** for now (you can change security rules later)
4. Select your location (closest to your users)
5. Click **Create**

## Step 4: Get Your Firebase Config

1. Go to **Project Settings** (gear icon in top left)
2. Under **Your apps**, click the **Web** icon (or create a new web app)
3. Copy the Firebase config object

## Step 5: Update config.js

Replace the placeholder values in `config.js` with your Firebase credentials:

```javascript
const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_PROJECT_ID.appspot.com",
    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
    appId: "YOUR_APP_ID"
};
```

## Step 6: Set Up Security Rules (Firestore)

1. Go to **Firestore Database** > **Rules**
2. Replace the rules with the following:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Users collection - users can only read/write their own data
    match /users/{userId} {
      allow read, write: if request.auth.uid == userId;
    }
    
    // Public data that anyone can read
    match /public/{document=**} {
      allow read: if request.auth != null;
      allow write: if false;
    }
  }
}
```

3. Click **Publish**

## Step 7: Configure Google OAuth Redirect URLs

1. Go to **Authentication** > **Settings**
2. Under **Authorized domains**, add:
   - `localhost`
   - Your domain when deployed

## File Structure

```
MeetMedia/
├── index.html              # Landing page (public website)
├── login.html              # Login page
├── signup.html             # Sign up page
├── dashboard.html          # User dashboard
├── config.js               # Firebase configuration
├── FIREBASE_SETUP.md       # This file
└── README.md               # Project information
```

## Testing Locally

1. You need to run a local server to test. Use one of these options:

### Option 1: Python
```bash
python -m http.server 8000
```

### Option 2: Node.js (http-server)
```bash
npx http-server
```

### Option 3: Live Server (VS Code Extension)
- Install "Live Server" extension
- Right-click on index.html
- Select "Open with Live Server"

## Features Implemented

✅ **Authentication**
- Email/Password registration and login
- Google Sign-In integration
- Session management

✅ **Dashboard**
- User profile display
- Discover people feature
- Messaging interface
- Events listing
- User settings

✅ **Pages**
- Landing page (index.html)
- Login page (login.html)
- Sign up page (signup.html)
- Dashboard (dashboard.html)

## Next Steps

1. Update the `config.js` with your Firebase credentials
2. Test the signup and login flow
3. Customize the dashboard with your features
4. Add more Firestore collections for messages, events, etc.
5. Deploy to Firebase Hosting or your preferred hosting

## Troubleshooting

**Issue**: "Firebase is not defined"
- Make sure `config.js` is loaded after the Firebase scripts in the HTML

**Issue**: CORS errors
- Make sure you've added your domain to authorized domains in Firebase Authentication settings

**Issue**: Authentication not working
- Check that Email/Password and Google are enabled in Firebase Authentication
- Verify config.js has correct credentials

## Support

For more help:
- [Firebase Documentation](https://firebase.google.com/docs)
- [Firebase Console](https://console.firebase.google.com)
