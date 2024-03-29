<h2> README para execução do exercício de publicação de aplicação go em um Container Docker </h2>

# Hospedeiro
- Ubuntu 18.04 (utilizado para montagem do teste)
- Ansible instalado:
```
sudo apt-get install ansible
```

- Git instalado
```
sudo apt-get install git
```
- Acesso a internet (acesso aos repositórios necessários da distribuição, Git Hub e Docker)
- Criar pasta para utilizar no teste
```
mkdir $HOME/nomedapasta
```
- Clone desse repositório do Git
```
git clone https://github.com/dsebrian/ansible.git $HOME/nomedapasta
```

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
- Se o Docker estiver na mesmo host do Ansible, a interface local do docker (chamada docker0) terá por padrão o IP 172.17.0.1
```
cd $HOME/nomedapasta/docker/docker_project
sudo ansible-playbook --connection=local -i 172.17.0.1, main.yml -v
```
- Se o Docker estiver em host diferente do Ansible, alterar o IP do servidor
```
cd $HOME/nomedapasta/docker/docker_project
sudo ansible-playbook -i IP_do_Servidor_Docker, main.yml -v
```

# Container
A imagem gerada é baseada na goolang e está expondo a porta 8080, acessível em HTTPS.
Essa imagem já acessa ao Git Hub, trazendo e disponibilizando ao container os arquivos necessários para sua configuração e execução.<br>
URL para acesso do host: https://ipdocontainer:8080 - pode ser acessada via browser ou via terminal (utilizando curl https://ipdocontainer:8080 por exemplo)
Se o container for o único e não houver alteração nas configurações de rede, o IP padrão do container será 172.17.0.2.

Dentro do container é executada automaticamente a aplicação compilada main.go, que chamei o aplicativo de mainexec, sem a necessidade de acesso interativo ao container.




