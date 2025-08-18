# Firebase Authentication - Data Storage & Management Guide (Canada)

## Where is Login Data Stored?

All user authentication data for CureMadeEasy Canada is stored in **Google Firebase Authentication**, which uses Google Cloud Platform's secure infrastructure with Canadian data residency considerations.

### Data Storage Location
- **Infrastructure**: Google Cloud Platform (GCP) data centres (Canadian region when possible)
- **Security**: Industry-standard encryption (AES-256)
- **Compliance**: PIPEDA, GDPR, SOC 2 compliant, Health Canada digital health guidelines
- **Replication**: Multi-region backup and redundancy with Canadian data protection standards

## How to Access Your User Data

### 1. Firebase Console Access
1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Select your "curemadeeasy" project
3. Click on "Authentication" in the left sidebar
4. Go to "Users" tab

### 2. What You'll See in the Console
- **User UID**: Unique Firebase identifier for each user
- **Email**: User's email address
- **Provider**: How they signed up (Email/Password or Google)
- **Created**: Account creation date
- **Last Sign-in**: Most recent login timestamp
- **User Status**: Enabled/Disabled

### 3. User Management Actions Available
- **View user details**: Click on any user row
- **Disable/Enable users**: Toggle user access
- **Delete users**: Permanently remove user accounts
- **Export user data**: Download user list as JSON
- **Send password reset**: Help users reset passwords

## Data Security & Privacy

### What Firebase Stores
✅ **Stored Securely:**
- Email addresses
- Password hashes (never plain passwords)
- OAuth provider data (Google profile info)
- Login timestamps
- User preferences and settings

❌ **Never Stored:**
- Plain text passwords
- Sensitive personal information (unless you add it)
- Payment information
- Medical records (stored separately if needed)

### Security Measures
- **Encryption**: All data encrypted at rest and in transit
- **Access Control**: Only project administrators can view user data
- **Audit Logs**: All access and changes are logged
- **Rate Limiting**: Protection against brute force attacks
- **Token Expiration**: Authentication tokens expire automatically

## Data Retention & Deletion

### User Data Lifecycle
1. **Account Creation**: Data stored in Firebase Auth
2. **Active Use**: Login/logout events tracked
3. **Account Deletion**: User can delete their own account
4. **Admin Deletion**: You can delete users from console

### PIPEDA & Canadian Privacy Compliance
- **Right to Access**: Users can request their data under PIPEDA
- **Right to Deletion**: Users can delete their accounts following Canadian privacy laws
- **Data Portability**: User data can be exported for healthcare continuity
- **Consent Management**: Clear consent for data processing under Canadian federal and provincial privacy legislation
- **Provincial Health Acts**: Compliance with individual provincial health information privacy acts

## Geographic Data Location

### Primary Regions for Canadian Users
Firebase Authentication data for Canadian users is stored in:
- **Preferred**: `northamerica-northeast1` (Montreal, Canada) - for Canadian data residency
- **Secondary**: `us-central1` (Iowa, USA) - with cross-border data agreements
- **Backup**: `us-east1` (South Carolina, USA) - following Canadian privacy law requirements for cross-border data transfers

### How to Check Your Project's Region
1. Firebase Console → Project Settings
2. Scroll down to "Default GCP resource location"
3. This shows where your authentication data is stored

## Backup & Recovery

### Firebase's Automatic Backups
- **Continuous Replication**: Data replicated across multiple zones
- **Point-in-time Recovery**: Google maintains automated backups
- **99.99% Uptime SLA**: Enterprise-grade reliability

### Your Backup Options
- **Export Users**: Regularly export user list from console
- **Admin SDK**: Programmatically backup user data
- **Custom Solutions**: Build your own backup system if needed

## Monitoring & Analytics

### Firebase Analytics Dashboard
- **User Growth**: New signups over time
- **Authentication Methods**: Email vs Google breakdown
- **Geographic Distribution**: Where users are located
- **Device Types**: Mobile vs desktop usage

### Custom Monitoring
```javascript
// Track custom authentication events
auth.onAuthStateChanged((user) => {
  if (user) {
    // Log successful login
    console.log('User logged in:', user.uid);
    // Send to analytics if needed
  }
});
```

## Cost Considerations

### Firebase Authentication Pricing
- **Free Tier**: Up to 10,000 monthly active users
- **Paid Tier**: $0.0055 per monthly active user beyond free tier
- **No Storage Costs**: User authentication data storage is included

### Current Usage Monitoring
1. Firebase Console → Usage and billing
2. View monthly active users count
3. Monitor against free tier limits

## Migration & Export Options

### If You Need to Move Data
```bash
# Using Firebase Admin SDK to export users
const admin = require('firebase-admin');

admin.auth().listUsers()
  .then((listUsersResult) => {
    // Export user data
    console.log('Users:', listUsersResult.users);
  });
```

### Alternative Authentication Providers
If you want to migrate away from Firebase:
- **Auth0**: Enterprise authentication service
- **AWS Cognito**: Amazon's user authentication
- **Custom Solution**: Build your own with Node.js + PostgreSQL

## Privacy Policy Requirements for Canadian Healthcare Platform

Since you're collecting healthcare-related user data in Canada, your privacy policy must comply with PIPEDA and provincial health information acts:
- What data you collect (email, login times, health records access logs)
- How you use it (authentication, account management, healthcare coordination)
- Where it's stored (Google Firebase, Canadian data centres when possible)
- User rights under PIPEDA (access, deletion, portability, correction)
- Provincial health information privacy rights
- Cross-border data transfer safeguards
- Healthcare provider data sharing protocols
- Contact information for privacy questions and complaints (including provincial privacy commissioners)
- Retention periods for health-related information
- Data breach notification procedures

## Security Best Practices

### For Your Application
- ✅ Use HTTPS only
- ✅ Implement proper session management
- ✅ Regular security audits
- ✅ Monitor for suspicious login patterns
- ✅ Implement account lockout after failed attempts

### For Users
- Encourage strong passwords
- Offer two-factor authentication
- Provide clear privacy controls
- Regular security notifications

## Contact & Support

- **Firebase Support**: Available through Google Cloud Console
- **Documentation**: https://firebase.google.com/docs/auth
- **Community**: Firebase Discord and Stack Overflow
- **Enterprise Support**: Available with paid plans
