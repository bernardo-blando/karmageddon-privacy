# Privacy Policy for Karmageddon

**Last Updated**: June 4, 2026

## 1. Introduction

Karmageddon ("we", "our", or "the extension") is a browser extension that helps FACEIT players rate and remember teammates and opponents. This policy explains what data we handle, how we handle it, and your rights.

## 2. Data We Store Locally

All your personal data is stored **locally on your device** using Chrome's secure storage API. We never have access to this data unless you log in (which enables Cloud Sync).

**Stored locally on your device:**
- **Your Ratings**: Numerical ratings (1-5 scale) you assign to players
- **Rating Tags**: Descriptive tags you select for players (such as "Toxic", "Leader", "Clutch")
- **FACEIT Player Information**: Player nicknames and IDs (from FACEIT's public API)
- **Your FACEIT Profile**: Your nickname, player ID, and avatar URL (if you log in)
- **Authentication Tokens**: OAuth tokens for your FACEIT account (if you log in)
- **Timestamps**: When ratings were created or modified
- **User Settings**: Your extension preferences
- **Sync Status**: Whether ratings have been synced to the cloud (if logged in)

## 3. Optional FACEIT Login

Karmageddon offers FACEIT login to identify your account. Login is optional for basic features like local ratings. **Logging in automatically enables Cloud Sync** to back up your ratings across devices. Future features like community ratings will also require login.

### What Happens When You Log In

1. You click "Login with FACEIT" and are redirected to FACEIT's official login page
2. FACEIT authenticates you and sends an authorization code back to the extension
3. The extension sends this code to our secure server (Firebase Functions) to exchange it for access tokens
4. Our server fetches your basic profile (nickname, player ID, avatar) from FACEIT
5. Tokens and profile are returned to the extension and **stored locally on your device**

### What Our Server Processes (Temporarily)

During login and token refresh, our server processes the following **in memory only**:
- Authorization code (from FACEIT)
- PKCE code verifier (security mechanism)
- Refresh tokens (when refreshing expired tokens)

**We do NOT store any of this data.** Our server acts purely as a secure proxy to exchange tokens with FACEIT (required because client secrets cannot be safely stored in browser extensions).

### What Our Server Does NOT Do

- Does NOT store your tokens, profile, or any user data
- Does NOT log your authentication requests
- Does NOT track who uses the extension
- Does NOT have a database of users
- Does NOT retain any information after the request completes

## 4. Cloud Sync

Karmageddon offers Cloud Sync to sync your ratings across devices. **Cloud Sync is automatically enabled when you log in with FACEIT.** If you don't want cloud sync, don't log in — your ratings will remain stored locally on your device.

### What Cloud Sync Does

When enabled, Cloud Sync:
- Stores your ratings in our server's database
- Syncs ratings between your devices automatically
- Downloads ratings to new devices when you log in
- Syncs new ratings as you create them

### What Data is Stored in the Cloud

When logged in, the following data is stored in our database:
- **Player IDs**: FACEIT player identifiers you have rated
- **Player Names**: FACEIT nicknames of rated players
- **Ratings**: Your numerical ratings (1-5 scale)
- **Tags**: Descriptive tags you assigned
- **Timestamps**: When ratings were created or last modified

### Cloud Data Security

- **User Isolation**: Your data is only accessible to you (secured by Firebase Authentication)
- **Encryption**: All data is encrypted in transit (HTTPS) and at rest (Google Cloud encryption)
- **No Selling**: Your data is never sold to third parties
- **Regional Storage**: Data is stored in Google Cloud (europe-west1 region)

### Disabling Cloud Sync

To stop cloud sync, log out of your FACEIT account:
- Logging out stops syncing but does **not** automatically delete your cloud data
- Your local data remains unchanged
- To delete your cloud data, email us at hey@karmageddon.app

## 5. Data Flow Summary

| Data | Where It Goes | Stored? |
|------|--------------|---------|
| Your ratings & tags | Your device | Yes (locally) |
| Your ratings & tags | Our cloud servers | Yes, if logged in |
| Your FACEIT profile | Your device only | Yes (locally) |
| OAuth tokens | Your device only | Yes (locally) |
| Authorization code | Our server → FACEIT | No (processed transiently) |
| Refresh tokens | Our server → FACEIT | No (processed transiently) |
| Player info from FACEIT API | Your browser → FACEIT | No (displayed only) |

## 6. Third-Party Services

### FACEIT
- The extension connects directly to FACEIT's public API to fetch player information
- If you log in, authentication goes through FACEIT's OAuth system
- Review [FACEIT's Privacy Policy](https://corporate.faceit.com/privacy/)

### Firebase (Google Cloud)
- Our token exchange server runs on Firebase Cloud Functions (Google Cloud Platform)
- Firebase Authentication verifies your identity for Cloud Sync
- Your ratings are stored in our cloud database if you log in
- Hosted in Europe (europe-west1 region)
- Review [Google Cloud Privacy Policy](https://cloud.google.com/terms/cloud-privacy-notice)

## 7. Security Measures

- **PKCE**: We use Proof Key for Code Exchange for secure OAuth flow
- **CSRF Protection**: Random state parameter prevents cross-site request forgery
- **CORS**: Our server only accepts requests from the official extension
- **Secret Management**: Client secrets are stored in Firebase Secret Manager, never exposed to clients
- **HTTPS**: All communications are encrypted
- **Database Security Rules**: Cloud data is protected by security rules that ensure user isolation

## 8. Your Rights and Controls

You have complete control over your data:

- **Export**: Export all your data at any time via the extension popup
- **Delete**: Delete individual ratings or all data at any time
- **Cloud Sync**: Automatically enabled with login; log out to disable
- **Delete Cloud Data**: Email hey@karmageddon.app to request deletion
- **Logout**: Log out of FACEIT to remove tokens from your device
- **Disable**: Disable the extension via the toggle in the popup
- **Uninstall**: Uninstalling removes all local data from your device

## 9. Data Retention

- **Local data**: Retained on your device until you delete it or uninstall the extension
- **Cloud data**: Retained until you request deletion (not automatically deleted when you log out or uninstall)
- **Server data**: We retain nothing - token exchange data is processed in memory and immediately discarded

## 10. Analytics and Tracking

**Current status:** We do not currently collect analytics or tracking data.

If we introduce analytics in the future:
- You will be clearly informed when analytics are enabled
- No personally identifiable information will be collected
- You will be able to opt out at any time via settings
- This policy will be updated to reflect those changes

We do NOT:
- Use cookies or tracking technologies
- Monitor which players you rate
- Sell or share your data with advertisers

## 11. Children's Privacy

This extension is not directed at children under 13 and we do not knowingly collect data from children.

## 12. Changes to This Policy

We may update this privacy policy from time to time. Updates will be posted on this page with a new "Last Updated" date. Changes are effective immediately upon posting.

### Upcoming: Community Karma Scores

We are introducing **Community Karma Scores** — aggregate reputation scores calculated from all user ratings. Here's how it works:

**Privacy Model:**
- **Individual ratings are PRIVATE** — no one can see WHO rated a player or what rating they gave
- **Aggregate karma is PUBLIC** — everyone can see a player's average score (e.g., "4.2 from 47 ratings")
- This works like Uber/Lyft ratings — you see the score, not who gave it

**Participation:**
- All ratings contribute to community karma — there is no opt-out
- By using Karmageddon to rate players, you consent to your ratings being included in aggregate scores
- Your individual rating remains private; only the mathematical aggregate is shared

**Future requirement:**
- Rating players will require FACEIT login (to ensure one rating per user per player)
- Cloud Sync is enabled automatically when you log in

### Other Planned Features

- **Private notes**: Encrypted personal notes visible only to you (premium feature)
- **Usage analytics**: Privacy-respecting analytics to improve the extension (opt-out available)

We will update this policy before launching any feature that changes how your data is collected or used.

## 13. Contact Us

For questions or concerns about this privacy policy:

- **Email**: hey@karmageddon.app
- **Discord**: https://discord.gg/JpnNX4QRFu
- **GitHub Issues**: https://github.com/bernardo-blando/karmageddon/issues
- **Ko-fi**: https://ko-fi.com/kaarmageddon

## 14. Privacy Summary

| Aspect | Status |
|--------|--------|
| Ratings & settings | Stored locally on your device |
| Cloud Sync | Enabled automatically when you log in |
| Community Karma | Your ratings contribute to public aggregate scores (no opt-out) |
| Individual ratings | Always private — no one sees WHO rated or what score |
| FACEIT login | Required for rating (future), tokens stored locally |
| Server storage | Token exchange: none. Cloud data: if logged in |
| Analytics/tracking | None currently (future: opt-out available) |
| Data selling | Never |
| Your control | Export anytime, delete local data anytime, email for cloud deletion |

## 15. Legal Compliance

We respect your privacy rights under GDPR, CCPA, and other privacy regulations:

- **Data minimization**: We only process what's necessary for functionality
- **Purpose limitation**: Cloud data is used for syncing your ratings and providing extension features
- **User consent**: Logging in enables cloud sync; users who don't want sync can use the extension without logging in
- **Data portability**: You can export all your data at any time
- **Right to deletion**: You can delete local data through the extension; email us to delete cloud data
- **Transparency**: This policy explains exactly what happens with your data
- **User control**: You can access and export your data through the extension

---

**Summary**: Karmageddon stores your ratings and settings locally on your device. FACEIT login uses our server only as a secure proxy for token exchange. **Logging in automatically enables Cloud Sync**, which stores your ratings in our cloud database for cross-device sync — if you don't want cloud sync, don't log in. **Community Karma Scores** (coming soon) will aggregate all user ratings into public scores — individual ratings remain private, only the aggregate is public. By rating players, you consent to contributing to community karma. Your data stays under your control.
