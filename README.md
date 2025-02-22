# Open Git GUI Here
Abre uma interface com botões, pra quem não quer trabalhar  com código. 

# Open Git Bash Here
Pra quem quer trabalhar com códigos

# cd e cd "pasta"
Usado para transitar entre pastas. cd puro sai, acompanhado de um nome, ele acessa a pasta. 

# ls
Lista tudo o que tem na pasta

# ls .ssh/
Lista as chaves ssh privadas e publicas, .epub, rsa, known_hosts.
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


