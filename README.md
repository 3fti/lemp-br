# LEMP-br
 LEMP usando o Repositório oficial Docker para Alpine Linux, Nginx, MariaDB, PHP e phpMyAdmin | Compatível com Raspbery, Orange PI e familia

# Preparação
sudo apt-get update && sudo apt-get install nano \
cd lemp-br \
mv LEMPBR .. \
cd ../LEMPBR \
nano docker-compose.yml

# Ajustes
Altere todas as linhas abaixo com a sua informação desejada.\
# container_name
container_name: LEMPBR_nginx para container_name: SEUPROJETO_nginx \
container_name: LEMPBR_mariaDB para container_name: SEUPROJETO_mariaDB \
container_name: LEMPPBR_php para container_name: SEUPROJETO_php \
container_name: LEMPBR_phpMyAdmin para container_name: SEUPROJETO_phpMyAdmin \

# networks:
Altere de LEMPBR para o nome desejado.

# volumes
Na sessão nginx: - ./webapps:/LEMPBR/webapps para  - ./webapps:/SEUPROJETO/webapps \
Na sessão php: - ./webapps:/LEMPBR/webapps para - ./webapps:/SEUPROJETO/webapps \



# Opcionais
Se desejar pode também alterar as portas espelhadas e a senha do usuário root do banco de dados.

# ports
Nas sessões ports altere sempre a primeira porta para a porta que deseja espelhar. \
Ex: \
   - "8183:80" para "8585:80".
# root passoword
A senha atual do usuário root é "654321" para altera-la, vá até a sessão mariaDB e altere em environment o valor da chave "- MYSQL_ROOT_PASSWORD"

# NGINX
nano nginx/default.conf 
Altere a linha 7 para pasta que desejar, este procedimento só deve ser executado caso a pasta em questão não seja LEMPBR, ou seja, tenha sido renomeada para customizar o ambiente.

# Para iniciar LEMP-br:
docker-compose up -d

# Para parar LEMP-br:
docker-compose stop

# Para remover LEMP-br:
docker-compose down

# Acessando
phpMyAdmin: http://<ip ou nome do host>:8183
 Banco: mariaDB
 Usuário: root
 Senha: 654321
 
 Nginx: http://<ip ou nome do host>:8080
 Será apresentada a versão do PHP do ambiente.
 
 # Utilizando
 Para usar o ambiente, basta desenvolver seus projetos na pasta "webapps" que ja está ajustada para carga do servidor web.

# Compatibilidade Especial
Compatível com Raspbery, Orange PI e familia.. projeto desenvolvido em um Orange PI PC(armv7)

![lemp-container](https://github.com/frekans7/docker-compose-lemp/blob/master/LEMP/code/img/LEMP.gif)
![php](https://github.com/serkan7/docker-compose-lemp/blob/master/LEMP/code/img/php.png)                                     
![phpMyAdmin](https://github.com/serkan7/docker-compose-lemp/blob/master/LEMP/code/img/phpMyAdmin.png)
# Projeto base
frekans7/docker-compose-lemp
 
