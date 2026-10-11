## 1. Initial Web Interface and DNS Configuration

### Objective

Configure the AdGuard Home administrator interface and DNS listener.

### Configuration

- **Installation method:** Native Linux installation
- **Platform:** Raspberry Pi 5 running Raspberry Pi OS Lite 64-bit
- **Web administration:** Configured through the initial setup wizard
- **DNS service:** Configured to listen on port 53
- **Administrator credentials:** Stored securely and excluded from Git

### Verification

The following commands are used to verify the service and listening ports:

```bash
sudo systemctl status AdGuardHome --no-pager
sudo ss -lntup | grep -E ':(53|3000)\b'
```

