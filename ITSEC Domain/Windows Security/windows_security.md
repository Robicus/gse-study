# Windows Security

## Exam Outcome

Demonstrate general knowledge of Windows Security and proficiency in a Windows environment.

## Service Packs, Hotfixes, and Backups

Source:  401.5, Module 24

### Windows Server Update Services (WSUS)

WSUS functions as an internally hosted Windows update.  It's built into Windows Server and operates as an IIS web application.  Administrators can control exactly which hotfixes and updates to deploy.

## Windows Access Controls

Source:  401.5, Module 25

### Windows Permissions and Privileges

The Windows NT File System (NTFS) offers permissions controls, auditing, encryption, compression, and transactional-oriented processing.  Within NTFS, every object as an owner and its up to their discretion to modify permissions (DACL).

A good DACL to default to:
System: Full Control
Administrators: Full Control
CREATOR OWNER: Full Control
Authenticated Users: Read & Execute (or Modify)

### Windows Registry

All configuration settings for the computer's hardware, operating system, applications, and its users' preferences are stored in registry.  You can explore, view, and edit registry settings with regedit.exe and/or PowerShell.

### Understanding Privileges

Unlike permissions, privileges are NOT tied to a particular object (like a folder, file, or the registry); instead, privileges references a general capability, i.e., "Take Ownership". Privileges are tied to users' Security Access Tokens (SATs).

### Windows BitLocker

Microsoft's built-in whole disk encryption utility.  Sectors are encrypted with AES (128-256 vit), includes boot-up integrity checking with a TPM, and supports USB and thunderbolt devices.

TPMs are chips in the motherboard that perform encryption, hashing, random key generation, secure key storage, and other cryptographic functions.

## Enforcing Security Policy

Source:  401.5, Module 26

### Security Templates

A security template is a plain text configuration file that can be store hundreds of security settings.  A computer can be stamped with a template and reconfigured in one shot to match the settings in the template.

A template can configure password policies, account lockout policies, Kerberos policies, audit, registry key permissions, etc.

### Group Policy

Applies to computer and users and often managed through the domain (via Active Directory).
Checklist of GPO settings:

1. Password Policy
2. Account Lockout Policy
3. Security Options
4. Anonymous Access Control
5. Kerberos
6. NTLMv2
7. Guest Acccount
etc.

### AppLocker

AppLocker is a tool that permits administrators to define exactly which executables can and cannot be run in a Windows environment. Rules can be defined by SHA256, local path, network path to program, code signing certificates, and user's group membership - they can be applied to executables, installer packages, scripts, and APPX packages.

## Securing Windows Network Services

Source:  401.5, Module 27

Best rule of thumb:  Don't need a service?  Disable it!

### RDP Best Practices

Require network level authentication
Get latest version of thin client software from Microsoft
Use smart card authentication for single sign-one

### Windows Passwords

#### LAN Manager (LANMAN)

Old Windows (NT) password schema that is insanely easy to crack.

- 14 character lenght
- Splits password into two 7 character strings

