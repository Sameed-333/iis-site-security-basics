# IIS Site Security Basics (Windows Authentication + Permissions)

This mini-project demonstrates basic hardening of an IIS website on Windows by:
- Enabling **Windows Authentication**
- Disabling **Anonymous Authentication**
- Tightening **NTFS permissions** for the Default Web Site
- Granting access to specific users/groups and validating access by testing the site

## Objective
- Enable Windows Authentication in IIS
- Restrict access by disabling anonymous access
- Review and reconfigure file/folder permissions for the website
- Validate the site works after applying security controls

## Environment
- Windows 11 (similar steps apply on Windows 10 / Windows Server)
- IIS installed (Internet Information Services)
- Administrator privileges

## Repository structure (recommended)
- `README.md`
- `assets/` (screenshots: authentication settings, permissions, browser test)
- `report/` (optional: your PDF/DOCX export)

---

## Part A — Enable Windows Authentication

### 1) Install Windows Authentication feature (if missing)
1. Open **Control Panel** → **Programs** → **Turn Windows features on or off**
2. Expand:
   - **Internet Information Services**
   - **World Wide Web Services**
   - **Security**
3. Check **Windows Authentication**
4. Click **OK** and let Windows install the feature

### 2) Configure Authentication settings in IIS
1. Open **IIS Manager**
2. Go to: **Sites** → **Default Web Site**
3. Open **Authentication**
4. Apply these settings:
   - **Disable**: Anonymous Authentication
   - **Enable**: Windows Authentication

> Result: Users must authenticate (Windows credentials) instead of browsing anonymously.

---

## Part B — Harden website folder permissions (NTFS)

### 3) Open Default Web Site folder permissions
1. In **IIS Manager**, right-click **Default Web Site**
2. Click **Edit Permissions**
3. Go to the **Security** tab

### 4) Disable inheritance and convert permissions
1. Click **Advanced**
2. Click **Disable inheritance**
3. Choose: **Convert inherited permissions into explicit permissions on this object**
4. Click **Apply** → **OK**

> This step gives you direct control over permissions instead of inheriting from parent folders.

### 5) Remove/adjust users and permissions
1. Back in **Security** tab → click **Edit**
2. Remove unnecessary groups/users (example: overly-broad access groups)
3. Ensure only required identities have access (typical examples):
   - Administrators (full control)
   - IIS worker identity (as needed)
   - Specific user/group you want to allow

---

## Part C — Allow specific user/group access

### 6) Add user/group and set permissions
1. In **Security** tab → **Edit** → **Add**
2. Enter a username or group name
3. Click **Check Names** → **OK**
4. Assign appropriate permissions (start minimal, expand only if needed):
   - Read & execute
   - List folder contents
   - Read
5. Click **Apply** → **OK**

---

## Part D — Test the site

### 7) Verify access works
1. In IIS Manager, select **Default Web Site**
2. Click **Browse Website**
3. Confirm:
   - The website opens successfully
   - Authentication behavior matches your settings (no anonymous access)

---

## Verification checklist (what to include in `assets/`)
Add screenshots and name them clearly, for example:
- `assets/01-windows-features-windows-auth.png`
- `assets/02-iis-authentication-settings.png`
- `assets/03-disable-inheritance.png`
- `assets/04-security-tab-users-groups.png`
- `assets/05-browser-test.png`

---

## Troubleshooting
- **Windows Authentication option not visible in IIS**
  - Ensure the Windows Feature “Windows Authentication” is installed (Part A).
- **Getting 401 Unauthorized**
  - Confirm Windows Authentication is enabled and Anonymous is disabled.
  - Confirm the authenticated user is granted NTFS permissions on the website folder.
- **Site breaks after permission changes**
  - Restore required permissions for IIS/app pool identity and re-test.

---

## Notes (safe publishing)
Before making this repo public:
- Blur/redact usernames, machine names, domains, IP addresses from screenshots.
- Do not upload credentials or private configs.

## Author
Muhammad Sameed Asif  
GitHub: https://github.com/Sameed-333
