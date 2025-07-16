# Sharing Items with Others

Vaultwarden supports secure sharing through **Organizations** and **Collections**. This is ideal for families, teams, or small businesses that need shared access to specific credentials.

---

## What Is an Organization?

An **Organization** is a shared space where multiple users can collaborate and manage shared vault items.

### Example Use Cases:
- A family sharing Netflix and Wi-Fi credentials
- A small IT team sharing server logins
- A business team managing social media accounts

---

## What Are Collections?

**Collections** are folders within an Organization that group related items. You can control which users have access to which Collections.

Example Collections:
- "Finance Logins"
- "Team Tools"
- "Social Media"

---

## Creating or Joining an Organization  

!!! note "Only Vaultwarden admins or invited users can create or join an Organization."

1. Go to the **Organizations** tab in the Vaultwarden web interface.
2. Click **New Organization** (if available), or accept an invite from an existing one.
3. Enter your organization name and billing email (if applicable).
4. Confirm creation and start adding users and Collections.

---

## Adding Users to an Organization

1. Navigate to your Organization.
2. Go to **Manage Users**.
3. Click **Invite User** and enter their email.
4. Choose their role:
   - **Owner**: Full control
   - **Admin**: Manage users and items
   - **User**: Access assigned Collections

!!! note "Invited users will receive an email to join your Organization. They must already have a Vaultwarden account."

---

## Sharing an Item

To share a login or note with your team:

1. Edit the item in your vault.
2. Change the **Ownership** from "Private" to your Organization.
3. Assign it to one or more Collections.
4. Click **Save**.

!!! warning "Only users with access to that Collection will be able to see and use the shared item."

---

## Auditing Shared Access

Vaultwarden lets admins view:
- Who accessed what item
- When an item was modified
- Who owns or shares each credential

Use this for accountability and access control within your team.

<br>

??? tip "Best Practices for Sharing"

    - Use **Collections** to keep items organized
    - Give users the **least privilege** required
    - Regularly review shared items and user roles
    - Use **2FA** for all users in an Organization

<br>
