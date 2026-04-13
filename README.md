

<p align="center">
  <img src="https://raw.githubusercontent.com/TEAMBCS/Fire-Eye/main/Image/fire-eye-logo.png" width="380" alt="FIRE-EYE Logo">
</p>

<h1 align="center">🔥 FIRE-EYE 🔥</h1>
<p align="center">
  A next-generation Firewall, CDN & WAF Fingerprinting Framework for Security Researchers, Bug Hunters, and Penetration Testers.
  <br><br>
  Built with ❤️ by <b>BLACK ZERO </b>
</p>
<p align="center">
  🚀 Powered by <b> BANGLADESH CYBER SQUAD and TEAM SHADOW STRIKER </b><br>
  📆 Year: 2025
</p>

---

<h1 align="center"> Over View </h1>

**FIRE-EYE** (`fire-eye.py`) is a Python3-based advanced security analysis framework that detects and fingerprints **Web Application Firewalls (WAFs)**, **CDNs**, **Load Balancers**, and related security layers.

It provides flexible control through user-supplied signatures, regex header matching, and custom request headers — making it suitable for professional pentesters, SOC analysts, and researchers.

---


<h1 align="center"> Core Features </h1>

* 🔍 **WAF / CDN / Load Balancer Detection**
* 🧩 **User-Supplied Signature Merging** (`--user-list`, `--user-vendors-list`)
* 🔎 **Regex Header/Cookie/Body Matching** (`--header-search`)
* ⚙️ **Custom HTTP Headers** (`--headers`)
* 🧠 **Smart User-Agent Rotation** (disable with `--no-rotate-ua`)
* 📦 **Automatic Report Generation (.txt / .md)**
* 💡 **Proxy and JSON Output Support**

---


<h1 align="center"> Command-Line Usage</h1>

```bash 
python3 fire-eye.py <target> [options]
```

### Example Options:

| Option                          | Description                                              |
| ------------------------------- | -------------------------------------------------------- |
| `target`                        | Target domain or URL (e.g., `https://example.com`)       |
| `--headers "Key:Val;Key2:Val2"` | Send custom request headers                              |
| `--header-search "<regex>"`     | Search for evidence in headers, cookies, or body         |
| `--user-list <file>`            | Custom WAF/CDN/token signature list (JSON/simple format) |
| `--user-vendors-list <file>`    | Custom vendor list to merge with default                 |
| `--proxy <file>`                | File containing proxies (HTTP/SOCKS)                     |
| `--show-headers`                | Displays raw HTTP headers via `curl`                     |
| `--no-rotate-ua`                | Disable User-Agent rotation                              |
| `--report <path>`               | Save the output report to a custom file                  |
| `--json`                        | Output in JSON format                                    |
| `--debug`                       | Enable debug logging                                     |

---


<h1 align="center"> Installation</h1>

### 📲 Termux / Linux

```bash
pkg update && pkg install python3 git curl -y
git clone https://github.com/TEAMBCS/Fire-Eye.git
cd Fire-Eye
chmod +x *
pip3 install -r requirements.txt
python3 fire-eye.py -h
```

After installation, simply run:

```bash
python3 fire-eye.py --help
```
### Another Way to install

```bash
pip install fire-eye-main
fire-eye -h
```


---

<h1 align="center"> JSON Formet Examples </h1>
### 1️⃣ **user-list.json**

```json
{
  "MyCustomWAF": {
    "manufacturer": "MyCompany",
    "type": "WAF",
    "headers": ["x-mycompany-id", "mycompany-waf"],
    "cookies": ["MYCOMP_SESSION"],
    "body": ["Access denied by MyCompany WAF"],
    "server": ["mycompany"]
  }
}
```

### 2️⃣ **user-vendors-list.json**

```json
{
  "vendors": [
    "Cloudflare",
    "Akamai",
    "Fastly",
    "AWS CloudFront",
    "Imperva"
  ]
}
```

---

## 🔧 How `--headers` and `--header-search` Work

* **`--headers`**
  Format: `"Key:Val;Key2:Val2"`
  Example:

  ```bash
  --headers "User-Agent:Mozilla/5.0;Referer:https://google.com;Accept:*/*"
  ```

  ➤ The tool parses and attaches these headers to all requests.

* **`--header-search`**
  Searches inside headers, cookies, and response body for specific patterns using regex.
  Example:

  ```bash
  --header-search "(?i)cf-ray|x-amz-cf-id|incap_ses"
  ```

  ➤ Matches are displayed and logged in the report.

---


<h1 align="center"> Usage Examples </h1>


### 1️⃣ Basic Scan

```bash
python3 fire-eye.py https://example.com
```

### 2️⃣ With Custom Headers and Regex Search

```bash
python3 fire-eye.py https://example.com \
  --headers "User-Agent:MyCustomAgent;Referer:https://google.com" \
  --header-search "(?i)cf-ray|x-amz-cf-id|fastly"
```

### 3️⃣ With Custom Signature Lists

```bash
python3 fire-eye.py https://target.com \
  --user-list user-list.json \
  --user-vendors-list user-vendors-list.json
```

### 4️⃣ With Proxy Support

```bash
python3 fire-eye.py https://example.com --proxy proxy.txt --debug
```

### 5️⃣ JSON Output Mode

```bash
python3 fire-eye.py https://example.com --json > result.json
```
### 6️⃣ REPORT Save Mode
```bash
python3 fire-eye.py https://example.com --report fire-eye.txt
```
---



<h1 align="center"> Sample Output pic </h1>



<p align="center">
  <img src="https://raw.githubusercontent.com/TEAMBCS/Fire-Eye/main/Image/fire-eye-img.jpg" alt="pic" width="800"/>
  &nbsp;&nbsp;&nbsp;
</p>

## ⚙️ Auto Report Save as :
```
example_com_fireeye_<timestamp>.txt
```

---

## 🧰 Dependencies

| Library    | Purpose                |
| ---------- | ---------------------- |
| `requests` | HTTP requests          |
| `rich`     | Console styling        |
| `pyfiglet` | ASCII banners          |
| `colorama` | Terminal color support |

Install manually:

```bash
pip install requests rich pyfiglet colorama
```

---

## ⚠️ Disclaimer

This tool is **for educational and authorized security testing only.**
Do **not** use it against any system or domain without proper permission.

Unauthorized scanning may violate laws or regulations.

---

## 👨‍💻 Author

* **Adi Barua (ADIRTTA)** — *BLACK ZERO*
* 🌐 GitHub: [github.com/TEAM-BCS](https://github.com/TEAM-BCS)
* 📱 Facebook: [facebook.com/BANGLADESH-CYBER-SQUAD](https://facebook.com/groups/572787103428508/)
* ⚡ Team: **TEAM BCS**

---

## 📜 License

**MIT License**
Use responsibly and only for ethical security research.

---

