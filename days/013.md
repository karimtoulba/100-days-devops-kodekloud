# Day 013 - IPTables Installation and Configuration

## 🎯 Objective

Install and configure IPTables to allow traffic from a specific IP while blocking all other access to a port.

---

## Install IPTables

```bash
sudo yum install iptables iptables-services -y
sudo systemctl enable --now iptables
```

---

## Configure Firewall Rules

Clear existing rules:

```bash
sudo iptables -F
```

Allow port **8083** from a specific IP:

```bash
sudo iptables -A INPUT -p tcp -s 10.244.196.3 --dport 8083 -j ACCEPT
```

Block all other traffic to port **8083**:

```bash
sudo iptables -A INPUT -p tcp --dport 8083 -j DROP
```

---

## Save the Rules

```bash
sudo sh -c 'iptables-save > /etc/sysconfig/iptables'
```

---

## Restart IPTables

```bash
sudo systemctl restart iptables
```

---

## Verify Rules

```bash
sudo iptables -L -n --line-numbers
```

---

✅ **Day 013 Complete**