# 🐧 Изменение TTL в Linux  

### **Способ 1: Через iptables (рекомендуется)**  
```bash
sudo iptables -t mangle -A POSTROUTING -j TTL --ttl-set 65

### Сохранить правило
sudo apt install iptables-persistent -y
sudo netfilter-persistent save

Способ 2: Через sysctl (навсегда)
echo 65 | sudo tee /proc/sys/net/ipv4/ip_default_ttl

Для сохранения после перезагрузки:

echo "net.ipv4.ip_default_ttl = 65" | sudo tee -a /etc/sysctl.conf
sudo sysctl -p 

📌 Проверка:
ping localhost  # Должно быть ttl=65