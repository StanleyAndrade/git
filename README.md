# Open Git GUI Here
Abre uma interface com botões, pra quem não quer trabalhar  com código. 

# Open Git Bash Here
Pra quem quer trabalhar com códigos

# cd e cd "pasta"
Usado para transitar entre pastas. cd puro sai, acompanhado de um nome, ele acessa a pasta. 

# ls
Lista tudo o que tem na pasta

# ls .ssh/
Lista as chaves ssh privadas e publicas QUE ESTÃO DENTRO DA PASTA SSH: .epub, rsa, known_hosts.
Elas ficam salvas na raiz do computador. 
Essas chaves SSH são usadas para se autenticar em servidores sem precisar de senha. No Git, isso é útil para clonar, fazer push e pull de repositórios privados sem precisar digitar a senha toda hora.
- id_ed25519 – Sua chave privada SSH (usando o algoritmo Ed25519).
- id_ed25519.pub – Sua chave pública correspondente.
- id_rsa – Outra chave privada, mas no formato RSA (um método mais antigo de criptografia).
- id_rsa.pub – Chave pública correspondente à id_rsa.
- known_hosts – Registro de servidores que você já conectou via SSH.
- known_hosts.old – Uma cópia antiga do known_hosts, geralmente criada quando algo muda.

# ssh -T git@github.com
Verifica qual chave está sendo usada no GitHub/GitLab
A mensagem será assim: 
Hi SEU_USUARIO! You've successfully authenticated, but GitHub does not provide shell access.

# rm nome_do_arquivo
Apaga um arquivo permanentemente. Para apagar uma chave ssh: 
rm ~/.ssh/id_rsa

# rm -r nome_da_pasta
Apaga uma pasta permanentemente. O -r significa "recursivo". Ele apaga a pasta e tudo o que está dentro dela. 

# trash nome_do_arquivo
Não apaga permanente, apenas manda para a lixeira. 

# Passo a passo pra usar 2 contas Github no Git
- Você precisa de uma pasta ssh na raiz do computador. Verifique se ela existe: ls -la ~
- Se ela não existir, vá pra raiz do computador e crie a pasta ssh se ela não existir: mkdir -p ~/.ssh

## Agora crie os arquivos pra pastar ssh
- ssh-keygen -t ed25519 -C "emailpessoal@gmail.com"
- /c/Users/user/.ssh/pessoal_ed25519 ( copie o caminho que aparecer pra você)
- ssh-keygen -t ed25519 -C "emailempresarial@gmail.com"
- /c/Users/user/.ssh/empresarial_ed25519 ( copie o caminho que aparecer pra você)
- cat ~/.ssh/id_github_pessoal.pub Copie o conteúdo e adicione em GitHub (Conta Empresarial) → Settings → SSH and GPG keys
Clique em New SSH Key e cole a chave. Em title coloque pessoal e empresarial em cada um.
- nano ~/.ssh/config dentro do arquivo coloque assim:
# Conta pessoal
Host github-pessoal
    HostName github.com
    User git
    IdentityFile ~/.ssh/pessoal_ed25519
# Conta empresarial
Host github-empresarial
    HostName github.com
    User git
    IdentityFile ~/.ssh/empresarial_ed25519
Salve e feche (no Nano, pressione Ctrl + X, depois Y e Enter).
- Teste as contas ssh -T git@github-pessoal
- Se tiver ok, você verá: Hi SEU_USUARIO_PESSOAL! You've successfully authenticated, but GitHub does not provide shell access.

# Como fica pra usar? 
# SSH-Agent
- eval "$(ssh-agent -s)"
- ssh-add ~/.ssh/pessoal_ed25519
- ssh-add ~/.ssh/empresarial_ed25519

# Clonando do GitHub
- git clone git@github-pessoal:pessoal/repositorio.git
- git config user.email "nome@gmail.com" (com globa, configura pra todos os projetos)
- git config user.name "nome"

- git remote add origin git@github.com:stanleyclientes/midiararario.git coloca endereço do repositório em projeto que NÃO TEM NENHUM
- git push -u origin main
- git remote set-url origin git@github-pessoal:usuario_pessoal/repositorio.git atualiza endereço em repositório em projeto que JÁ TEM ENDEREÇO
- git push
- git remote -v checa origem

- git remote remove origin (remove o origin pra colocar um novo)
- git push origin main (primeiro push)
- git push (2º em diante)

Em cada projeto, será preciso fazer essa configuração, especificando qual é pessoal e qual nã é: 
- git config user.email "nome@gmail.com"
- git config user.name "nome"
- eval $(ssh-agent -s)
- ssh-add ~/.ssh/empresarial_ed25519 ou outro
- git branch -M main
- git remote add origin git@github.com:stanleyclientes/nome.git
- git push -u origin main

Desfazer commit localmente e no github
- git reset --hard HEAD~1
Ele apaga o ultimo commit localmente. O número no final identifica quantos commits vai apagar.

- git push --force
Ele atualiza o Github. 








