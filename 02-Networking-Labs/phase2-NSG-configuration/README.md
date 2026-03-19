## Phase 2 — Network Security Group (NSG) Configuration

**Steps Performed:**
- Created virtual network `vnet-lab` with subnets:
  - `subnet-noc` for NOC VMs
  - `subnet-security` for Security VMs

![](/images/vnet-and-subnets.png)

- Deployed VMs in corresponding subnets
- Configured NSG rules:

**NSG Rules Overview:**

| Subnet          | Rule Name            | Priority | Port | Protocol | Source        | Destination | Action |
|-----------------|--------------------|---------|------|----------|---------------|------------|--------|
| subnet-noc      | allow-ssh-from-noc  | 110     | 22   | TCP      | 10.0.1.0/24  | Any        | Allow  |
| subnet-noc      | allow-ssh-my-ip     | 100     | 22   | TCP      | <Laptop IP>  | Any        | Allow  |
| subnet-noc      | deny-ssh            | 120     | 22   | TCP      | Any           | Any        | Deny   |
| subnet-noc      | allow-ping          | 130     | Any  | ICMP     | Any           | Any        | Allow  |
| subnet-security | allow-ssh-my-ip     | 100     | 22   | TCP      | <Laptop IP>  | Any        | Allow  |
| subnet-security | allow-ssh-from-noc  | 110     | 22   | TCP      | 10.0.1.0/24  | Any        | Allow  |
| subnet-security | deny-ssh            | 120     | 22   | TCP      | Any           | Any        | Deny   |
| subnet-security | allow-ping          | 130     | Any  | ICMP     | Any           | Any        | Allow  |

**Notes:**
- NSGs applied at **subnet level** and **VM NIC level** for testing
- Priorities determine rule evaluation order
- ICMP allowed for ping tests; SSH restricted according to RBAC & subnet
