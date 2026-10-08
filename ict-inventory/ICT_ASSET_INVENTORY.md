# ICT Asset Inventory

**Site:** Server rack (from site photos)  
**Inventory date:** 2026-10-08  
**Source:** Visual inspection of two rack photographs  
**Status:** Draft — serial numbers, IPs, and exact SKUs require on-site capture  

## Summary counts

| Category | Qty (visible) |
|---|---|
| Servers / compute hosts | 2–3 (2× HP ML310e Gen8 v2 confirmed; +1 HP SFF/tower in Photo 2) |
| Firewall / UTM | 1 (Cyberoam CR 50iNG) |
| Network switch | 1 (TRENDnet PoE+ Gigabit, ~24-port) |
| ISP CPE / wireless gateway | 1 (ZOL-owned) |
| Other routers / APs / appliances | 2–3 (partially identified) |
| Rack enclosure | 1 |
| Cabling lot | 1 (many patch leads + fiber) |

## Device details

### SRV-001 — HP (Hewlett-Packard) ProLiant ML310e Gen8 v2
- **Category:** Server
- **Form factor:** Tower server
- **Location:** Server rack - upper shelf (left)
- **Visible specs:** Intel Xeon; DVD-RW; 4x front USB; perforated front grille
- **Observed status:** Powered ON (green Power + Health LEDs)
- **Connectivity:** Black front USB/console-style cable attached
- **Owner notes:** Internal company asset (verify serial/hostname on site)
- **Criticality:** High
- **Serial / IP:** TBD - capture from rear/iLO label / TBD
- **Next action:** Record serial, iLO IP, OS, RAM/disk config; label front
- **Photo source:** Photo 1

### SRV-002 — HP (Hewlett-Packard) ProLiant ML310e Gen8 v2
- **Category:** Server
- **Form factor:** Tower server
- **Location:** Server rack - upper shelf (right)
- **Visible specs:** Intel Xeon; DVD-RW; 4x front USB; perforated front grille
- **Observed status:** Powered ON (green Power + Health LEDs)
- **Connectivity:** Power/network cabling present (rear not fully visible)
- **Owner notes:** Internal company asset (verify serial/hostname on site)
- **Criticality:** High
- **Serial / IP:** TBD - capture from rear/iLO label / TBD
- **Next action:** Record serial, iLO IP, OS, RAM/disk config; label front
- **Photo source:** Photo 1

### FW-001 — Cyberoam (Sophos lineage) CR 50iNG (NG Series / Future Ready)
- **Category:** Firewall / UTM
- **Form factor:** 1U rack-mount security appliance
- **Location:** Server rack - mid section
- **Visible specs:** 8x RJ45 copper ports; Console port; USB; PWR/SYS/Alarm LEDs
- **Observed status:** Powered ON (Power LED illuminated)
- **Connectivity:** Ethernet cables connected on left-side ports (Photo 2)
- **Owner notes:** Primary perimeter/security gateway candidate
- **Criticality:** Critical
- **Serial / IP:** TBD - capture from rear label / web UI / TBD (management IP)
- **Next action:** Export config; note firmware; plan Sophos/other replacement
- **Photo source:** Photo 1 & Photo 2

### SW-001 — TRENDnet PoE+ Gigabit Switch (appears 24-port; likely TPE-series e.g. TPE-TG240g / similar)
- **Category:** Network Switch
- **Form factor:** 1U rack-mount PoE+ switch
- **Location:** Server rack - below firewall
- **Visible specs:** Approx. 24x Gigabit RJ45; PoE+ capability; link/PoE LED grid
- **Observed status:** Powered ON; many ports active (green/amber LEDs)
- **Connectivity:** Heavy blue/grey Cat5e/Cat6 patching; primary LAN aggregation
- **Owner notes:** Core access/distribution switch for rack LAN
- **Criticality:** Critical
- **Serial / IP:** TBD - capture from rear label / TBD (if managed)
- **Next action:** Confirm exact model/SKU; map port-to-device; note PoE budget
- **Photo source:** Photo 1 & Photo 2

### RTR-001 — ZOL (Zimbabwe Online) provided CPE ISP wireless router/modem (exact model not readable)
- **Category:** ISP Modem / Wireless Gateway
- **Form factor:** Desktop/consumer gateway
- **Location:** Server rack - lower shelf
- **Visible specs:** White chassis; 2 external antennas; perforated top
- **Observed status:** Present / appears in service
- **Connectivity:** Yellow fiber patch visible (Photo 2); Ethernet to LAN; PROPERTY OF ZOL sticker
- **Owner notes:** ISP-owned CPE — do not remove; asset of ZOL, not company owned
- **Criticality:** Critical (internet edge)
- **Serial / IP:** TBD - ISP label / underside / TBD (WAN/LAN IPs from ISP)
- **Next action:** Record circuit ID, WAN IP, support contacts; keep ZOL ownership noted
- **Photo source:** Photo 1 & Photo 2

