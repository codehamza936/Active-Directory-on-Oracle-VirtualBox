# 🧪 Home Lab: Active Directory with Oracle VirtualBox  
**Automate User Creation with PowerShell**

![Home Lab Overview](https://github.com/codehamza936/Active-Directory-on-Oracle-VirtualBox/blob/main/Screenshort/Main.png?raw=true)

---

## 🧾 TL;DR

**Tech Stack:**  
`Oracle VirtualBox` · `Windows Server 2019` · `Windows 10` · `PowerShell`

**Quick Downloads:**

- [Oracle VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- [Windows Server 2019 ISO](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019)
- [Windows 10 ISO](https://www.microsoft.com/en-us/software-download/windows10)

This project sets up a lightweight home lab for Active Directory using Oracle VirtualBox. You'll deploy a Windows Server virtual machine as a domain controller, install and configure Active Directory Domain Services (AD DS), and automate user creation via PowerShell.

---

## 📘 Introduction

This guide walks you through building a simple yet powerful Active Directory environment in a virtualized lab. You’ll:

- Set up a Windows Server VM using VirtualBox
- Configure AD DS and promote the server to a domain controller
- Use PowerShell scripts to bulk-create AD users

Perfect for practice, certification prep, or infrastructure simulation.

---

## 🛠️ Stage 1: Set Up Oracle VirtualBox and Create a VM

1. **Install VirtualBox**  
   Download and install from the [official site](https://www.virtualbox.org/wiki/Downloads).
   
![VM Creation](https://github.com/codehamza936/Active-Directory-on-Oracle-VirtualBox/blob/main/Screenshort/2.png?raw=true)

3. **Create a Windows Server VM**  
   - Launch VirtualBox  
   - Select "New" → Choose "Windows Server" as the OS  
   - Allocate CPU, RAM, and disk space appropriately

![Windows Setup](https://github.com/codehamza936/Active-Directory-on-Oracle-VirtualBox/blob/main/Screenshort/3.png?raw=true)


---

## 💾 Stage 2: Install Windows Server

1. **Download the ISO**  
   Get it from the [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019).

2. **Install the OS**  
   - Mount the ISO in VirtualBox  
   - Run through the installer  
   - Set a strong Administrator password

3. **Configure Networking & Enhancements**  
   - Enable internet access  
   - Install VirtualBox Guest Additions for better VM performance


---

## 🧱 Stage 3: Install & Configure Active Directory Domain Services (AD DS)

1. **Install AD DS Role**
   - Open `Server Manager`
   - Go to **Add Roles and Features**
   - Select **Active Directory Domain Services**

![AD DS Role](https://github.com/codehamza936/Active-Directory-on-Oracle-VirtualBox/blob/main/Screenshort/4.png?raw=true)

2. **Promote Server to Domain Controller**
   - Use the **AD DS Configuration Wizard**
   - Create a new forest and specify your domain name
   - Reboot when prompted

![Promote to DC](https://github.com/codehamza936/Active-Directory-on-Oracle-VirtualBox/blob/main/Screenshort/5.png?raw=true)

3. **Verify Setup**
   - After reboot, check Server Manager for AD DS and DNS role status

---

## ⚙️ Stage 4: Automate AD User Creation with PowerShell

1. **Launch PowerShell as Admin**  
   Open PowerShell on the domain controller with elevated privileges.

   ![Promote to DC](https://github.com/codehamza936/Active-Directory-on-Oracle-VirtualBox/blob/main/Screenshort/6.png?raw=true)

3. **Sample Script to Create Users**
```powershell
Import-Module ActiveDirectory

For ($i = 1; $i -le 10; $i++) {
    $username = "user$i"
    $password = ConvertTo-SecureString "P@ssword123" -AsPlainText -Force
    New-ADUser -Name $username `
               -SamAccountName $username `
               -UserPrincipalName "$username@yourdomain.local" `
               -AccountPassword $password `
               -Enabled $true `
               -Path "OU=Users,DC=yourdomain,DC=local"
}
```

## ✅ Results

By the end of this project, I had a fully functional Active Directory lab environment running inside Oracle VirtualBox. I:

- Deployed a Windows Server virtual machine as my domain controller
- Installed and configured Active Directory Domain Services (AD DS)
- Used PowerShell scripts to automate the creation of user accounts

This setup successfully simulated a basic enterprise network, giving me a lightweight and flexible environment to practice user management, domain control, and scripting techniques—all from my personal machine.

---

## 🧩 Conclusion

Working through this home lab gave me valuable, hands-on experience with Windows Server administration and Active Directory. I learned how to:

- Install and configure a domain controller from scratch
- Understand and manage Active Directory components
- Use PowerShell to automate common administrative tasks

This project helped strengthen my skills in system administration and network management. It also prepared me for more advanced topics, like Group Policy, DHCP/DNS roles, and domain-level automation. Whether you're studying for certifications or building out your I

