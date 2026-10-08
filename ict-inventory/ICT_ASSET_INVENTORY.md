# ICT Asset Inventory

**Site:** Server rack (from site photos)  
**Inventory date:** 2026-10-08  
**Source:** Visual inspection of two rack photographs  
**Status:** Draft v2 — serial numbers, IPs, and some SKUs still require on-site capture  

## Summary counts

| Category | Qty (visible) | Asset IDs |
|---|---|---|
| Tower servers (HP ProLiant) | 2 | SRV-001, SRV-002 |
| Workstation / additional HP host | 1 | PC-001 |
| Firewall / UTM | 1 | FW-001 |
| PoE+ Gigabit switch | 1 | SW-001 |
| MikroTik router | 1 | RTR-002 |
| ISP CPE / wireless gateway (ZOL-owned) | 1 | RTR-001 |
| Unidentified silver appliance | 1 | NET-003 |
| Secondary wireless router/AP (uncertain) | 0–1 | NET-002 |
| Rack enclosure + cooling fans | 1 | RACK-001 |
| Cabling lot (Ethernet + fiber) | 1 | CAB-LOT-001 |

**Active compute/network devices confidently identified:** 8  
**Infrastructure / passive:** 2  

---

## Likely logical topology (inferred)

```text
Internet (ZOL fiber)
        │
        ▼
 [RTR-001] ZOL CPE / ONT+Wi‑Fi  (ISP-owned)
        │ Ethernet
        ▼
 [FW-001] Cyberoam CR 50iNG  ← perimeter firewall/UTM
        │
        ▼
 [SW-001] TRENDnet TPE-TG240g PoE+ 24-port  ← LAN aggregation
   ├── [SRV-001] HP ProLiant ML310e Gen8 v2
   ├── [SRV-002] HP ProLiant ML310e Gen8 v2
   ├── [PC-001]  HP tower/SFF host (Photo 2)
   ├── [RTR-002] MikroTik (hEX S / similar)  ← possible routing/VPN/VLAN helper
   └── [NET-003] Silver appliance (role TBD)
```

> Topology is **inferred from photos only**. Confirm with live config (Cyberoam zones, MikroTik bridges, DHCP scopes) before treating as authoritative.

---

## Device register

### SRV-001 — HP ProLiant ML310e Gen8 v2
| Field | Value |
|---|---|
| Asset ID | SRV-001 |
| Category | Server |
| Manufacturer | HP (Hewlett-Packard) |
| Model | ProLiant ML310e Gen8 v2 |
| Form factor | Tower (shelf-mounted in rack) |
| Location | Upper shelf — left |
| Visible specs | Intel Xeon badge; DVD-RW; 4× front USB; perforated grille |
| Observed status | **ON** — green Power + Health LEDs |
| Connectivity | Front USB cable attached; rear power/network present |
| Ownership | Organization-owned (assumed) |
| Criticality | High |
| Serial / hostname / IP / iLO | TBD |
| Photo | Photo 1 |
| Next action | Capture serial + iLO IP; record OS, CPU/RAM/disk, role (DC/file/app/backup) |

### SRV-002 — HP ProLiant ML310e Gen8 v2
| Field | Value |
|---|---|
| Asset ID | SRV-002 |
| Category | Server |
| Manufacturer | HP (Hewlett-Packard) |
| Model | ProLiant ML310e Gen8 v2 |
| Form factor | Tower (shelf-mounted in rack) |
| Location | Upper shelf — right |
| Visible specs | Same as SRV-001 (identical twin) |
| Observed status | **ON** — green Power + Health LEDs |
| Connectivity | Rear cabling visible; no front USB in use |
| Ownership | Organization-owned (assumed) |
| Criticality | High |
| Serial / hostname / IP / iLO | TBD |
| Photo | Photo 1 |
| Next action | Same as SRV-001; document HA/cluster or distinct role vs twin |

