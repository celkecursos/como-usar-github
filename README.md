# Como usar o GitHub

Baixar os arquivos do repositório do GitHub. O ponto no final do comando "." indica que o projeto será clonado no mesmo diretório.
```
git clone --branch <nome_da_branch> <ur_do_repositorio_no_github> .
```
```
git clone --branch dev-master https://github.com/celkecursos/como-usar-github.git .
```

Definir as configurações do usuário.
Definir o nome do usuário.
```
git config --local user.name <nome_do_usuario>
```
```
git config --local user.name Cesar
```

Definir o e-mail do usuário.
```
git config --local user.email <email_do_usuario>
```
```
git config --local user.email cesar@celke.com.br
```

Verificar a branch atual.
```
git branch 
```

Baixar as atualizações do repositório remoto.
```
git pull
```

Adicionar todos os arquivos modificados à staging area (área de preparação).
```
git add .
```

O commit representa um conjunto de alterações em um ponto específico do projeto, registrando apenas as alterações adicionadas à área de preparação. O comando -m permite inserir a mensagem do commit diretamente na linha de comando.
```
git commit -m "Descrição do commit"
```

Enviar os commits locais para um repositório remoto.
```
git push <nome_padrao_do_repositorio_remoto> <nome_da_branch>
```
```
git push origin dev-master
```

Criar nova branch no PC.
```
git checkout -b <nome_da_branch>
```
```
git checkout -b main
```

Trocar de branch.
```
git switch <nome_da_branch>
```
```
git switch main
```

Mesclar o histórico de commits de uma branch em outra branch.
```
git merge <nome_da_branch>
```
```
git merge dev-master
```

Fazer o push das alterações de uma branch para outra.
```
git push <nome_padrao_do_repositorio_remoto> <nome_da_branch>
```
```
git push origin main
```

## Conectar o PC ao servidor com SSH

Criar chave SSH (chave pública e privada).
```
ssh-keygen -t rsa -b 4096 -C "seu-email@exemplo.com"
```
```
ssh-keygen -t rsa -b 4096 -C "cesar@celke.com.br"
```

Senha usada na aula, não utilizar a mesma: 36CFc3#3t75W<br>

Local que é criado a chave pública.
```
C:\Users\SeuUsuario\.ssh\
```
```
C:\Users\cesar/.ssh/
```

Exibir o conteúdo da chave pública.
```
cat ~/.ssh/id_rsa.pub
```

Acessar o servidor com SSH.
```
ssh <usuario>@<ip_do_servidor>
```
```
ssh root@93.127.210.72
```

Usar o terminal conectado ao servidor para listar os arquivo.
```
cd /var/www/html
```

Listar os arquivo.
```
ls
```

Remover os arquivos do servidor.
```
rm -rf /var/www/html/{*,.*}
```

Compactar os arquivos com ZIP. Usar terminal sem conexão com o servidor.
```
Compress-Archive -Path .\* -DestinationPath celke_hostinger.zip
```

Enviar o projeto local para o servidor. Usar terminal sem conexão com o servidor.
```
scp /caminho/do/seu/projeto.zip <usuario_ssh>@<ip_do_servidor>:/var/www/html/
```
```
scp C:\celke\celke_hostinger.zip root@93.127.210.72:/var/www/html/
```

Usar o terminal conectado ao servidor. Primeiro acessar o diretório do projeto no servidor. Em seguida descompactar o arquivo.
```
cd /var/www/html/
```
```
unzip celke_hostinger.zip
```

Se não tiver "unzip" instalado no servidor, atualize a lista de pacotes. Usar o terminal conectado ao servidor.
```
sudo apt update
```

Instalar unzip. Usar o terminal conectado ao servidor.
```
sudo apt install unzip
```

Reiniciar o Apache. Usar o terminal conectado ao servidor.
```
sudo systemctl restart apache2
```

Remover o arquivo compactado do servidor.
```
rm -rf /var/www/html/<nome_do_arquivo>
```
```
rm -rf /var/www/html/celke_hostinger.zip
```

## Conectar Servidor ao GitHub

Gerar a chave SSH no servidor.
```
ssh-keygen -t rsa -b 4096 -C "cesar@celke.com.br"
```

Imprimir a chave pública gerada.
```
cat ~/.ssh/id_rsa.pub
```

No GitHub, vá para Settings (Configurações) do seu repositório ou da sua conta, em seguida, vá para SSH and GPG keys e clique em New SSH key.<br>
Cole a chave pública no campo fornecido e salve.<br>

Verificar a conexão com o GitHub.
```
ssh -T git@github.com
```

Se gerar o erro "The authenticity of host 'github.com (xx.xxx.xx.xxx)' can't be established.".<br>
Isso é uma medida de segurança para evitar ataques de "man-in-the-middle".<br>
Necessário adicionar a chave do host do GitHub ao arquivo de known_hosts do seu servidor.<br>

Digite yes quando for solicitado.
```
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
```

Mensagem de conexão realizada com sucesso.<br>
Hi nome-usuario! You've successfully authenticated, but GitHub does not provide shell access.<br>

Usar o terminal conectado ao servidor para listar os arquivo.
```
cd /var/www/html
```

Listar os arquivo.
```
ls
```

Remover os arquivos do servidor.
```
rm -rf /var/www/html/{*,.*}
```

Baixar os arquivos para o servidor do GitHub via SSH.
```
git clone -b <branch_name> <repository_url_ssh> .
```
```
git clone -b main git@github.com:celkecursos/como-usar-github.git .
```

Verificar e baixar as atualizações do projeto no GitHub via SSH.
```
git pull
```

## Administrar o MySQL no Servidor LAMP

Verificar se o PDO está habilitado.
```
php -m | grep pdo
```

Abrir o prompt do MySQL.
```
sudo mysql
```

Alterar o método de autenticação root.
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'senha_usada_para_instalar_lamp';
```

Acessar o MySQL no servidor.
```
sudo mysql -u root -p
```

Senha usada na aula, não utilizar a mesma: 36CFc3#3t75W<br>

Listar bancos de dados.
```
SHOW DATABASES;
```

Criar banco de dados.
```
CREATE DATABASE nome_do_banco;
```

Acessar o banco de dados.
```
USE nome_do_banco;
```

Comando SQL para criar tabela no banco de dados.
```
CREATE TABLE IF NOT EXISTS `usuarios` (
  `id` int NOT NULL AUTO_INCREMENT,
  `nome` varchar(220) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL,
  `email` varchar(220) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=13 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```

Comando SQL para cadastrar registro no banco de dados.
```
INSERT INTO `usuarios` (`nome`, `email`) VALUES
('Cesar', 'cesar@celke.com.br'),
('Kelly', 'kelly@celke.com.br'),
('Jessica', 'jessica@celke.com.br'),
('Gabrielly', 'gabrielly@celke.com.br');
```

Abrir o arquivo de conexão com banco de dados e alterar as credenciais.
```
nano conexao.php
```