# Frequently Asked Questions (FAQ)

This section covers common questions and problems users encounter when using Vaultwarden.

---

## I forgot my master password. Can I reset it?

Unfortunately, no.

Vaultwarden (like Bitwarden) uses **zero-knowledge encryption**, meaning **no one—not even the administrator—can recover your master password**. If it's lost, your data is permanently inaccessible.

!!! tip "Use a password hint or save your master password securely offline."

---

## I didn’t receive a login or verification email. What should I do?

Check the following:

- Look in your **Spam** or **Junk** folder.
- Make sure you're using the correct email address.
- If the server is self-hosted, the admin may need to configure email (SMTP) settings.

!!! note "Contact your Vaultwarden admin if the issue persists."

---

## The browser extension says “Cannot connect to server.” What’s wrong?

Most likely, the **Server URL** is not set correctly.

1. Click the **Settings** link in the browser extension login screen.
2. Replace the default server URL (`https://vault.bitwarden.com`) with your self-hosted Vaultwarden instance URL (e.g., `https://vault.bradix.org`).
3. Save and try logging in again.

---

## Can I use Vaultwarden on mobile?

Yes!

- Download the **Bitwarden** mobile app from the [App Store](https://apps.apple.com/app/bitwarden-password-manager/id1137397744) or [Google Play Store](https://play.google.com/store/apps/details?id=com.x8bit.bitwarden).
- In **Settings**, change the Server URL to your Vaultwarden instance.
- Log in with your credentials.

!!! note "The mobile app works just like the browser extension, including autofill and vault sync."

---

## How do I back up my vault?

You can export your vault to a file:

1. Go to **Tools** → **Export Vault**.
2. Enter your master password.
3. Download the file in CSV or JSON format.

!!! warning "Exported vault files are unencrypted! Store them securely and delete them when finished."

---

## Is Vaultwarden safe?

Vaultwarden is a secure, self-hosted alternative to Bitwarden. It uses:

- End-to-end encryption
- Zero-knowledge architecture
- Open-source code (auditable on GitHub)

!!! note "Security also depends on how you use it—strong passwords, 2FA, and safe sharing are essential."

<br>
