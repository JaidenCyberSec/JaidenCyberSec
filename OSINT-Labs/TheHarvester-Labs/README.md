# 🕵️ OSINT – TheHarvester Labs  

This folder contains a series of hands-on **TheHarvester OSINT labs** designed to practice and master Open Source Intelligence collection using **Kali Linux**, Python, and data visualization tools.  

Each lab demonstrates collecting **emails**, **subdomains**, and building **network graphs** to analyze an organization's public footprint.

---

## 🎯 Objectives
- Learn to use **TheHarvester** effectively with multiple search engines.  
- Collect and structure OSINT data in **JSON and CSV formats**.  
- Visualize relationships between emails and subdomains using **Python, NetworkX, and Matplotlib**.  
- Document workflow and maintain **reproducible lab reports**.  

---

## 🧰 Tools Used
- 🐧 Kali Linux  
- 🔍 TheHarvester  
- 📜 Python 3  
- 📊 Pandas (CSV parsing)  
- 🌐 NetworkX + Matplotlib (network visualization)  

---

## 📂 Labs Overview

| Lab # | Target | Description | Status |
|-------|--------|-------------|--------|
| Lab 1 | Tesla.com | Collected emails & subdomains, parsed JSON → CSV, built network graph | ✅ Complete |
| Lab 2 | [Add Target] | [Short description] | ⬜ In Progress |
| Lab 3 | [Add Target] | [Short description] | ⬜ Planned |
| …     | …      | …           | …      |

> Each lab has its own **subfolder** containing all scripts, CSV/JSON outputs, network graph PNGs, and a lab-specific README.md.  

---

## 📖 Lab Workflow (Generic)
1. **Run TheHarvester:**  
   ```bash
   theHarvester -d <target-domain> -b <source> -f <output.json>

