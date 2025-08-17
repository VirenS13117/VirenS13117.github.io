# Firebase Authentication Setup Instructions

## Step 1: Create a Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add project" or "Create a project"
3. Enter project name (e.g., "virender-portfolio")
4. Configure Google Analytics (optional)
5. Click "Create project"

## Step 2: Enable Authentication

1. In your Firebase project, click "Authentication" in the left sidebar
2. Click "Get started"
3. Go to "Sign-in method" tab
4. Enable the following providers:
   - **Google**: Click on Google → Enable → Save
   - **Facebook**: Click on Facebook → Enable → Add your Facebook App ID and App Secret → Save

## Step 3: Configure Authorized Domains

1. Still in Authentication > Sign-in method
2. Scroll down to "Authorized domains"
3. Add your domain:
   - For GitHub Pages: `virenS13117.github.io`
   - For local testing: `localhost` (usually already added)

## Step 4: Get Firebase Config

1. Click the gear icon next to "Project Overview"
2. Select "Project settings"
3. Scroll down to "Your apps" section
4. Click the web icon `</>` to create a web app
5. Register your app with a nickname (e.g., "Portfolio Website")
6. Copy the Firebase configuration object

## Step 5: Update Your Website

1. Open `index.html` in your code editor
2. Find the `firebaseConfig` object (around line 288)
3. Replace the placeholder values with your actual Firebase config:

```javascript
const firebaseConfig = {
  apiKey: "your-actual-api-key-here",
  authDomain: "your-project-id.firebaseapp.com",
  projectId: "your-actual-project-id",
  storageBucket: "your-project-id.appspot.com",
  messagingSenderId: "your-actual-sender-id",
  appId: "your-actual-app-id"
};
```

## Step 6: Facebook App Setup (Optional)

If you want Facebook login to work:

1. Go to [Facebook Developers](https://developers.facebook.com/)
2. Create a new app or use existing one
3. Add Facebook Login product
4. Set redirect URI: `https://your-project-id.firebaseapp.com/__/auth/handler`
5. Copy App ID and App Secret to Firebase Authentication settings

## Step 7: Test Your Authentication

1. Open your website
2. Click the "Login" button in the top-right corner
3. Try logging in with Gmail or Facebook
4. Verify that your profile appears after successful login

## Important Notes:

- **Security**: Never commit your Firebase config to public repositories if they contain sensitive data
- **Domains**: Make sure to add all domains where your site will be hosted to Firebase authorized domains
- **Testing**: You can test locally by serving your HTML file through a local server

## Troubleshooting:

- **"This domain is not authorized"**: Add your domain to Firebase authorized domains
- **Facebook login fails**: Check Facebook app settings and redirect URIs
- **Gmail login fails**: Verify Google provider is enabled in Firebase
