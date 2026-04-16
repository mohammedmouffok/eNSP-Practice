# 🔐 Security & Password Configuration (Router ↔ PC via Console)

## 📌 Overview
This section explains how to securely access a router from a PC using the console port, and how to configure authentication using Password mode and AAA mode (Huawei / eNSP environment).

---

## 🖥️ Physical Connection

- Use a console cable (RJ45 to USB/Serial)
- Connect:
  - PC ➝ Router Console Port
- Open terminal software:
  - eNSP console / PuTTY / SecureCRT

---

## ⚙️ Basic Access (Password Mode)

### Configuration:

```
<Huawei> system-view
[Huawei] user-interface console 0
[Huawei-ui-console0] authentication-mode password
[Huawei-ui-console0] set authentication password cipher YOUR_PASSWORD
```

### Explanation:
- user-interface console 0 → Access console line
- authentication-mode password → Enable password authentication
- set authentication password → Define encrypted password

---

## 🔐 Advanced Access (AAA Mode)

### Configuration:

```
<Huawei> system-view
[Huawei] aaa
[Huawei-aaa] local-user admin password cipher YOUR_PASSWORD
[Huawei-aaa] local-user admin service-type terminal

[Huawei] user-interface console 0
[Huawei-ui-console0] authentication-mode aaa
```

### Explanation:
- aaa → Enter AAA configuration
- local-user admin → Create user
- service-type terminal → Allow console login
- authentication-mode aaa → Enable AAA login

---

## 🧪 Verification

- Disconnect and reconnect console
- Expected:
  - Password prompt (Password mode)
  - Username + password (AAA mode)

---

## ⚠️ Best Practices

- Use AAA mode instead of password mode
- Use strong passwords
- Disable unused interfaces
- Save configuration:

```
[Huawei] save
```

---

## 📊 Comparison

| Mode      | Security Level | Features            |
|----------|--------------|---------------------|
| Password | Low          | Simple login        |
| AAA      | High         | User-based control  |

---

## ✅ Notes
- AAA is required in real-world enterprise networks
- This configuration is aligned with HCIA-Datacom exam objectives