### NET-001 — Unknown (white chassis; possibly MikroTik or similar) TBD - partially obscured
- **Category:** Router / Small Network Appliance
- **Form factor:** Desktop/small appliance
- **Location:** Server rack - below switch / mid-lower
- **Visible specs:** Multiple RJ45; possible SFP/fiber port; blue link/power LED
- **Observed status:** Appears powered (LED visible)
- **Connectivity:** Blue Ethernet connected; cream/blue patch cables nearby
- **Owner notes:** Identity uncertain from photos — physical inspection required
- **Criticality:** Medium/High (verify role)
- **Serial / IP:** TBD / TBD
- **Next action:** Photograph front label; identify role (router/AP/controller)
- **Photo source:** Photo 1

### NET-002 — Unknown (white unit) / possible TP-Link family appearance TBD
- **Category:** Router / Wireless Access Point
- **Form factor:** Desktop wireless router/AP
- **Location:** Server rack - mid/lower shelf
- **Visible specs:** White plastic; multiple Ethernet; external antennas (grey)
- **Observed status:** Cabled / appears in use
- **Connectivity:** Blue/grey Ethernet connected
- **Owner notes:** Secondary Wi-Fi / LAN device — confirm if still required
- **Criticality:** Medium
- **Serial / IP:** TBD / TBD
- **Next action:** Identify SSID ownership; check if duplicate of ZOL Wi-Fi
- **Photo source:** Photo 1 & Photo 2

### NET-003 — Unknown (silver chassis) TBD
- **Category:** Network Appliance / Small Router or NAS-like device
- **Form factor:** Desktop/small form factor network device
- **Location:** Server rack - lower shelf (beside ZOL CPE)
- **Visible specs:** Silver body; multiple Ethernet in use; 2x front USB; status LEDs
- **Observed status:** Powered ON (blue/green LEDs lit)
- **Connectivity:** Blue Ethernet cables connected; grey antennas nearby
- **Owner notes:** Could be secondary router, firewall, or mini PC — inspect labels
- **Criticality:** Medium
- **Serial / IP:** TBD / TBD
- **Next action:** Photograph underside/rear labels; determine function
- **Photo source:** Photo 2

### PC-001 — HP (Hewlett-Packard) SFF/tower PC or server (exact model not readable in Photo 2)
- **Category:** Workstation / Small Server
- **Form factor:** Small form factor / tower PC
- **Location:** Server rack - bottom area (Photo 2)
- **Visible specs:** Mesh front; optical drive; front USB; audio jack
- **Observed status:** Powered ON (green power LED)
- **Connectivity:** Likely network + power at rear (not fully visible)
- **Owner notes:** May be monitoring PC, domain helper, or backup host — verify role. Note: Photo 1 shows two ML310e towers; Photo 2 shows this additional HP unit — treat as separate unless confirmed same site inventory overlap.
- **Criticality:** Medium/High
- **Serial / IP:** TBD / TBD
- **Next action:** Confirm whether this is a third compute host or alternate angle of existing gear
- **Photo source:** Photo 2

### RACK-001 — Unknown (standard 19-inch rack) Open/enclosed 19-inch server rack
- **Category:** Infrastructure / Enclosure
- **Form factor:** Floor/wall rack with shelves + rails
- **Location:** ICT room / network closet
- **Visible specs:** Black metal; square-hole rails; numbered U markings; top cooling fans
- **Observed status:** In use
- **Connectivity:** Houses all listed devices; poor cable management observed
- **Owner notes:** Facility asset
- **Criticality:** High (housing)
- **Serial / IP:** TBD / N/A
- **Next action:** Add PDU inventory; improve cable management; label U positions
- **Photo source:** Photo 1 & Photo 2

### CAB-LOT-001 — Various Cat5e/Cat6 patch leads + fiber patch
- **Category:** Cabling / Passive Infrastructure
- **Form factor:** Patch cables (blue, grey/cream, yellow fiber)
- **Location:** Throughout rack front
- **Visible specs:** Ethernet patch density high; 1x yellow fiber to ZOL CPE
- **Observed status:** In use; disorganized
- **Connectivity:** No visible patch-panel labeling in photos
- **Owner notes:** Passive plant — document as lot until port map exists
- **Criticality:** Medium
- **Serial / IP:** N/A / N/A
- **Next action:** Install patch panel; color-code; create port map spreadsheet
- **Photo source:** Photo 1 & Photo 2

## Suggested inventory fields still missing (capture on site)

1. Serial numbers / asset tags for every device  
2. Exact switch model from rear/bottom label  
3. Management IPs (Cyberoam, switch, servers, iLO)  
4. Hostnames, OS versions, roles (AD, file, apps, backup)  
5. RAM / storage / CPU details for servers  
6. PoE budget and port-to-endpoint map for the TRENDnet switch  
7. ISP circuit ID, WAN IP, and ZOL support contact  
8. PDU / UPS inventory (not clearly visible in photos)  
9. Software licenses / firewall subscriptions  
10. Cable port labeling and logical network diagram  

## Risk / ICT notes

- **Cyberoam** platforms are end-of-life; treat FW-001 as a migration priority.  
- **ZOL CPE** is ISP property — inventory as *custodied*, not owned.  
- Cable management is poor; increases troubleshooting time and outage risk.  
- Multiple overlapping routers/APs may indicate undocumented dual-NAT or rogue Wi-Fi — validate topology.  
