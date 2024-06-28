# Burp Suite Setup and Intruder Usage

Este projeto demonstra como configurar o Burp Suite para interceptar o tráfego do navegador e usar o Intruder para realizar ataques de força bruta com wordlists de usuários e senhas.

## Conteúdo

- [Configuração do Proxy no Navegador](#configuração-do-proxy-no-navegador)
- [Configuração do Burp Suite](#configuração-do-burp-suite)
- [Wordlists](#wordlists)

## Pré-requisitos

- Burp Suite instalado
- Navegador (Chrome, Firefox, etc.)
- Wordlists para usuários e senhas

## Configuração do Proxy no Navegador

### Passo a Passo

1. Abra as configurações do seu navegador.
2. Vá para as configurações de rede ou proxy.
3. Ative manualmente o proxy.
4. Configure o proxy para `localhost` e a porta que o Burp Suite está utilizando (geralmente 8080).

### Exemplo no Firefox

1. Abra as `Preferências`.
2. Vá para `Configurações de Rede`.
3. Selecione `Configuração manual de proxy`.
4. Em `HTTP Proxy`, insira `localhost` e a porta `8080`.
5. Clique em `OK`.

Após essa configuração, o navegador redirecionará o tráfego através do Burp Suite.

## Configuração do Burp Suite

### Passo a Passo

1. Abra o Burp Suite.
2. Vá para a aba `Proxy`.
3. Clique em `Intercept` e ligue o `intercept`.
4. Configure a porta em que o Burp Suite ouvirá o tráfego (geralmente 8080).

### Testando a Configuração

1. Tente acessar qualquer site no navegador configurado.
2. Verifique se o Burp Suite captura a requisição.

Se tudo estiver configurado corretamente, você verá as requisições sendo interceptadas pelo Burp Suite.

### Usando o Intruder

1. Com o `Intercept` ligado, tente acessar um site alvo.
2. No Burp Suite, selecione a requisição que deseja atacar.
3. Envie a requisição para o `Intruder` clicando com o botão direito e selecionando `Send to Intruder`.
4. Vá para a aba `Intruder`.
5. Configure os pontos de ataque usando a técnica `Cluster Bomb`.
6. Carregue suas wordlists para `users` e `passwords`.
7. Inicie o ataque e analise os resultados.

## Wordlists

Coloque suas wordlists no diretório `wordlists/` deste projeto.

- `users.txt`
- `passwords.txt`

### Exemplo de Wordlists

#### users.txt

```
admin
user
test
```

#### passwords.txt

```
password
123456
admin
```

## Como usar este projeto

1. Siga as instruções na seção [Configuração do Proxy no Navegador](#configuração-do-proxy-no-navegador).
2. Configure o Burp Suite conforme as instruções na seção [Configuração do Burp Suite](#configuração-do-burp-suite).
3. Prepare suas wordlists no diretório `wordlists/`.
4. Utilize o Burp Suite para interceptar e atacar o site alvo.


Você pode criar a estrutura do projeto e adicionar o conteúdo acima ao arquivo `README.md`. Adicione também as wordlists nos arquivos `users.txt` e `passwords.txt` dentro da pasta `wordlists/`.
