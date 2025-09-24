

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

> Repeat with other sources (Bing, Yahoo, etc.) for more comprehensive results.

---

### Step 2: Parse JSON → CSV

Use Python to extract emails and subdomains from `tesla_results.json`:

```python
import json
import pandas as pd

# Load JSON data
with open("tesla_results.json") as f:
    data = json.load(f)

# Extract emails and subdomains
if isinstance(data, dict):
    emails = data.get("emails", [])
    subdomains = data.get("hosts", [])
elif isinstance(data, list):
    emails = data
    subdomains = []
else:
    emails, subdomains = [], []

# Ensure lists are equal length
max_len = max(len(emails), len(subdomains))
emails += [None]*(max_len - len(emails))
subdomains += [None]*(max_len - len(subdomains))

# Save to CSV
df = pd.DataFrame({"Emails": emails, "Subdomains": subdomains})
df.to_csv("tesla_harvester.csv", index=False)
print(f"Saved {len(emails)} emails and {len(subdomains)} subdomains to tesla_harvester.csv")
```

> Output: `tesla_harvester.csv` with all emails and subdomains.

---

### Step 3: Build Network Graph

Visualize relationships between emails and subdomains using Python:

```python
import pandas as pd
import networkx as nx
import matplotlib.pyplot as plt

# Load CSV
df = pd.read_csv("tesla_harvester.csv")

emails = df['Emails'].dropna().tolist()
subs = df['Subdomains'].dropna().tolist()

# Create graph
G = nx.Graph()

# Add nodes
for email in emails:
    G.add_node(email, type='email')
for sub in subs:
    G.add_node(sub, type='subdomain')

# Connect each email to each subdomain
for email in emails:
    for sub in subs:
        G.add_edge(email, sub)

# Draw graph
plt.figure(figsize=(14,10))
pos = nx.spring_layout(G, k=0.5)
nx.draw(
    G, pos, with_labels=True, 
    node_size=800, 
    node_color='lightblue', 
    font_size=8, 
    edge_color="gray"
)
plt.title("Tesla OSINT: Email ↔ Subdomain Network", fontsize=14)
plt.savefig("tesla_network_graph.png", dpi=300)
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

* Mastered **TheHarvester** across multiple search engines.
* Learned **JSON → CSV parsing** in Python for OSINT automation.
* Created **network visualizations** to map relationships between emails and subdomains.
* Practiced **professional lab documentation** for GitHub portfolios.

---

## 📌 Notes

* All scripts are **commented and reusable**.
* Run the lab in **Kali Linux** for best compatibility.
* This lab is **ethical and educational**, using only publicly available information.

---

© 2025 Jaiden Jimerson. All rights reserved.

```

```





