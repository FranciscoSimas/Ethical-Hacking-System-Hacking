### Ethical Hacking: Web Application Reconnaissance

This project demonstrates various techniques for web application reconnaissance, including whois, nmap, telnet, whatweb, and clickjacking vulnerability tests. Below are the steps and the results of using these tools, providing a basic and straightforward explanation of each.

---

#### 1. WHOIS Lookup

**Command:**
```sh
whois 54.235.172.57
```

**Description:**
WHOIS lookup provides information about the registered owner of an IP address or domain name. 

**Result:**
![WHOIS Result](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/4147183e-1fc0-492a-a568-2841abe9c7f1)

---

#### 2. Nmap Scan

**Command:**
```sh
nmap -T4 -A -v www.simasgame.cloudns.ch
```

**Description:**
Nmap is a network scanning tool that identifies open ports, services, and potential vulnerabilities on the target host.

**Port Scan Result:**
![Nmap Port Scan Result](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/d8ae0c0f-949d-4904-ac56-fcfecbb6fbed)

**Detailed Information:**
![Nmap Detailed Info](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/8e4cb303-a002-40f3-b202-6c000eacd90a)

---

#### 3. Telnet Banner Grabbing

**Command:**
```sh
telnet www.simasgame.cloudns.ch 80
GET / HTTP/1.0
```

**Description:**
Telnet is used to connect to remote servers. Banner grabbing reveals the server software and version.

**Result:**
![Telnet Result](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/7f61b95b-f3cc-4787-add8-4a046f60585e)

**Server Information:**
```plaintext
Microsoft-HTTPAPI/2.0
```

---

#### 4. WhatWeb Analysis

**Command:**
```sh
whatweb -v www.simasgame.cloudns.ch
```

**Description:**
WhatWeb identifies websites' technologies, including server information, plugins, and other metadata.

**Result:**
![WhatWeb Result](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/4345c146-4f00-426f-b5dd-0a2612b87208)

**Logging:**
```sh
whatweb --log-verbose=SimasGame_Report www.simasgame.cloudns.ch
```

---

#### 5. Clickjacking Vulnerability Test

**HTML Code:**
```html
<html>
<head>
<title>Clickjack Vulnerability Test</title>
</head>
<body>
<p>Website is vulnerable to clickjacking!</p>
<iframe src="https://www.simasgame.cloudns.ch" width="1920" height="1080"></iframe>
</body>
</html>
```

**Description:**
This HTML code checks if a website is vulnerable to clickjacking by embedding it in an iframe. If the message appears, the site is vulnerable.

**Result:**
![Clickjacking Test Result](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/32549023-5680-4b2e-b0dd-15170b3354be)

---

### Conclusion

In real-world scenarios, hackers can use this information to find and exploit vulnerabilities. This guide covers the reconnaissance stage using tools like WHOIS, DNS interrogation, port and services discovery, banner grabbing, and firewall detection. Below are the results for each command used, illustrating what information they reveal.



