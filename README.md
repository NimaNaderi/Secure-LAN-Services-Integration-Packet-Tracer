# 🌍 Secure LAN Services Integration (VLAN, Routing, DHCP, DNS, ACL)

Dieses Projekt simuliert eine **sichere Standortvernetzung (WAN)** zwischen einem Hauptquartier (HQ) und einer Zweigstelle (Berlin). Neben der reinen Konnektivität liegt der Fokus auf **Netzwerksicherheit** und **sicherem Management**.

Das Szenario umfasst dynamisches Routing, Internetzugriff für alle Mitarbeiter sowie Zugriffskontrolllisten (ACLs) zum Schutz sensibler interner Ressourcen.

---

## 🚀 Implementierte Features

### 1. LAN-Struktur & Segmentierung
* **VLAN-Segmentierung:** Logische Trennung der Netzwerkbereiche Office und IT zur Isolierung von Endgeräten.
* **Trunking:** VLAN-Übertragung zwischen mehreren Switches und dem Router.

### 2. Routing & Netzwerk-Integration
* **Inter-VLAN-Routing (Router-on-a-Stick):** Zentrale Weiterleitung des Datenverkehrs zwischen den VLANs über Subinterfaces.
* **Zentrales Gateway:** Einheitlicher Netzwerkzugang pro VLAN über den Router.

### 3. Zentrale Netzwerkdienste
* **DHCP-Service:** Automatische Zuweisung von IP-Adressen, Gateways und DNS-Servern an alle Clients.
* **DNS-Service:** Zentrale Namensauflösung für interne Dienste (z. B. Intranet).

### 4. Zugriffskontrolle (Basissicherheit)
* **Access Control Lists (ACLs):** Einschränkung des Zugriffs bestimmter VLANs auf sensible interne Ressourcen.
    * **Regel:** Clients aus dem IT-VLAN dürfen keinen direkten Zugriff auf den internen Server im Office-Netzwerk erhalten.

---

## 🛠️ Technische Konfiguration (Highlights)

### SSHv2 Konfiguration (Sicheres Management)
```cisco
username admin privilege 15 secret cisco123
ip domain-name nextgen.local
crypto key generate rsa
ip ssh version 2
line vty 0 4
 transport input ssh
