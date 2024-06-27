1- Web application reconnaissance

whois 54.235.172.57
![Captura de ecrã 2024-06-27 201419](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/4147183e-1fc0-492a-a568-2841abe9c7f1)

---
---

nmap -T4 -A -v www.simasgame.cloudns.ch

portas
![Captura de ecrã 2024-06-27 195225](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/d8ae0c0f-949d-4904-ac56-fcfecbb6fbed)

---
---

MAC, DNS name, NetBIOS, OS, SSL cert
![Captura de ecrã 2024-06-27 195558](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/8e4cb303-a002-40f3-b202-6c000eacd90a)

---
---

telnet www.simasgame.cloudns.ch 80
GET / HTTP/1.0
![Captura de ecrã 2024-06-27 200041](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/7f61b95b-f3cc-4787-add8-4a046f60585e)

Dá para ver o server que tá usando no caso é Microsoft-HTTPAPI/2.0

---
---

também tem esse comando do whatweb, dá para ver, ip, plugin information e http header information
whatweb -v www.simasgame.cloudns.ch
![Captura de ecrã 2024-06-27 201728](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/4345c146-4f00-426f-b5dd-0a2612b87208)

whatweb --log-verbose=SimasGmae_Report www.simasgame.cloudns.ch - esse comando cria um .txt com o report agora visto.

ainda podemos verificar se o site está vulneravel a Clickjacking com o seguinte html

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

executando o ficheiro html... se aparecer a mensagem em cima quer dizer que está vulneravel.

![Captura de ecrã 2024-06-27 221453](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/32549023-5680-4b2e-b0dd-15170b3354be)



em situações reais hackers podem usar essas informações para encontrar vulnerabilities e dar exploit nelas depois

Por aqui acaba a etapa de reconnaissance usando o Whois, DNS interrogation, port and services discovery, banner grabing and firewall detection.

