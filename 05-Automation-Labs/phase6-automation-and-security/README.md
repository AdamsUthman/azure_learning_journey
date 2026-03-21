# Phase 6 — Automation & Security Engineering

**Focus:** Automate Azure resource management and enforce secure network access.

---

## Objectives

- Deploy, manage, and delete Azure VMs using CLI.
- Apply NSG rules for internal segmentation.
- Test jump-host architecture.
- Understand stopped vs deallocated VM states for cost efficiency.
- Prepare for automated workflows.

---

## Lab Environment

- **Resource Group:** `rg-automation-labs`
- **Virtual Network:** `vnet-automation`
- **Subnet:** `subnet-automation`
- **Virtual Machines:** `vm-automation`, `vm-automation-2`
- **NSG Rules:** Configured for segmentation and jump-host access.

---

## Step-by-Step Instructions

### Step 1 — Deploy VMs

```bash
az vm create \
  --resource-group rg-automation-labs \
  --name vm-automation \
  --image Ubuntu2204 \
  --admin-username azureuser \
  --generate-ssh-keys \
  --vnet-name vnet-automation \
  --subnet subnet-automation
```


### Step 2 — Test VM Connectivity

```bash
ping <VM2_private_IP>
ssh azureuser@<VM2_private_IP>
```
#### Observation
- VMs communicate internally.


### Step 3 — Apply NSG Segmentation

```bash
az network nsg rule create \
  --resource-group rg-automation-labs \
  --nsg-name nsg-automation \
  --name Deny-SSH-VNet \
  --priority 200 \
  --protocol Tcp \
  --direction Inbound \
  --source-address-prefix VirtualNetwork \
  --destination-address-prefix VirtualNetwork \
  --destination-port-range 22 \
  --access Deny
```

#### Observation
- Internal SSH blocked, ping allowed.


### Step 4 — Jump Host Architecture

```bash
az network nsg rule create \
  --resource-group rg-automation-labs \
  --nsg-name nsg-automation \
  --name Allow-SSH-VM1-to-VM2 \
  --priority 150 \
  --protocol Tcp \
  --direction Inbound \
  --source-address-prefix <VM1_private_IP> \
  --destination-address-prefix <VM2_private_IP> \
  --destination-port-range 22 \
  --access Allow
```

#### Observation
- Only VM1 can SSH into VM2.


### Step 5 — VM Lifecycle Management

```bash
az vm stop --name vm-automation-2 --resource-group rg-automation-labs
az vm deallocate --name vm-automation-2 --resource-group rg-automation-labs
az vm start --name vm-automation-2 --resource-group rg-automation-labs
az vm delete --name vm-automation-2 --resource-group rg-automation-labs --yes
```

#### Observation
- Learned difference between stopped and deallocated states; deallocation saves costs.

---

### Key Takeaways

- NSG rules control internal traffic and enforce segmentation.
- Jump host architecture ensures secure access to internal VMs.
- Azure CLI enables repeatable, automated workflows.
- Deallocating VMs helps manage costs in real cloud environments.
- Practicing these steps builds a strong foundation for cloud security engineering.

