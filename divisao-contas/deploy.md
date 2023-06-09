# Criar o projeto
- [OK] Criar o repositório
- [OK] Criar o projeto local
- [OK] Conectar com o repositório
- [OK] Alterar para Hello World
# Criar o servidor em nuvem. O que é Nuvem? O que é uma máquina virtual?
- [OK] Acessar por SSH. O que é SSH?
- [OK] apt update && apt upgrade
- [OK] Instalar e habilitar Firewall. O que é Firewall? Analogia do Porteiro
- [OK] apt install nginx certbot python3-certbot-nginx
- [OK] ufw allow "Nginx Full"
- [OK] ufw allow OpenSSH
- [OK] ufw enable
- [OK] Instalar o Node. O que é o Node? Por que vamos usar Node?
- [OK] apt install npm
- [OK] curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
- [OK] source ~/.bashrc
- [OK] npm install -g pm2
# Criar o subdomínio e encaminhar para o servidor
# Configurar o Firewall e registrar a aplicação
* cd /etc/nginx
* cd sites-available
* touch divisao-contas
* vi divisao-contas
	```server {
        listen 80;
        server_name divisao-contas.devs4.fun;

        gzip on;
        gzip_proxied any;
        gzip_types application/javascript application/x-javascript text/css text/javascript;
        gzip_comp_level 5;
        gzip_buffers 16 8k;
        gzip_min_length 256;

        location /_next/static/ {
                alias /var/www/divisao-contas/.next/static/;
                expires 365d;
                access_log off;
        }

        location / {
                proxy_pass http://127.0.0.1:3000;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection 'upgrade';
                proxy_set_header Host $host;
                proxy_cache_bypass $http_upgrade;
        }
}```
* Alterar a pasta em que o nginx guarda as configurações
	* vi /etc/nginx/nginx.conf
	* Alterar `include /etc/nginx/sites-enabled/*;` para `include /etc/nginx/sites-available/*;`
	* nginx -t
	* rm /etc/nginx/sites-available/default
	* rm /etc/nginx/sites-enabled/default
	* systemctl restart nginx
# Integrar/autenticar o GitHub
* ssh-keygen -t ed25519 -C "cainitech@gmail.com"
* eval "$(ssh-agent -s)"
* ssh-add ~/.ssh/id_ed25519
* cat ~/.ssh/id_ed25519.pub
* Clonar o repositório
	* npm install
	* editar .env
	* npm run build
# Inicializar a aplicação no servidor
* pm2 start npm --name divisao-contas -- start
# Habilitar HTTPS
* certbot --nginx -d divisao-contas.devs4.fun

# ########################

# Instalar o MySQL no servidor
* apt install mysql-server
* systemctl start mysql.service
* systemctl status mysql.service
* Trocar a senha do usuário `root`
	* mysql
	* ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'tiroliro123';
	* exit
* mysql_secure_installation (Responder todo o questionário e esperar terminar o script)
# Criar usuário pra aplicação no Banco de Dados
* mysql -u root -p (ou somente mysql se não tiver trocado a senha)
* CREATE USER 'divisaocontas'@'%' IDENTIFIED WITH authentication_plugin BY 'divisaoXPTO@123';
# Liberar acesso remoto ao banco de dados - https://www.digitalocean.com/community/tutorials/how-to-allow-remote-access-to-mysql
* 