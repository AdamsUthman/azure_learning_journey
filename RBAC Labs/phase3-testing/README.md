## Phase 3 — VM Testing

**Test Environment:**
- VMs:
  - `vm-noc` (Private IP: 10.0.1.4, Public IP: 20.124.90.247)
  - `vm-security` (Private IP: 10.0.2.4, Public IP: 20.83.156.175)
- Laptop external IP allowed for SSH via NSG rules
- All internal VM-to-VM tests use **private IPs**

---

### Step 1 — NOC → VM-Security (Allowed)

```bash
# From vm-noc
ping 10.0.2.4          # Should succeed ✅
ssh azureuser@10.0.2.4 # Should succeed ✅


