## 1. Initial DNS Resolution Test

### Objective

Verify that AdGuard Home responds to DNS queries from a client on the local network.

### Test command

Run from the client computer, replacing `PI_IP` with the Raspberry Pi's LAN IP address:

```bash
nslookup google.com PI_IP
```

### Expected result

- The DNS server corresponds to the Raspberry Pi.
- The query returns an IP address for `example.org`.
- The request appears in the AdGuard Home Query Log.

### Results

- [✓] DNS query completed successfully.
- [✓] Correct DNS server confirmed.
- [✓] Query visible in AdGuard Home Query Log.
- [✓] Screenshot saved as `screenshots/dns-query-test.png`.

**Status:** Pending verification.