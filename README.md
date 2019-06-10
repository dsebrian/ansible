<h2> README para execução do exercício de publicação de aplicação go em um Container Docker </h2>

# Hospedeiro utilizado
- Ubuntu 18.04
- Ansible instalado e configurado
- Acesso a internet (acesso aos repositórios necessários da distribuição, Git Hub e Docker)
- Clone desse repositório do Git.

# Descrição das atividades
No hospedeiro, executar o clone desse repositório do Git e executar apenas o playbook main.yml (comando para execução abaixo).
Esse Playbook main.yaml executa:
- Instalação do PIP e suas dependências
- Instalação do Docker e suas dependências
- Instalação do Docker Compose e suas dependências
- Gera uma imagem do Docker a partir de um dockerfile
- Executa o container
- Valida se o container está ativo

# Comando para execução do playbook:
...
- Se o Docker estiver na mesmo host do Ansible <br>
sudo ansible-playbook --connection=local -i IP_do_Docker, main.yml -v

- Se o Docker estiver em outro host do Ansible <br>
sudo ansible-playbook -i IP_do_Docker, main.yml -v
...

# Container
A imagem gerada é baseada na goolang e está expondo a porta 8080, acessível em HTTPS.
Essa imagem já acessa ao Git Hub, trazendo e disponibilizando ao container os arquivos necessários para sua configuração e execução.<br>
URL para acesso do host: https://ipdocontainer:8080

Dentro do container sempre é executada a aplicação compilada main.go, que chamei o aplicativo de mainexec.




