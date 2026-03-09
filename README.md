# endpoint-zero-to-hero
Zero-touch enterprise device provisioning with Microsoft Intune, Entra ID &amp; Windows Autopilot

📋 Project Overview
A fully automated, zero-touch endpoint provisioning pipeline built on Microsoft Intune, Microsoft Entra ID (Azure Active Directory), and Windows Autopilot.

Goal: A new hire opens their laptop out of the box — and without a single manual IT step, the device is named, encrypted, policy-compliant, and app-ready.

Tenant: dgtechnology369.onmicrosoft.com
Admin: DipenGohel@dgtechnology369.onmicrosoft.com
Completed: March 2026

🏗 Architecture
NEW HIRE              ENTRA ID               INTUNE                DEVICE
────────              ────────               ──────                ──────
📦 Receives    ──▶   👤 User Created   ──▶  📋 Compliance   ──▶  💻 Auto
   Laptop            🔑 Licence Assign       ⚙️  Config           Pilot
                     👥 Group Added          📦 Apps Deploy       Setup
                     🔒 MFA Ready            🛡️  Defender

                Zero IT helpdesk involvement. Zero manual steps.

📁 Project Structure
zero-touch-onboarding/
│
├── 📄 README.md                         ← You are here
├── 📄 ZeroTouch_Onboarding_Pipeline.docx ← Full technical documentation
│
├── 📁 screenshots/
│   ├── 01_M365_Admin_Center.png
│   ├── 02_Intune_Dashboard_Clean.png
│   ├── 03_Security_Groups.png
│   ├── 04_Users_List.png
│   ├── 05_User_Profile.png
│   ├── 06_Compliance_Policy_Settings.png
│   ├── 07_Compliance_Assignments.png
│   ├── 08_Device_Restriction_Profile.png
│   ├── 09_BitLocker_Policy.png
│   ├── 10_Update_Ring.png
│   ├── 11_M365_Apps_Suite.png
│   ├── 12_Mozilla_Firefox_Store.png
│   ├── 13_Autopilot_OOBE_Profile.png
│   └── 14_Enrollment_Status_Page.png
│
└── 📁 policies/
    └── policy-summary.md

🗺 Pipeline Phases
#PhaseComponentKey Deliverable0Lab SetupM365 Admin CenterTenant provisioned — dgtechnology3691IdentityEntra ID4 users + 3 security groups2ComplianceIntune PolicyWIN-Compliance-Baseline3ConfigurationDevice ProfilesRestrictions + BitLocker + Update Ring4AppsApp DeploymentM365 Suite (Required) + Firefox (Available)5ProvisioningWindows AutopilotAutoPilot_UserDriven_Profile + ESP

👥 Test User Personas
NameUsernameDepartmentTitleGroupArjun Sharmaarjun.sharma@dgtechnology369…EngineeringSoftware EngineerGRP_EngineeringJake Reynoldsjake.reynolds@dgtechnology369…EngineeringDevOps EngineerGRP_EngineeringPriya Patelpriya.patel@dgtechnology369…FinanceFinancial AnalystGRP_FinanceZara Malikzara.malik@dgtechnology369…HRHR CoordinatorGRP_HR

🔒 Phase 2 — Compliance Policy: WIN-Compliance-Baseline
Platform: Windows 10 and later
Device Health
SettingValueBitLocker✅ RequireSecure Boot✅ RequireCode Integrity✅ Require
System Security
SettingValuePassword required✅ RequirePassword typeAlphanumericPassword complexityDigits + lowercase + uppercase + special charsMinimum password length4 charactersPassword expiration7 daysPrevious passwords blocked5Firewall✅ RequireAntivirus✅ Require
Assignments

✅ GRP_Finance (1 user)
✅ GRP_Engineering (2 users)
✅ GRP_HR (1 user)


⚙️ Phase 3 — Configuration Profiles
1. WIN-DeviceRestriction-Baseline
SettingValueCamera🚫 BlockCortana🚫 BlockScreen capture🚫 BlockEnd processes from Task Manager🚫 Block
2. WIN-BitLocker-Policy
Profile type: Endpoint Protection
SettingValueEncrypt devices✅ RequireWarning for other disk encryption🚫 BlockAllow standard users to enable encryption✅ AllowAdditional authentication at startup✅ RequireOS drive recovery✅ EnableSave BitLocker recovery info to Entra ID✅ EnableStore recovery info BEFORE enabling BitLocker✅ RequireFixed drive recovery✅ Enable

