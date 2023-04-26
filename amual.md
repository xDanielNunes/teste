# Como disponibilizar a página do DiarioAnimes em um container Docker no Laboratório Elan


#### 1º passo (Acesso ao ELAN):

No prompt de comando, execute o comando: 

`ssh -x usuario@200.17.141.82 -o 3333`

"usuario" é seu nome de usuário do SIGAA, 
após a execução desse comando, 
insira a senha que equivale ao seu número de matrícula, 
e efetue a maudança da mesma, logo após.

#### 2º passo (Construindo imagem com Dockerfile):


Execute o comando:

`git clone https://github.com/othonb/pythonUDPTCP.git`

caso não possua o arquivo TCPServer.py.

Execute o comando:

`nano Dockerfile`

Copie e cole os seguintes comandos no editor de arquivos:

`FROM python:3-slim`

`LABEL version="1.0.0" description="DiarioAnimes" maintainer="Daniel Nunes Oliveira` `<danielnunesoliveira@academico.ufs.br>"`
`WORKDIR /usr/src/daniel`

`COPY . .`

`EXPOSE 12000`

`CMD [ "python3", "./pythonUDPTCP/TCP/TCPServer.py" ]`

Salve o arquivo.

Execute o comando:

`docker build -t daniel .`

para contruir a imagem a partir do Dockerfile.

Execute o comando:

`docker run -d -p 12008:12000 -it --rm --name diarioanimes daniel`

para criar o container.













