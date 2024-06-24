Criar 4 mauqinas na AWS
. Windows 11
. Windows Server 2016
. Ubuntu
. Parrot

Entra no Ubuntu pelo terminus e instalar o ambiente grafico com os seguintes comandos:
"sudo apt update
sudo apt upgrade
sudo apt install -y xfce4 xfce4-goodies
sudo apt install -y xrdp chromium-browser filezilla
sudo adduser xrdp ssl-cert
sudo adduser [user]
login [user]
echo xfce4-session > ~/.xsession"

Entrar por rdp nas maquinas de Win11, WinServ e Ubuntu e por SSH no Parrot e Ubuntu também.

No ubuntu fazer
"git clone https://github.com/SpiderLabs/Responder"