🔑 Key Feature: Recovery keys auto-escrowed to Microsoft Entra ID. IT can retrieve keys from the portal — no lost keys, ever.

3. WIN-UpdateRing-Standard
SettingValueMicrosoft product updates✅ AllowWindows drivers✅ AllowQuality update deferral7 daysFeature update deferral30 daysAutomatic update behaviorAuto install at maintenance timeActive hours start8:00 AMActive hours end6:00 PMOption to pause updatesEnable

📦 Phase 4 — Application Deployment
ApplicationTypeAssignmentInstall MethodMicrosoft WordM365 SuiteRequiredSilent auto-installMicrosoft ExcelM365 SuiteRequiredSilent auto-installMicrosoft OutlookM365 SuiteRequiredSilent auto-installMicrosoft PowerPointM365 SuiteRequiredSilent auto-installMicrosoft TeamsM365 SuiteRequiredSilent auto-installMicrosoft OneNoteM365 SuiteRequiredSilent auto-installMicrosoft AccessM365 SuiteRequiredSilent auto-installMicrosoft PublisherM365 SuiteRequiredSilent auto-installMozilla FirefoxStore (UWP)AvailableSelf-service portal

🚀 Phase 5 — Windows Autopilot
AutoPilot_UserDriven_Profile — OOBE Settings
SettingValueDeployment modeUser-DrivenJoin to Microsoft Entra ID asMicrosoft Entra joinedMicrosoft Software License Terms (EULA)🙈 HiddenPrivacy settings🙈 HiddenHide change account options🙈 HiddenUser account typeStandard (NOT local admin)Apply device name templateYesNaming templateCORP-%RAND:4%Example namesCORP-4729, CORP-8831
ESP-Default — Enrollment Status Page
SettingValueShow app and profile config progress✅ YesError if install > X minutes60 minutesCustom error message✅ Yes — configuredLog collection for end users✅ YesOnly show to OOBE devices✅ YesInstall Windows updates during ESP✅ YesBlock device until all apps installed✅ YesAllow user to reset on error❌ NoBlock until required apps installedAll

🎯 The New Hire Experience
Day 1: Arjun receives laptop from courier 📦
  ↓
Step 1: Opens box, powers on device
  ↓
Step 2: Device connects to internet automatically
  ↓
Step 3: Autopilot contacts Intune → applies ALL policies silently
  ↓
Step 4: Device named CORP-XXXX, apps install in background
  ↓
Step 5: Arjun logs in with UPN → forced password change
  ↓
✅ Fully configured. Fully secure. Day 1 productive.
   Zero IT helpdesk calls. Zero manual steps.

🛠 Technologies Used

Microsoft Intune — MDM / compliance / configuration / app management
Microsoft Entra ID — Identity, users, groups, licences
Windows Autopilot — Zero-touch device provisioning
Microsoft Defender — Endpoint antivirus + real-time protection
BitLocker — Full-disk encryption with Entra ID key escrow
Windows Update Rings — Controlled patch deployment


📸 Screenshots
All 14 screenshots documenting each phase are in the /screenshots folder.
ScreenshotPhaseDescription01Phase 0M365 Admin Center — Dipen Gohel, dgtechnology369 tenant02Phase 0Intune Dashboard — 0 devices, clean state03Phase 1Security Groups — GRP_Finance, GRP_Engineering, GRP_HR04Phase 1Users list — all 5 users visible05Phase 1User profile — Dipen Gohel, account enabled, 1 licence06Phase 2Compliance policy — BitLocker, Secure Boot, passwords07Phase 2Compliance assignments — all 3 groups active08Phase 3Device restrictions — Camera, Cortana, screen capture blocked09Phase 3BitLocker policy — Entra ID key escrow enabled10Phase 3Update Ring — 7-day quality + 30-day feature deferral11Phase 4M365 Apps — 8 apps selected12Phase 4Mozilla Firefox — Store app (UWP) available13Phase 5Autopilot profile — CORP-%RAND:4%, Standard user, EULA hidden14Phase 5ESP — Block device until all apps installed

👤 Author
Dipen Gohel

📧 DipenGohel@dgtechnology369.onmicrosoft.com
🔗 LinkedIn

