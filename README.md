<h2> README do exercício de publicação de aplicação go em container docker </h2>
#Premissas:

#Hospedeiro
- Ubuntu 18.04
- Ansible
- Acesso a internet (acesso ao repositório da dist, Git Hub e Docker)


#Descrição das atividades
No hospedeiro, executar apenas o playbook main.yml.
Esse Playbook main.yaml executa:
- Instalação do PIP e suas dependências no hospedeiro
- Instalação do Docker Compose e suas dependências no hospedeiro
- Gera uma imagem do Docker a partir de um dockerfile
- Executa o container
- Valida se o container está ativo

#comando para execução do playbook:
sudo ansible-playbook --connection=local -i IP_do_Docker, main.yml -v

#Container
A imagem gerada é baseada na goolang e está expondo a porta 8080, acessível em HTTPS.
Essa imagem já acessa ao Git Hub, trazendo e disponibilizando ao container os arquivos necessários para sua configuração e execução.
Para acesso do host, https://ipdocontainer:8080




