# Privacy Policy for Karmageddon

**Last Updated**: May 20, 2026

## 1. Introduction

Karmageddon ("we", "our", or "the extension") is a browser extension that helps FACEIT players rate and remember teammates and opponents. This policy explains what data we handle, how we handle it, and your rights.

## 2. Data We Store Locally

All your personal data is stored **locally on your device** using Chrome's secure storage API. We never have access to this data.

**Stored locally on your device:**
- **Your Ratings**: Numerical ratings (1-5 scale) you assign to players
- **Rating Tags**: Descriptive tags you select for players (such as "Toxic", "Leader", "Clutch")
- **FACEIT Player Information**: Player nicknames and IDs (from FACEIT's public API)
- **Your FACEIT Profile**: Your nickname, player ID, and avatar URL (if you log in)
- **Authentication Tokens**: OAuth tokens for your FACEIT account (if you log in)
- **Timestamps**: When ratings were created or modified
- **User Settings**: Your extension preferences

## 3. Optional FACEIT Login

Karmageddon offers optional FACEIT login to identify your account. **This feature is entirely optional** - you can use the extension without logging in.

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

## 4. Data Flow Summary

| Data | Where It Goes | Stored? |
|------|--------------|---------|
| Your ratings & tags | Your device only | Yes (locally) |
| Your FACEIT profile | Your device only | Yes (locally) |
| OAuth tokens | Your device only | Yes (locally) |
| Authorization code | Our server → FACEIT | No (processed transiently) |
| Refresh tokens | Our server → FACEIT | No (processed transiently) |
| Player info from FACEIT API | Your browser → FACEIT | No (displayed only) |

## 5. Third-Party Services

### FACEIT
- The extension connects directly to FACEIT's public API to fetch player information
- If you log in, authentication goes through FACEIT's OAuth system
- Review [FACEIT's Privacy Policy](https://corporate.faceit.com/privacy/)

### Firebase (Google Cloud)
- Our token exchange server runs on Firebase Cloud Functions (Google Cloud Platform)
- Firebase processes requests but does not store any user data
- Hosted in Europe (europe-west1 region)
- Review [Google Cloud Privacy Policy](https://cloud.google.com/terms/cloud-privacy-notice)

## 6. Security Measures

- **PKCE**: We use Proof Key for Code Exchange for secure OAuth flow
- **CSRF Protection**: Random state parameter prevents cross-site request forgery
- **CORS**: Our server only accepts requests from the official extension
- **Secret Management**: Client secrets are stored in Firebase Secret Manager, never exposed to clients
- **HTTPS**: All communications are encrypted

## 7. Your Rights and Controls

You have complete control over your data:

- **Export**: Export all your data at any time via the extension popup
- **Delete**: Delete individual ratings or all data at any time
- **Logout**: Log out of FACEIT to remove tokens from your device
- **Disable**: Disable the extension via the toggle in the popup
- **Uninstall**: Uninstalling removes all stored data from your device

## 8. Data Retention

- **Local data**: Retained on your device until you delete it or uninstall the extension
- **Server data**: We retain nothing - data is processed in memory and immediately discarded

## 9. No Tracking or Analytics

- We do NOT use any analytics services
- We do NOT track your usage or behavior
- We do NOT collect telemetry or diagnostic data
- We do NOT use cookies or tracking technologies
- We do NOT monitor which players you rate

## 10. Children's Privacy

This extension is not directed at children under 13 and we do not knowingly collect data from children.

## 11. Changes to This Policy

We may update this privacy policy from time to time. Updates will be posted on this page with a new "Last Updated" date. Changes are effective immediately upon posting.

## 12. Contact Us

For questions or concerns about this privacy policy:

- **Discord**: https://discord.gg/JpnNX4QRFu
- **GitHub Issues**: https://github.com/bernardo-blando/karmageddon/issues
- **Ko-fi**: https://ko-fi.com/kaarmageddon

## 13. Privacy Summary

| Aspect | Status |
|--------|--------|
| Ratings & settings | Stored locally on your device |
| FACEIT login | Optional, tokens stored locally |
| Server storage | None - we don't store user data |
| Analytics/tracking | None |
| Data sharing | None |
| Your control | Full - export, delete, logout anytime |

## 14. Legal Compliance

We respect your privacy rights under GDPR, CCPA, and other privacy regulations:

- **Data minimization**: We only process what's necessary for authentication
- **No data retention**: Our servers don't store personal data
- **Transparency**: This policy explains exactly what happens with your data
- **User control**: You can access, export, or delete your data through the extension

---

**Summary**: Karmageddon stores your ratings and settings locally on your device. Optional FACEIT login uses our server only as a secure proxy for token exchange - we don't store any user data. Your data stays on your device, under your control.
