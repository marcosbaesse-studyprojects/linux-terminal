# Linux no Terminal

# Acesso por SSH no Windows

No windows, é comum o uso do Putty, para acesso ssh.
Também é comum o uso do puttygen, para gerar as chaves

No putty deve-se informar apenas o IP, o Username e o Password.
a porta do ssh é 22

AS configurações do ssh ficam em: '/etc/ssh/ssgd_config'

Para permitir o login apenas de chaves autorizadas, utiliza-se o putty gen.
Sempre deve-se gerar uma chave pública e privada

A chave privada nunca deve ser disponibilizada, ela é especídica de cada computador

A chave pública não deve conter quebras de linha

Para realizar o acesso ssh, deve informar na máquina onde se deseja acessar, a chave pública gerada na máquina windows.

essa informação é salva no arquivo '~# .ssh/suthorized-keys'

no seguinte formato:

```ssh-rsa CHAVE-PUBLICA-DO-WINDOWS```

Deve-se ter atenção para remover as quebras de linha contidas na chave.

## Configurar o putty para o ssh

### Categoria /Connection/Data

* Auto-login username: informar o nome de usuário (root, joaodascouves, xpto...)

### Categoria /Connection/SSH/Auth

* informa a localização da chave privada.

## Conectar

Com as configurações definidas, pode-se realizar a conexão ssh facilmente.

## Permitir acesso apenas daquela chave públic

No arquivo de configuração do ssh
* PermitRootLogin without-password

Então, após reiniciar o serviço do ssh (sshd), ele aceitará o login apenas das chaves públicas informadas.

# Acesso por SSH no Linux

O linux não necessita do putty para se realizar o acesso por ssh, pois ele já possui o ssh nativo:

* ssh usuario@ip.host.remoto

## Para gerar a chave no linux

* ssh-keygen

a chave fica armazenada em: ```/home/usuario/.ssh/id_rsa```

Pode-se informar um nome diferente para chave, ao invés de id_rsa.

## Para informar a chave para o servidor, sem alterar o arquivo de chaves autrizadas diretamente:

* ssh-copy-id usuario@ip.host.remoto

# O comando apt

O comando apt é utilizada em distribuições **debian-based** para gerenciar os pacotes do sistema

* apt-get update: atualiza as versões dos pacotes a partir da source-list
* apt-get upgrade: atualiza os pacotes do sistema
* apt-get install <pacote>: instala o pacote
* apt-get remove <pacote>: remove o pacote
* apt-get purge <pacote>: remove o pacote, e arquivos de cache que o pacote pode gerar na instalação
* apt-cache search <termo>: busca pacotes que tenham o nome ou descrição informado
* apt-cache search -n <termo>: buca pacotes que tenham o nome informado.
* apt-cache show <pacote>: mostra informações do pacote
* apt-get install -d <pacote>: baixa o pacote, não instala

## Fonte dos pacotes

Os pacotes são buscados dos repositórios informados na source-list:
* /etc/apt/sources.list

Após adicionar um repositório na source-list, deve rodar o apt-get update

#Usuários grupos permissões

Comandos para gerenciar grupos e usuários:

* adduser <usuario>: Cria o usuário, diretório, senha e grupo
* useradd <usuario>: Apenas o usuário, sem as configurações
* su - <usuario>: troca a sessão do usuario, no termial
* passwd: troca a senha do usuário da sessão atual
* passwd <usuario>: troca a senha do usuário informado
* cat /etc/passwd: mostra todos os usuários do sistema, e suas devidas informações de acesso
* cat /etc/shadow: mostra a senha (criptografada) dos usuários
* deluser <usuario>: deleta o usuário
* deluser <usuario> --remove-home: deleta o usuário e a pasta home
* deluser <usuario> --backup: deleta o usuário, mas cria um arquivo de backup das informações e configurações do usuário deletado.
* adduser <usuario> <grupo>: Adiciona o usuário a um grupo.