### FW-001 — Cyberoam CR 50iNG
| Field | Value |
|---|---|
| Asset ID | FW-001 |
| Category | Firewall / UTM |
| Manufacturer | Cyberoam (Sophos lineage) |
| Model | CR 50iNG (NG Series “Future Ready”) |
| Form factor | 1U rack-mount |
| Location | Mid rack, below servers |
| Visible specs | Console RJ45; USB; 8× copper GbE (ports A–H / 1–8); PWR/SYS LEDs |
| Observed status | **ON** — Power LED lit; ports in use (Photo 2: A/B cabled) |
| Connectivity | Upstream/downstream Ethernet to ISP path and LAN switch |
| Ownership | Organization-owned (assumed) |
| Criticality | **Critical** |
| Serial / mgmt IP / firmware | TBD |
| Photo | Photo 1 & 2 |
| Next action | Export config; note firmware & license; **plan EOL replacement** (Cyberoam is end-of-life) |

### SW-001 — TRENDnet TPE-TG240g (PoE+ Gigabit)
| Field | Value |
|---|---|
| Asset ID | SW-001 |
| Category | Network switch |
| Manufacturer | TRENDnet |
| Model | **TPE-TG240g** (24-Port Gigabit PoE+) — model text consistent with Photo 2 |
| Form factor | 1U rack-mount |
| Location | Directly below Cyberoam |
| Visible specs | 24× RJ45; Link/Act + PoE LED grid; many ports occupied |
| Observed status | **ON** — numerous green/amber LEDs active |
| Connectivity | Dense blue/grey Cat5e/Cat6 patching — primary LAN aggregation |
| Ownership | Organization-owned (assumed) |
| Criticality | **Critical** |
| Serial / mgmt IP / PoE budget | TBD (confirm if unmanaged vs web-smart) |
| Photo | Photo 1 & 2 |
| Next action | Confirm SKU on rear label; build port-to-device map; note PoE draw |

### RTR-002 — MikroTik router (likely hEX S / RB760iGS class)
| Field | Value |
|---|---|
| Asset ID | RTR-002 |
| Category | Router / L3 appliance |
| Manufacturer | **MikroTik** |
| Model | Likely **hEX S (RB760iGS)** or similar — white chassis, 5× RJ45 + 1× SFP + console |
| Form factor | Desktop / shelf |
| Location | Shelf below TRENDnet switch (Photo 1) |
| Visible specs | 5× Ethernet; SFP cage; console; blue link LED |
| Observed status | Appears **powered** |
| Connectivity | Blue Ethernet connected; possible fiber via SFP (verify) |
| Ownership | Organization-owned (assumed) |
| Criticality | Medium–High (depends on role: VPN, VLAN, failover, hotspot) |
| Serial / identity / IP | TBD — read RouterOS identity |
| Photo | Photo 1 |
| Next action | Confirm exact board name (`/system routerboard print`); document bridges/NAT |

### RTR-001 — ZOL ISP CPE (ONT / wireless gateway)
| Field | Value |
|---|---|
| Asset ID | RTR-001 |
| Category | ISP modem / ONT / wireless gateway |
| Manufacturer | ZOL-provided CPE (Liquid / ZOL Zimbabwe) |
| Model | Exact consumer model not readable |
| Form factor | Desktop white gateway, 2 external antennas |
| Location | Lower shelf |
| Visible specs | “PROPERTY OF ZOL” + orange “DO NOT REMOVE”; perforated top |
| Observed status | In service |
| Connectivity | **Yellow fiber** patch (Photo 2) + Ethernet toward LAN/firewall |
| Ownership | **ISP-owned (custodied)** — not company property |
| Criticality | **Critical** (internet edge) |
| Circuit ID / WAN IP | TBD from ZOL |
| Photo | Photo 1 & 2 |
| Next action | Record circuit ID, WAN IP, support contacts; keep ownership tagged as ISP |

### NET-003 — Silver network appliance (unidentified)
| Field | Value |
|---|---|
| Asset ID | NET-003 |
| Category | Network appliance / mini router / controller |
| Manufacturer | Unknown |
| Model | TBD |
| Form factor | Silver desktop chassis |
| Location | Lower shelf beside ZOL CPE (Photo 2) |
| Visible specs | Multiple Ethernet in use; USB ports; status LEDs; antennas nearby |
| Observed status | **ON** |
| Connectivity | Blue Ethernet cables attached |
| Ownership | TBD |
| Criticality | Medium |
| Serial / IP | TBD |
| Photo | Photo 2 |
| Next action | Clear photo of front/rear labels; determine function |

