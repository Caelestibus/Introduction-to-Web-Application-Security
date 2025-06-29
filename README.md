### Introduction-to-Web-Application-Security

### 🛡️ Task 2: Introduction to Web Application Security

**Cyber Security Internship @ Redynox**  
*Focus: Identify and exploit basic web vulnerabilities using OWASP ZAP and WebGoat*

---

### 📌 Objective

The learning objective of this task is centered around web application vulnerabilities (SQL Injection, XSS, CSRF) by scanning and analyzing an intentionally vulnerable application. I am focused on learning each attack, how to spot them, how to initiate them and how to easily document the outcome

---

#### 🧰 Tools I imployed in the process includes;

- [WebGoat](https://owasp.org/www-project-webgoat/) - Vulnerable web app

- [OWASP ZAP](https://www.zaproxy.org/) - Security scanner

- Python HTTP Server (optional)

- Kali Linux (or any Linux-based testing environment)

---

#### 🧱 These are the steps I followed 

#### 1. This is mainly to clone webgoat from a github repository

```bash
git clone https://github.com/WebGoat/WebGoat.git
cd WebGoat
```

📌 I accessed WebGoat using firefox, as webgoat is a vulnerable website and also a learning platform for website vulnerability tests:

```bash
http://localhost:8080/WebGoat
```

I ran this command on my terminal, as I wasn't able to access the url until I start the server

```
java -jar webgoat-server-8.2.0.jar
```

Upon accessing webgoat on firefox, I had to create my login, the option was provided

```
username: getdavid1
password: 123456789

```

---

#### 2. I also Installed OWASP ZAP, as I used it to intercept and analyze traffic between the browser and WebGoat, helping identify security flaws. It also performed automated scans to detect vulnerabilities like SQL Injection, XSS, and CSRF. Including running attacks


```bash
sudo apt install zaproxy
```


---


#### 3. The following are the vulnerability analysis I performed


 _Configure ZAP to Intercept Traffic_

- I opened ZAP GUI by running the command on my terminal

```bash
zaproxy
```

- I went to Tools > Options > Local Proxies

- I made sure ZAP is listening on localhost:8080 or 127.0.0.1:8080

- I set my firefox proxy to match this (localhost:8080)


---


_Passive Scan with ZAP_

- I had to browse through WebGoat challenges to generate traffic and also learnt from the challenges

- I used ZAP to passively record and analyze the requests

- View alerts under Alerts Tab (left-hand panel)

---


_Active Scan_

- I right-clicked on  http://localhost:8080/WebGoat in the Sites tree

- Selected Attack > Active Scan

- Waited for scan to complete

---


_I generated a report_

---

#### 🧨 Found Vulnerabilities

_SQL Injection_

- Where:
WebGoat → Injection Flaws → SQL Injection (Advanced)

- What Happened:
ZAP detected a vulnerable input. Typing ' OR '1'='1 in the login form bypassed authentication and showed all users.

- Fix:
Use prepared statements (parameterized queries) and sanitize inputs.

---


_Cross-Site Scripting (XSS)_

- Where:
WebGoat → Cross-Site Scripting (XSS) → Stored XSS

- What Happened:
ZAP found a field storing user input without filtering. Typing <script>alert(1)</script> showed a popup — proof of XSS.

- Fix:
Escape HTML output, apply input validation, and use a Content Security Policy (CSP).

---

