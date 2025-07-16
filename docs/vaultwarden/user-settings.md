# Managing Your Account & User Settings

Vaultwarden gives users control over their security and account preferences. This page walks through how to update your information, enable two-factor authentication (2FA), and export your vault data (if needed).

---

## Updating Your Account Information

To update your email, name, or language settings:

1. Log into the Vaultwarden web app.
2. Click your profile icon in the upper-right corner.
3. Select **Account Settings**.
4. Edit the fields as needed and click **Save**.

!!! warning "Changing your email address will require re-verification."

---

## Changing Your Master Password

Your master password is the key to your entire vault. To change it:

1. Navigate to **Account Settings** &rarr; **Security** tab.
2. Click **Change Master Password**.
3. Enter your current password, then the new one twice.
4. Click **Save**.

!!! tip "Use a long passphrase you can remember. This password cannot be recovered if lost."

---

## Enabling Two-Factor Authentication (2FA)

1. In **Account Settings** &rarr; **Security** &rarr; **Two-Step Login** tab.
2. Click **Manage** under the providers tab.
3. Choose **Authenticator App (TOTP)**.
4. Scan the QR code using an app like:  

    - Google Authenticator
    - Authy
    - Microsoft Authenticator
5. Enter the generated code and click **Enable**.

!!! tip "Keep your backup codes somewhere safe. You'll need them if you lose access to your device."

---

## Exporting Your Vault

You can export your vault as an encrypted or plaintext file:

1. Go to **Tools** → **Export vault**.
2. Choose your export format (CSV or JSON).
3. Re-enter your master password.
4. Click **Export vault**.

!!! warning "Exported files are not encrypted! Only do this in a secure environment and delete the file immediately after use."

---

## Deleting Your Account

To delete your Vaultwarden account permanently:

1. Go to **Account Settings** → <span style="color: red;">**Danger Zone**</span>.
2. Click **Delete Account**.
3. Confirm your master password and approve the deletion.

!!! warning " This action cannot be undone. Your vault data will be permanently lost."

<br>


