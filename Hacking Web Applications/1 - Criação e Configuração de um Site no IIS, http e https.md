### Documentação para Criação e Configuração de um Site no IIS

## Introdução

Configurar um site no IIS envolve abrir portas no firewall, criar e configurar o site no IIS, ajustar registros DNS e configurar HTTPS. Aqui estão os passos detalhados e suas explicações resumidas para configurar um site acessível via HTTP e HTTPS usando o domínio `simasgame.cloudns.ch`.

## 1. Abrir as Portas 80 e 443 no Firewall do Windows

1. O firewall do Windows pode bloquear tráfego não autorizado para garantir a segurança do sistema.
2. Para permitir que os visitantes acessem o site via HTTP (porta 80), é necessário abrir essa porta no firewall.
3. HTTPS utiliza a porta 443 para comunicações seguras e criptografadas.
4. Assim como a porta 80, a porta 443 também precisa ser aberta no firewall para permitir o tráfego seguro.

### 1.1. Abrindo a Porta 80 e 443

1. Pressione `Win + R`, digite `wf.msc` e pressione Enter.
2. Clique em **Regras de Entrada** no painel esquerdo.
3. Clique em **Nova Regra** no painel direito.
4. Selecione **Porta** e clique em **Avançar**.
5. Selecione **TCP** e, em **Portas locais específicas**, digite `80, 443`. Clique em **Avançar**.
6. Selecione **Permitir a conexão** e clique em **Avançar**.
7. Marque todas as opções (Domínio, Privada, Pública) e clique em **Avançar**.
8. Nomeie a regra como `Abertura da Porta 80 e 443` e clique em **Concluir**.

![image](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/73f69e44-53da-42c7-bade-447f0f4532e3)

## 2. Instalar o IIS e Configurar o Site

1. IIS é o servidor web da Microsoft utilizado para hospedar sites e aplicações web.
2. A instalação do IIS prepara o servidor para hospedar sites, fornecendo uma interface de gerenciamento para configuração e manutenção.
3. O IIS vem com um site padrão que pode ser modificado para hospedar seu conteúdo.
4. Substituir os arquivos na pasta raiz do site (`C:\inetpub\wwwroot`) permite que o IIS sirva seu próprio site quando acessado.

### 2.1. Instalar o IIS (caso não esteja instalado)

1. Abra o **Server Manager**.
2. Clique em **Gerenciar** e selecione **Adicionar Funções e Recursos**.
3. No assistente, clique em **Avançar** até **Seleção de Funções**.
4. Marque **Serviço de Informações da Internet (IIS)**.
5. Clique em **Avançar** e depois em **Instalar**.

### 2.2. Modificar o Default Web Site

1. Abra o **Gerenciador do IIS** (Win + R, digite `inetmgr`).
2. Expanda o nome do servidor e depois **Sites**.
3. Clique em **Default Web Site**.
4. No painel **Ações**, clique em **Explorar** para abrir a pasta raiz do site (`C:\inetpub\wwwroot`).
5. Substitua o arquivo `index.html`.

![image](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/38146e41-8250-4967-8715-267661f6f17b)

## 3. Configurar o DNS no Server Manager

1. O DNS (Domain Name System) traduz nomes de domínio em endereços IP, permitindo que os navegadores localizem seu servidor.
2. Criar uma zona de pesquisa direta no servidor DNS do Windows permite gerenciar os registros DNS para seu domínio.
3. A configuração da zona é essencial para que o domínio `simasgame.cloudns.ch` seja resolvido para o endereço IP do seu servidor.

### 3.1. Criar uma Zona de Pesquisa Direta

1. Abra o **Gerenciador de DNS** (Server Manager > Ferramentas > DNS).
2. Expanda o servidor DNS e clique com o botão direito em **Zonas de Pesquisa Direta**.
3. Selecione **Nova Zona**.
4. No assistente, clique em **Avançar**.
5. Selecione **Zona Primária** e clique em **Avançar**.
6. Digite o nome da zona (ex: `simasgame.cloudns.ch`) e clique em **Avançar**.
7. Mantenha as configurações padrão para o arquivo de zona e clique em **Avançar**.
8. Escolha **Não permitir atualizações dinâmicas** e clique em **Avançar**.
9. Clique em **Concluir**.

### 3.2. Adicionar Registros DNS

1. Clique com o botão direito na zona criada e selecione **Novo Host (A ou AAAA)**.
2. Em **Nome**, deixe em branco para o domínio raiz e crie outro e digite `www` para subdomínio.
3. Em **Endereço IP**, insira o endereço IP público do seu servidor web.
4. Clique em **Adicionar Host**.

![image](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/aadfa382-c0bc-4166-916e-20f048237218)

## 4. Configurar o CloudDNS

1. CloudDNS é um serviço que permite gerenciar DNS de forma eficiente, flexível e grátis.
2. Configurar registros DNS no CloudDNS complementa a configuração do servidor DNS local.
3. Essa configuração garante que o domínio `simasgame.cloudns.ch` seja resolvido corretamente a partir de qualquer local na Internet.

### 4.1. Configurar o hostnames de DNS no CloudDNS

