
---

## **3. Файл `Windows-Guide.md`**  
```markdown
# 🪟 Изменение TTL в Windows  

### **Способ 1: Через реестр (навсегда)**  
1. Открой **Редактор реестра** (`Win + R` → `regedit`).  
2. Перейди в:  **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters**

3. Создай **DWORD-параметр** с именем `DefaultTTL` (если нет).  
4. Установи значение **65** (Десятичная система).  
5. Перезагрузи ПК.  

### **Способ 2: Через PowerShell (временно)**  
```powershell
netsh int ipv4 set glob defaultcurhoplimit=65

#Проверка
ping 127.0.0.1  # Должно быть ttl=65