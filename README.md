# 📦 Windows 11 25H2: Debloat Default Microsoft Store Apps via Group Policy

## 📝 Overview

Windows 11 version 25H2 introduces a new **Group Policy** setting that allows system administrators to **debloat** the OS by automatically **removing default Microsoft Store apps** during new user account creation.

This guide explains how to use the new policy step by step, including setup, testing, and registry verification.

---

## 📌 Key Points

- ✅ Only available on **Windows 11 Pro or higher**
- 🚫 Not available on Windows 11 Home
- 🛠️ Removes **Microsoft Store-based apps only**
- 👤 Applies **only to new user accounts**
- 🧪 Currently part of the **Insider Preview Builds (Beta/Dev Channels)**

---

## 📁 List of Apps That Can Be Removed

The following 25 inbox apps can be uninstalled using this policy:

- Feedback Hub  
- Microsoft 365 Copilot  
- Microsoft Clipchamp  
- Microsoft News  
- Microsoft Photos  
- Microsoft Solitaire Collection  
- Microsoft Sticky Notes  
- Microsoft Teams  
- Microsoft To Do  
- MSN Weather  
- Outlook for Windows  
- Paint  
- Quick Assist  
- Snipping Tool  
- Windows Calculator  
- Windows Camera  
- Windows Media Player  
- Windows Notepad  
- Windows Sound Recorder  
- Windows Terminal  
- Xbox Gaming App  
- Xbox Gaming Overlay  
- Xbox Identity Provider  
- Xbox Speech To Text Overlay  
- Xbox TCUI  

---

## ⚙️ How to Enable Debloat Policy via Group Policy

### 🪟 Step-by-Step Guide

1. Press `Win + S` and search for: **Edit Group Policy**  
2. Navigate to the following path:  
```
Computer Configuration > Administrative Templates > Windows Components > App Package Deployment
```
3. Locate the policy:

```
Remove Default Microsoft Store packages from the system
```

5. Double-click the policy, then:
- Select **Enabled**
- Click **Apply**
- Click **OK**

5. Done! The policy is now active.

📝 For testing, try selecting apps like **Microsoft News** and **Xbox** to be removed.

---

## 🔍 Registry Check (Optional)

After enabling the policy, the system creates a registry key:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Appx\RemoveDefaultMicrosoftStorePackages
```

You’ll see entries for each app, for example:

- `Microsoft.Xbox.TCUI` → `RemovePackage = 1` ✅ (Removed)
- `Microsoft.MediaPlayer` → `RemovePackage = 0` ❌ (Still Present)

---

## 👤 Test the Policy with a New User Account

To verify that apps are removed for new users:

1. Open **Settings**
2. Go to **Accounts**
3. Click **Add Account**
4. Choose **Local Account**
5. Use:
   - Username: `test`
   - Password: `P@ssw0rd@123`
6. Log out and switch to the new account
7. Check for apps like **Xbox** or **Microsoft News**  
   ✅ They should be gone!

---

## 💡 Why This Feature Helps System Admins

This debloat feature is useful because:

- Reduces clutter and distractions
- Removes unused default apps for enterprise environments
- Streamlines the system image before deployment
- Gives admins better control over app provisioning

---

## ⚠️ Notes & Limitations

- ❗ **Only works for new accounts**, not existing ones
- ❗ **Removes only Microsoft Store apps**, not promotional apps or admin-installed software
- ❗ Requires Windows 11 **25H2 Pro or higher**
- ❗ Not available in **Home edition**

---

## 🧪 Enable Feature on Unsupported Builds (Optional)

If you're not seeing this policy, you can **force-enable** it using **ViveTool**:

### 📥 Download and Setup ViveTool

1. Download from:  
   [https://github.com/thebookisclosed/ViVe/releases](https://github.com/thebookisclosed/ViVe/releases)

2. Extract the ZIP file to a location, e.g.:  
```

C:\Users\<YourName>\Downloads\ViveTool

````

3. Open **Command Prompt as Administrator**

4. Run the following commands:

```cmd
cd C:\Users\<YourName>\Downloads\ViveTool
````

```cmd
vivetool /enable /id:48433719,57056100
````

5. You should see:
```
Successfully set feature configuration(s)
```

7. Restart your PC.

---

## 📆 Availability

* This feature is part of **Windows 11 25H2** (expected fall 2025)
* Currently available in **Insider Beta/Dev Channel Builds**
* Not yet confirmed for version 24H2

---

## ✅ Summary

With Windows 11 25H2, Microsoft is giving system administrators better tools to **reduce bloatware** and streamline deployments. This guide provides a complete walkthrough for enabling and verifying the new app removal policy.

> 🧑‍💻 Take full control of your Windows image and simplify user environments with this new Group Policy.

---

