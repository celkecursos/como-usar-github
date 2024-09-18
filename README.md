# Como usar o GitHub

Baixar os arquivos do repositório do GitHub. O ponto no final do comando "." indica que o projeto será clonado no mesmo diretório.
```
git clone --branch <nome_da_branch> <ur_do_repositorio_no_github> .
```
```
git clone --branch dev-master <ur_do_repositorio_no_github> .
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

