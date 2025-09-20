

````markdown
# Lab 1 – Tesla – TheHarvester OSINT

This lab demonstrates practical **OSINT collection** using **TheHarvester** on Tesla.com.  
The goal is to collect emails, subdomains, and visualize the network relationships of publicly available assets.

---

## 🎯 Objectives
- Learn to use **TheHarvester** effectively across multiple sources.  
- Collect and parse OSINT data into **JSON and CSV**.  
- Generate **network graphs** of emails and subdomains using Python and NetworkX.  
- Document a complete OSINT workflow for professional presentation.

---

## 🧰 Tools & Technologies
- 🐧 Kali Linux  
- 🔍 TheHarvester  
- 📜 Python 3  
- 📊 Pandas (CSV/JSON parsing)  
- 🌐 NetworkX & Matplotlib (network graph visualization)  

---

## 📝 Lab Workflow

### Step 1: Run TheHarvester
Collect emails and subdomains from Tesla.com using multiple search engines:

```bash
theHarvester -d tesla.com -b google -f tesla_results.json
````

* `-d tesla.com` → target domain
* `-b google` → search engine
* `-f tesla_results.json` → output file

> You can repeat with other sources (Bing, Yahoo, etc.) for more comprehensive results.

---

### Step 2: Parse JSON → CSV

Use Python to extract emails and subdomains from `tesla_results.json`:

```python
import json
import pandas as pd

with open('tesla_results.json') as f:
    data = json.load(f)

emails = data.get('emails', [])
subdomains = data.get('subdomains', [])

df = pd.DataFrame({
    'Emails': emails,
    'Subdomains': subdomains
})

df.to_csv('tesla_harvester.csv', index=False)
```

> Output: `tesla_harvester.csv` with all emails and subdomains.

---

### Step 3: Build Network Graph

Visualize relationships between emails and subdomains using Python:

```python
import pandas as pd
import networkx as nx
import matplotlib.pyplot as plt

df = pd.read_csv('tesla_harvester.csv')

G = nx.Graph()

# Add nodes
for email in df['Emails']:
    G.add_node(email, type='email')

for subdomain in df['Subdomains']:
    G.add_node(subdomain, type='subdomain')

# Connect emails to subdomains
for email in df['Emails']:
    for subdomain in df['Subdomains']:
        G.add_edge(email, subdomain)

# Draw network graph
plt.figure(figsize=(12,12))
nx.draw(G, with_labels=True, node_size=2000, node_color='skyblue', font_size=10)
plt.savefig('tesla_network_graph.png')
plt.show()
```

> Output: `tesla_network_graph.png` showing connections between emails and subdomains.

---

## 📂 Folder Structure

```
Lab1-Tesla-TheHarvester/
├── README.md
├── tesla_results.json
├── tesla_harvester.csv
├── parse_tesla_harvester.py
├── tesla_network_graph.py
└── tesla_network_graph.png
```

---

## 🧠 Lessons Learned

* Mastered **TheHarvester** for multiple search engines.
* Learned **JSON → CSV parsing** in Python for OSINT automation.
* Created **network visualizations** to map relationships between emails and subdomains.
* Practiced **professional lab documentation** for GitHub portfolios.

---

## 📌 Notes

* All scripts are **commented and reusable**.
* Ensure to run the lab in **Kali Linux** for best compatibility.
* This lab is **ethical and educational**, using only publicly available information.

---

© 2025 Jaiden Jimerson. All rights reserved.

```

---

✅ This README.md is **ready to paste** into your `Lab1-Tesla-TheHarvester` folder.  
- It documents the **full workflow**.  
- Links all scripts and outputs.  
- Professional and GitHub-ready.  

---



