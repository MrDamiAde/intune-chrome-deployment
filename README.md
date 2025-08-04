# Deploy Google Chrome with Intune (Win32 App)

This lab shows how I successfully packaged and deployed Google Chrome to a Windows device using Microsoft Intune.

##⚙️ Lab Environment

- Created using a **Microsoft 365 E3 free trial** (includes Intune)
- Ran Windows virtual machines using **VMware Workstation Player** (free)
- Simulated real-world device onboarding and app deployment scenarios

---

## 📦 Step-by-Step Deployment Process

### 1. Download Required Tools

- **Google Chrome Enterprise MSI**  
  [https://chromeenterprise.google/browser/download/](https://chromeenterprise.google/browser/download/)
  
- **Microsoft Win32 Content Prep Tool**  
  [https://github.com/microsoft/Microsoft-Win32-Content-Prep-Tool](https://github.com/microsoft/Microsoft-Win32-Content-Prep-Tool)

---

### 2. Prepare Folder Structure

```text
C:\IntuneApps\
├── Chrome\                  → contains the .msi file
├── Output\                  → stores the .intunewin file
└── ContentPrepTool\        → contains IntuneWinAppUtil.exe
```
### 3. Package the Chrome Installer

```powershell
.\IntuneWinAppUtil.exe -c "C:\IntuneApps\Chrome" -s GoogleChromeStandaloneEnterprise64.msi -o "C:\IntuneApps\Output"
```
### 4. Upload to Intune

Go to Intune Admin Centre → Apps → Windows → Add
Choose Win32 app
Upload the .intunewin file generated in Step 3

### 5. Configure App Settings and Assign the App
Assign the app to the test user group 

### 6. Sync and verify
on the VM, go to 
```Settings > Accounts > Work or School Account > Info > Sync```
Chrome automatically appeared on the desktop after a few minutes 🎉

✅ Summary
This project demonstrated a full cycle of Intune Win32 app deployment in a realistic test environment, all using free tools.
<img width="1225" height="854" alt="Screenshot 2025-08-04 115210" src="https://github.com/user-attachments/assets/6d9e2b08-1005-44be-bb5a-37e288a1847d" />

