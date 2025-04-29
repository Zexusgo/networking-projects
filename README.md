# 📄Project Documentation

---

![Screenshot](repo_layer-1/images1.png)

# 🔹 **Project Title**

Basic LAN Simulation – Physical Layer (OSI Layer 1)

# 🎯 **Goal**

Understand how devices connect physically using cables and switches, and how cable type affects communication.

# 🧪 **Setup Summary**

- 2 PCs, 1 switch
- Copper straight-through cables
- Assigned manual IPs
- Used ping to test physical + data layer success

# 🔧 **Step-by-Step with Reflections**

1. Connected PC0 and PC1 to Switch using straight-through cables
2. Go, to IP configuration of PCO. Its in static. 
3. First try: I turned the static into DHCP. Done same with PC1
4. It shows DHCP failed. APIPA is being used. 
5. Still, it shows IP address and subnet mask. So, I tried my hand at  

Result:

![image.png](repo_layer-1/images2.png)

# 📚 **Deep Dive: What’s Actually Happening**

- When I selected **DHCP** on both PCs, they couldn’t find a DHCP server.
- As a fallback, the operating system assigned **APIPA addresses** in the range:
    
    **169.254.0.1 to 169.254.255.254**, with subnet mask **255.255.0.0**.
    
- This is an OS feature (e.g., Windows) to enable limited communication when DHCP fails.
- Both PCs were assigned APIPA addresses.
- Despite not having a DHCP server, I was **able to successfully ping** from PC0 to PC1.
- This means:
    - Both PCs were on the **same switch** (same Layer 2 domain).
    - The switch forwarded the traffic successfully based on MAC address.
    - The PCs considered each other in the same subnet, so no routing was needed.

### 🧠 **Important Note:**

- **In real life**, APIPA **can** allow basic local communication on a switch — **if both devices use APIPA and are in the same subnet**.
- However, APIPA is not reliable for production environments:
    - It doesn't work across routers.
    - Some firewalls block it.
    - Not all software supports it consistently.
- In some labs or older Packet Tracer versions, APIPA pings might fail.

### 📌 **Takeaway:**

- **APIPA worked here**, but it’s still best practice to use **manual or DHCP IPs** for predictable connectivity in networks and labs.
