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
```
![](/images/ping_vm-security.png)
![](/images/ssh-vm-security.png)

#### Observation:
- NOC subnet can reach Security VM; SSH and ping succeed.

### Step 2 — Security → VM-NOC (Denied)

```bash
# From vm-security
ping 10.0.1.4          # Should succeed ✅
ssh azureuser@10.0.1.4 # Should fail ❌
```
![](/images/ping-vm-noc.png)
![](/images/denied-ssh.png)

#### Observation:
- NSG denies SSH but allows ping, as expected.

### Step 3 — NOC → VM-NOC (Internal Subnet Access)

```bash
# From vm-security
ping 10.0.2.4           # Should succeed ✅
ssh azureuser@10.0.2.4  # Should succeed ✅
```
![](/images/ping-from-vm-noc-to-self.png)
![](/images/ssh-noc-noc.png)

#### Observation:
- NOC users can reach other NOC VMs within the same subnet.