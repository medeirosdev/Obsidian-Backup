
sintaxe antiga / sintaxe nova

docker ps  / docker container ls-> Visualizar containers que estão sendo executados
docker ps -a  / -> visualizar todos os containers já usados e usados no momento
docker pull {container_name} -> baixa o container

docker run {container_name} sleep 10 -> ele irá continuar rodando , e depois de 10s ele irá finalizar

docker run -it ubuntu -> Para usar o Sistema operacional, o -it serve para usar o container, dentro!

docker run / docker container run

Para ajudar -
docker --help // docker container --help

docker run -d -> o -d deixa o container em execução em background

Se existir já um container rodando de fundo, para executá-lo, use
docker exec -it _id_do_container_
Lembre-se que se for um OS, É NECESSÁRIO instalar e atualizar suas dependências
para isso : apt update -> no caso do ubuntu
e apt upgrade =y , para ubuntu também

Para sair do container, use "exitt apenas, e também quando usar o exit, ele continuará rodando no fundo, cuidado!

Para parar um container, use:
docker stop _id_do_container

Para remover um container, use

docker rm _id_container

O que pode consumir espaço são as IMAGENS
por isso, exclua

docker rmi   _nome_da_imagem

Para listar imagens

docker images

para renomear um ID
USE
docker run -dti --name  _nome_container nome_imagem
ex: docker run -dti --name Ubuntu1 ubuntu

 
Como copiar arquivo para dentro do contêiner 

use - cp -.> copy fille

docker cp NomeArquivo.txt NomeContainerqueElevai/Destino
docker cp arquiv.txt Ubuntu1:/pastadestino

Como copiar arquivos do container e levar até nossa máquia local

docker cp container_name:caminhodoarquivo.txt lugarquevouenviaroarquivo

através de tags na imagem selecionada, vc pode mudar de versões, e outras coisas.
ex: pegar a versão 9 da imagem debian e colocar no docker
docker pull debian:9 ->


![[OneDrive_2023-02-17.zip]]
## Parando e reiniciando um container

Para salvar um container e seus dados
docker 