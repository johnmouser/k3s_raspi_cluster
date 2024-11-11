# K3s Raspberry Pi Cluster

## **Overview**

**Single Master** K3s cluster with two agent nodes running on Raspberry Pi 4Bs.  

## **Disclaimer**

This setup is still a work in progress and may not adhere to industry best practices. In its current form, it's primarily designed as a quick-and-dirty solution to redeploy my lab cluster whenever I inevitably break it (because, let’s face it, I *will*).  

## **Technologies Used**

- **Raspberry Pi 4B** (8GB) as the hardware platform
- **Pi OS Lite (64-bit Bookworm)** as the base operating system
- **K3s** for lightweight Kubernetes management
- **Rancher** for Kubernetes management and multi-cluster management
- **Helm** for managing apps and deploying packages via charts
- **Jetstack** for certificate management
- **Nginx** for reverse proxying
- **MetalLB** for load balancing
- **Nftables** for host-based firewall

## **Setup Instructions**

### 1. **Add the following content to your `inventory.ini` file:**

```
[master]
x.x.x.x   # Replace with the IP of the master node

[agents]
x.x.x.x   # Replace with the IP of each agent node
x.x.x.x
```

### 2. **Create the `group_vars/vars.yml` file and insert the following:**

```
metallb_range: "x.x.x.x-x.x.x.x"   # IP range for MetalLB to assign to services on your LAN

k3s_token: "*****"   # Add a cluster token here 
```

### 3. **Execute Playbook**

```
ansible-playbook -i inventory.ini site.yml
```

## 💬 **Notes**

- I use NFS shared storage but its commented out in site.yml. Ignore it.


---

> Happy tinkering! 🎉  
> **Contributions and suggestions are welcome.** 🙌




