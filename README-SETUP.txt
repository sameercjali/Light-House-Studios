# Portfolio Admin System

This converts the static portfolio into a Firebase-backed CMS.

## What the admin can manage

- Secure admin login
- Portfolio image upload
- Portfolio image deletion
- Portfolio title/category/description
- Blog cards
- Filmmaking cards
- Startup/client cards
- Site name and hero text
- Profile image URL
- Section background URLs
- Media organization

## Firebase setup

1. Create a Firebase project.
2. Register a Web App and copy its config into `firebase-config.js`.
3. Enable Authentication -> Email/Password.
4. Create your admin account in Firebase Authentication.
5. Create Firestore Database.
6. Create Storage.
7. Publish the included `firestore.rules` and `storage.rules`.
8. In Firestore, manually create:
   `admins/{YOUR_AUTH_UID}`
   with:
   `admin: true`
9. Deploy the files to the same hosting domain.
10. Open `/admin.html` to manage the site.

Firebase's current web SDK uses the modular API. The supplied admin uses Firebase Authentication, Firestore and Cloud Storage.

## Important

The Firebase config object is safe to include in browser code; it is not a password. Security comes from Firebase Authentication and Firestore/Storage Security Rules.

Do NOT put a Firebase Admin SDK service-account private key in this website.

## Current static-to-dynamic migration

The existing pages are preserved as the design starting point. The next integration step is to replace hard-coded portfolio/content arrays in the public pages with Firestore reads from:

- `site/settings`
- `portfolio/*`
- `blogs/*`
- `filmmaking/*`
- `startups/*`

This keeps your visual design while making content editable from the dashboard.
