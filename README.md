# IIS Site Security Basics (Windows Authentication + Permissions)

This mini-project demonstrates basic hardening of an IIS website on Windows by enabling **Windows Authentication**, disabling **Anonymous Authentication**, and tightening **NTFS permissions** for controlled access.

**Course:** System & Network Administration (SNA Lab)  
**Tool Used:** Internet Information Services (IIS)  
**Focus:** Authentication hardening, NTFS permission control, access validation

---

## Tools & Technologies
- Windows 11 (similar steps apply on Windows 10 / Windows Server)
- IIS (Internet Information Services)
- Windows Features (to enable IIS security components)
- IIS Manager (Authentication settings)
- NTFS Permissions (Security tab / Advanced permissions)

---

## Project Files
- `report/IIS-Site-Security-Basics.pdf` (detailed lab report)
- `assets/` (screenshots: configurations, permissions, validation)

---

## What’s Demonstrated
- Installing/enabling **Windows Authentication** for IIS
- Disabling **Anonymous Authentication** for the target site
- Reconfiguring Default Web Site folder permissions:
  - Disabling inheritance
  - Converting inherited permissions into explicit permissions
  - Managing allowed users/groups
- Testing the site after applying security controls

---

## Key Learning
- How IIS authentication modes affect website access
- How NTFS permissions control who can read/execute website files
- Why permission inheritance should be reviewed for hosted content
- How to verify security changes without breaking availability

---

## Screenshots
Evidence is available in `assets/`:
- `01-windows-features-windows-auth.png`
- `02-iis-authentication-settings.png`
- `03-disable-inheritance.png`
- `04-security-tab-users-groups.png`
- `05-browser-test.png`

---

## How to Run
1. Clone the repository:
```bash
git clone https://github.com/Sameed-333/iis-site-security-basics.git
```

2. Navigate to the project folder:
```bash
cd iis-site-security-basics
```

3. Review the lab report and evidence:
- Open `report/IIS-Site-Security-Basics.pdf`
- Review screenshots in `assets/`

4. Apply and validate (high-level):
- Enable Windows Authentication and disable Anonymous Authentication for the site
- Adjust NTFS permissions on the website directory to allow only required users/groups
- Browse the site to confirm expected authentication behavior and availability

### Disclaimer
This project is for educational purposes only as part of a university SNA lab. It demonstrates basic IIS authentication and permission hardening in a controlled environment and is not intended as a complete production security baseline.
