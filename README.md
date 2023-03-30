# signing-commit

Esse repositório foi criado explusivamente para testar a assinatura de commits.


### Comandos

*Importante:* Certifique-se que você tenha configurado em sua máquina os dados globais do git como `nome` e `email`.

#### 1° Etapa
```shell
git config --global user.name "Seu nome aqui"
git config --global user.email "Seu email aqui"
```

Agora é possível começar o processo de assinatura de commits.

#### 2° Etapa

```shell
# Cria uma chave secreta por meio de um menu interativo no shell
gpg --full-generate-key

# Lista todas as chaves secretas geradas pelo gpg
gpg --list-secret-keys --keyid-form LONG

# Defina a chave da sua assinatura caso queira sempre usar a mesma chave para qualquer repositório defina a flag --global
# Você pode encontrar a key usando o comando acima
git config user.signingkey SUA_KEY

# Defina se as tags serão assinadas caso queira que a configuração seja global, use a flag "--global"
git config tag.gpgSign true

# Defina se os commits serão assinadas caso queira que a configuração seja global, use a flag "--global"
git config commit.gpgsign true

# Defina essa Variável em seu Sistema Operacional
export GPG_TTY=$(tty)
```
#### 3° Etapa
- **Cadastre a GPG KEY no Github**
```shell
  # retorna a sua chave privada para ser cadastrada no github.
  gpg --armor --export SUA_KEY
```
[Como cadastrar a chave gpg no github ?](https://docs.github.com/en/enterprise-server@3.5/authentication/managing-commit-signature-verification/adding-a-gpg-key-to-your-github-account)
 
 
### Considerações Finais
Agora ao realizar um commit será solicitado a mesma senha que foi definida ao usar  o commando `gpg --full-generate-key`. Digite a senha na janela, feito isso faça o push das suas modificações e verifique se o commit está assinado no Github.

