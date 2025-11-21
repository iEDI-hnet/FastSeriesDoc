# User Settings

## Overview

User Settings allow you to personalize your FastProducts experience. These settings are specific to your account and don't affect other users in your organization. Access User Settings by clicking on the Avatar (profile picture) on the left side of the navigation menu.

> Some settings may be read-only when you're offline or when settings have been changed on another device. In such cases, you'll see a message indicating the current state and what action is needed.{style="note"}

## Display Settings

Customize how FastProducts looks and feels to match your preferences and working environment.

### Language

You can localize your user interface to your preferred language. FastProducts supports multiple languages to accommodate users worldwide.

**Supported Languages:**
- English (en)
- Danish (da)
- German (de)
- Spanish (es)
- French (franc)
- Italian (it)
- Dutch (nl)

**How to Change Language:**
1. Click on the Avatar (profile picture) on the left side of the navigation menu to open User Settings
2. Find "Preferred language" in the Display section
3. Select your desired language from the dropdown
4. The interface will update immediately to your selected language

> Language changes apply immediately and affect all text in the user interface, including menus, buttons, labels, and messages.{style="note"}

### Theme

Choose your preferred color theme for the application interface. You can select from light, dark, or system theme (which automatically matches your operating system's theme preference).

**Theme Options:**
- **System:** Automatically matches your operating system's theme (light or dark)
- **Light:** Light color scheme with dark text on light backgrounds
- **Dark:** Dark color scheme with light text on dark backgrounds

**How to Change Theme:**
1. Click on the Avatar (profile picture) on the left side of the navigation menu to open User Settings
2. Find "Theme" in the Display section
3. Select your preferred theme from the dropdown
4. The interface will update immediately

> Benefits:
> Dark theme can reduce eye strain in low-light environments, while light theme provides better readability in bright conditions. System theme ensures consistency with your overall system appearance.

### Start Full Screen

Configure FastProducts to automatically start in full screen mode when launched. This maximizes your workspace and provides an immersive experience for managing products and catalogues.

**How to Enable:**
1. Click on the Avatar (profile picture) on the left side of the navigation menu to open User Settings
2. Find "Start full screen" in the Display section
3. Toggle the switch to "On"
4. FastProducts will start in full screen mode on next launch

> You can still exit full screen mode at any time using the exit full screen button in the footer, regardless of this setting.{style="note"}

## Notifications & Actions

Configure how and when you receive notifications about important events and updates in FastProducts. Notifications help you stay informed about product updates, sharing events, and billing alerts.

### Notification Channels

Choose how you want to receive notifications. You can enable or disable email and push notifications independently.

**Email Notifications:**
- Receive notifications via email at your registered email address
- Useful for important updates that you want to review later
- Notifications are sent to the email address in your Account & Privacy settings

**Push Notifications:**
- Receive real-time notifications within the application
- Ideal for immediate alerts that require your attention
- Appear as toast messages or notification badges

**How to Configure:**
1. Click on the Avatar (profile picture) on the left side of the navigation menu to open User Settings
2. Expand "Notifications" in the Notifications & Actions section
3. Toggle "Email" and/or "Push" notifications on or off
4. Changes are saved automatically

### Notification Categories

Fine-tune which types of events trigger notifications. You can enable or disable specific categories to receive only the notifications that matter to you.

**Available Categories:**
- **Product Updates:** Notifications about product changes, new products, or product information updates
- **Share Events:** Notifications about catalogue sharing, partner activities, or sharing-related events
- **Billing Alerts:** Notifications about subscription changes, payment reminders, or billing-related information

**How to Configure:**
1. Click on the Avatar (profile picture) on the left side of the navigation menu to open User Settings
2. Expand "Categories" in the Notifications & Actions section
3. Toggle individual categories (Product updates, Share events, Billing alerts) on or off
4. Changes are saved automatically with a short delay (debounced) to prevent excessive API calls

> Category settings work in combination with channel settings. For example, if you disable Email notifications, you won't receive email notifications for any category, even if individual categories are enabled.{style="note"}

## Account & Privacy

Manage your account information and privacy preferences, including email address and newsletter subscription.

### Email

Update your email address associated with your FastProducts account. This email is used for:
- Account notifications (if email notifications are enabled)
- Password recovery
- Important system communications

**How to Update:**
1. Click on the Avatar (profile picture) on the left side of the navigation menu to open User Settings
2. Expand "Account & Privacy"
3. Enter your new email address in the Email field
4. Changes are saved automatically after a short delay

> Ensure your email address is valid and accessible, as it's used for important account communications.{style="note"}

### Newsletter Subscription

Subscribe to the FastProducts newsletter to receive updates about new features, tips, best practices, and product news.

**How to Subscribe/Unsubscribe:**
1. Click on the Avatar (profile picture) on the left side of the navigation menu to open User Settings
2. Expand "Account & Privacy"
3. Toggle "Subscribe to newsletter" on or off
4. Changes are saved immediately

>Content:
> The newsletter includes information about product updates, feature releases, usage tips, and industry best practices to help you get the most out of FastProducts.

## Security

Manage your account security settings, including password changes and encryption PIN for offline access and local data protection.

### Change Password

Regularly updating your password helps maintain account security. Use a strong, unique password that you don't use elsewhere.

**How to Change Password:**
1. Click on the Avatar (profile picture) on the left side of the navigation menu to open User Settings
2. Find "Change Password" in the Security section
3. Click to open the password change dialog
4. Enter your current password
5. Enter your new password (and confirm it)
6. Click Save to update your password

> Password Requirements:
> Follow the password requirements shown in the dialog. Typically, passwords should be strong and meet minimum length and complexity requirements.

### Encryption PIN

The Encryption PIN protects your local data at rest on this device. When enabled, you'll need to enter the PIN to access your data when offline or when the database is locked.

**Purpose:** The PIN provides an additional layer of security for your local FastProducts data, ensuring that even if someone gains physical access to your device, they cannot access your encrypted data without the PIN.

**Unified PIN System:** When you enable encryption, the same PIN is automatically used for both database encryption and offline authentication. This unified system ensures consistency and simplifies PIN management - you only need to remember one PIN for both securing your local data and accessing the application when offline.

**PIN Requirements:**
- Must be exactly 4 digits (0-9)
- Should be memorable but not easily guessable

**How to Enable Encryption PIN:**
1. Click on the Avatar (profile picture) on the left side of the navigation menu to open User Settings
2. Expand "Security (PIN)" in the Security section
3. Toggle "Use encryption PIN for offline login" to On
4. Enter your 4-digit PIN in the dialog
5. Confirm your PIN
6. The encryption will be enabled and your data will be protected. The same PIN will also be used for offline authentication (unified PIN system)

**How to Change PIN:**
1. Ensure "Use encryption PIN for offline login" is enabled
2. Click "Change PIN" button
3. Enter your current PIN
4. Enter your new PIN (and confirm it)
5. The PIN will be updated for both database encryption and offline authentication (unified PIN system)

**Important Notes:**
- **Database Must Be Open:** To enable, disable, or change your PIN, the database must be open (you must be logged in online and the application must be running)
- **Administrator Privileges:** Only device administrators can enable, disable, or change the encryption PIN
- **Unified PIN:** The same PIN is used for both database encryption and offline authentication. Changing the PIN updates both systems simultaneously
- **Offline Access:** Once enabled, you'll need the PIN to access your data when offline or when the database is locked
- **Sharing PIN:** If multiple users share the same device, you may need to share the PIN with them for offline access
- **Encryption Availability:** In some builds, database encryption may not be available. In such cases, PIN protection cannot be enabled
- **PIN Change Requires Current PIN:** When changing your PIN, you must provide your current PIN for verification

**Conflict Resolution:** If settings are changed on another device, you may see a conflict message. Reload your settings to continue editing. When offline, settings are read-only and show the last saved values.

**Troubleshooting:**
- If you see "Encryption Not Available": Database encryption is not supported in your current build. Install the latest FastProducts release or contact support
- If "Change PIN" is disabled: Ensure the database is open (application is running and you're logged in online) and you have administrator privileges
- If PIN change fails: Verify your current PIN is correct and that you meet all requirements (exactly 4 digits, 0-9 only)
- If you see "Only a device administrator can manage the PIN": Sign in with an administrator account to enable or change the PIN

## Log Out

Sign out of your FastProducts account. Logging out will end your current session and require you to log in again to access the application.

**How to Log Out:**
1. Click the "Log off" button in the navigation menu (bottom of the sidebar)
2. Your session will be ended immediately
3. You'll be redirected to the login page

> If you have encryption PIN enabled, your local encrypted data will remain protected. You'll need to log in again (and enter your PIN if accessing offline) to access your data.
{style="note"}