1. Acesse [CloudDNS](https://www.cloudns.net/) e faça login.
2. No painel, clique em **DNS Zones**.
3. Selecione a zona `simasgame.cloudns.ch`.
4. Adicione registros DNS:
   - **Tipo**: `A`
   - **Nome**: deixe em branco para o domínio raiz e outro com `www` para subdomínio.
   - **Endereço**: insira o endereço IP público do seu servidor web.
5. Clique em **Salvar**.

![image](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/b65e890b-582c-4990-9e47-e36565c47e62)

## 5. Configurar Bindings no IIS para HTTP

1. Bindings no IIS determinam como o servidor responde a solicitações de diferentes endereços, portas e protocolos.
2. Configurar um binding HTTP para o domínio assegura que o IIS atenda solicitações HTTP na porta 80.
3. Este passo é essencial para que o site esteja acessível via HTTP usando o domínio configurado.

### 5.1. Adicionar o Bindings ao site

1. Abra o **Gerenciador do IIS**.
2. No painel **Conexões**, clique em **Default Web Site**.
3. No painel **Ações**, clique em **Bindings**.
4. Clique em **Add**.
5. Em **Type**, selecione `http`.
6. Em **IP address**, selecione `All Unassigned`.
7. Em **Port**, insira `80`.
8. Em **Hostname**, insira `simasgame.cloudns.ch` e outro `www.simasgame.cloudns.ch`.
9. Clique em **OK**.

![image](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/4f8b883f-5c65-4b75-b8c4-53a7d7d9b456)

## 6. Instalar PHP e Configurar no IIS

1. Para executar scripts PHP no IIS, é necessário instalar o PHP e configurá-lo corretamente.

### 6.1. Instalar PHP

1. Baixe a versão mais recente do PHP [aqui](https://windows.php.net/download/).
2. Extraia os arquivos para `C:\php`.

### 6.2. Adicionar PHP ao PATH

1. Abra as **Configurações do Sistema** (Win + Pause/Break).
2. Clique em **Configurações Avançadas do Sistema**.
3. Clique em **Variáveis de Ambiente**.
4. Em **Variáveis do Sistema**, selecione `Path` e clique em **Editar**.
5. Adicione `C:\php` ao final da lista e clique em **OK**.

### 6.3. Instalar CGI no Server Manager

1. Abra o **Server Manager**.
2. Clique em **Gerenciar** e selecione **Adicionar Funções e Recursos**.
3. No assistente, clique em **Avançar** até **Seleção de Funções**.
4. Marque **Serviço de Informações da Internet (IIS)**.
5. Expanda **Funções de Servidor**.
6. Selecione **CGI** e clique em **Avançar**.
7. Clique em **Instalar**.

### 6.4. Configurar Mapeamento de Handler para PHP no IIS

1. Abra o **Gerenciador do IIS**.
2. No painel **Conexões**, selecione o servidor ou o site onde deseja configurar o PHP.
3. No painel **Central de Recursos**, clique em **Mapeamento de Manipuladores**.
4. No painel **Ações**, clique em **Adicionar Módulo de Mapeamento...**.
5. Em **Solicitação**, digite `*.php`.
6. Em **Módulo**, selecione `FastCgiModule`.
7. Em **Executável**, digite o caminho para o PHP (`C:\php\php-cgi.exe`).
8. Nomeie o mapeamento como `PHP via FastCGI` e clique em **OK**.

### 6.5. Configurar Request Filtering para PHP

1. No **Gerenciador do IIS**, selecione o servidor ou o site onde deseja configurar o PHP.
2. No painel **Central de Recursos**, clique em **Filtragem de Solicitações**.
3. No painel **Ações**, clique em **Configurações de Regras de Solicitação**.
4. Clique em **Adicionar Permitida**.
5. Em **Verbo**, digite `POST`.
6. Em **Extensão**, digite `.php`.
7. Clique em **OK**.

## 7. Instalar e Configurar Certify the Web para HTTPS

1. A instalação desta ferramenta facilita a configuração de HTTPS no IIS.
2. Certificados SSL são necessários para criptografar comunicações e garantir a segurança dos dados.
3. A ferramenta Certify the Web pode solicitar certificados SSL automaticamente.

### 7.1. Instalar Certify the Web

1. Baixe o instalador do [Certify the Web](https://certifytheweb.com/) e execute-o.
2. Siga as instruções do instalador para concluir a instalação.

### 7.2. Configurar Certificado SSL

1. Abra o **Certify the Web**.
2. Clique em **New Certificate**.
3. Em **Domain**, insira `simasgame.cloudns.ch` e `www.simasgame.cloudns.ch`.
4. Clique em **Add**.
5. Clique em **Request Certificate**.
6. Após a conclusão, o certificado será instalado automaticamente no IIS.
7. O Binding de 443 é automaticamente adicionado nos dois hostnames no IIS.

![image](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/e611088d-3404-44d2-9efb-56181177c742)

## Conclusão

Após seguir esses passos, seu site estará configurado para ser acessado via HTTP e HTTPS usando o domínio `simasgame.cloudns.ch`. Certifique-se de verificar se todas as configurações estão funcionando corretamente acessando o site a partir de diferentes redes.