### NET-002 — Secondary wireless router/AP (uncertain / may be same as NET-003 clutter)
| Field | Value |
|---|---|
| Asset ID | NET-002 |
| Category | Wireless router / AP (tentative) |
| Manufacturer | Unknown (white plastic; possible TP-Link-class) |
| Model | TBD |
| Form factor | Desktop Wi‑Fi device |
| Location | Mid/lower rack among cable bundle |
| Visible specs | White body; external antennas; Ethernet connected |
| Observed status | Appears cabled |
| Ownership | TBD |
| Criticality | Medium — may be redundant Wi‑Fi |
| Photo | Photo 1 (partial) |
| Next action | Confirm whether distinct from ZOL CPE / NET-003; remove if unused |

### PC-001 — HP tower / SFF host
| Field | Value |
|---|---|
| Asset ID | PC-001 |
| Category | Workstation / small server |
| Manufacturer | HP |
| Model | Exact model not readable (mesh-front tower/SFF) |
| Form factor | Tower / SFF in rack base (Photo 2) |
| Location | Bottom of rack |
| Visible specs | Optical drive; front USB; audio; green power LED; HP logo |
| Observed status | **ON** |
| Ownership | Organization-owned (assumed) |
| Criticality | Medium–High |
| Note | Photo 1 shows two ML310e towers on top; Photo 2 shows this lower HP unit — inventory as **separate** until site visit confirms otherwise |
| Photo | Photo 2 |
| Next action | Read model/serial sticker; record OS and role |

### RACK-001 — 19-inch equipment rack
| Field | Value |
|---|---|
| Asset ID | RACK-001 |
| Category | Enclosure / facility |
| Manufacturer | Unknown |
| Model | Standard 19" rack (open/enclosed) with shelves + rails |
| Visible specs | Black metal; numbered U rails; **two top cooling fans** |
| Status | In use |
| Criticality | High (housing) |
| Next action | Inventory PDU/UPS (not clearly visible); label U positions; cable management |

### CAB-LOT-001 — Patch cabling lot
| Field | Value |
|---|---|
| Asset ID | CAB-LOT-001 |
| Category | Passive infrastructure |
| Contents | Cat5e/Cat6 patch leads (blue, grey/cream) + yellow fiber to ZOL CPE |
| Status | In use — disorganized (“cable spaghetti”) |
| Criticality | Medium |
| Next action | Patch panel + port map; color-code; dress cables |

---

## Ownership summary

| Ownership | Assets |
|---|---|
| Organization (assumed) | SRV-001, SRV-002, FW-001, SW-001, RTR-002, PC-001, RACK-001, CAB-LOT-001, NET-002/003 (pending) |
| ISP (ZOL) — custodied only | RTR-001 |

---

## Risks & recommendations

1. **Cyberoam EOL** — FW-001 should be on a replacement roadmap (Sophos or alternative NGFW).  
2. **ISP CPE ownership** — do not dispose/relabel RTR-001; keep “PROPERTY OF ZOL” intact.  
3. **Cable hygiene** — high fault/troubleshooting risk; schedule dress-and-label day.  
4. **Duplicate edge devices** — MikroTik + Cyberoam + ZOL Wi‑Fi may mean double NAT; document the real default gateway for LAN clients.  
5. **Aging servers** — ML310e Gen8 v2 are older Xeon towers; plan refresh / backup verification.  
6. **Missing power protection** — no clear UPS/PDU in photos; add to inventory urgently if present off-camera.

---

## Related files

- `ict_asset_inventory.csv` — machine-readable register  
- `on_site_capture_sheet.csv` — blank fields to fill during physical audit  
- `photo1_rack_overview.jpg` / `photo2_rack_network_gear.jpg` — source photos  
