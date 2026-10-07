# Installing WSL on Windows

WSL (Windows Subsystem for Linux) allows you to run a Linux environment directly inside Windows.

> **Requirements:** Windows 11 or Windows 10 version 2004 (Build 19041) or newer.

## 1. Install WSL

Open **PowerShell as Administrator**:

1. Open the Start menu.
2. Search for `PowerShell`.
3. Right-click **Windows PowerShell** and select **Run as administrator**.

Run:

```powershell
wsl --install
```

This installs **WSL 2** and **Ubuntu** by default.

Restart Windows when prompted.

## 2. Create your Linux account

After restarting, open **Ubuntu** from the Start menu.

The first launch completes the installation and asks you to create:

```text
Enter new UNIX username:
New password:
Retype new password:
```

Choose a username and password.

> When entering a Linux password, **nothing appears on screen**. This is normal.

This account is separate from your Windows account and can perform administrative tasks using `sudo`.

## 3. Update Ubuntu

Once the Linux terminal opens, run:

```bash
sudo apt update
sudo apt upgrade -y
```

Enter the Linux password you created when prompted.

## 4. Check the installation

From PowerShell, run:

```powershell
wsl --list --verbose
```

You should see something similar to:

```text
NAME      STATE     VERSION
Ubuntu    Running   2
```

The `VERSION` should normally be **2**.

## 5. Start WSL

You can start Ubuntu from the Start menu or directly from PowerShell:

```powershell
wsl
```

To leave Linux:

```bash
exit
```

You now have a working Linux environment inside Windows able to connect to Hyperion without issues