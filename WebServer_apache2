# Servidor Web utilizando apache2

Baixe a imagem do Raspbian no próprio site da fabricante: http://www.raspberrypi.org/downloads
É necessário a conexão com a internet para baixar os pacotes necessários.

Primeiro vamos criar um usuário para que não fique com o padrão só por uma questão de segurança, caso você venha a disponibilizar o acesso a rede.

Adicione um usuário com uma senha:

sudo useradd -m mikael sudo passwd mikael123 

Adicione aos grupos necessários, coloque no final do arquivo o usuário criado /etc/group

adm:x:4:pi,mikael

Agora saia do usuário e logue com o novo.

Defina o shell padrão dele como o bash

chsh -s /bin/bash

Agora você já pode retirar o usuário "pi" se você quiser.

userdel pi

Já que vamos utilizar ele como servidor, é bom diminuir o uso de memória para a interface já que não vamos utiliza-la:

cp /boot/arm224_start.elf /boot/start.elf

Configurando a rede

Defina o endereço do raspberry pi comom estático, edite o arquivo /etc/network/interfaces :

iface eth0 inet static 
address 192.168.1.4 
netmask 255.255.255.0 
gateway 192.168.1.1 

Defina também o dns dele para o roteador, edite o arquivo /etc/resolv.conf :
nameserver 192.168.1.1

Reinicie o raspberry para garantir as modificações feitas


Acesse via ssh

ssh mikael@192.168.1.4

Permita a conexão e ele irá pedir suas credenciais, faça o login e pronto, já temos acesso.

É necessário liberar o tráfego para o raspberry caso você queira acessar ele da internet de qualquer lugar,
sendo assim, siga a documentação do seu roteador e habilite as portas 22 e 80 para o raspberry pi.

Agora sim, vamos a instalação do servidor =)

Instale o apache2:
apt-get install apache2

Instale o mysql, durante a instalação ele irá pedir a criação de usuário e senha, crie e não esqueça (;
apt-get install mysql-server

Instale o php5
apt-get install php5 php5-mysql 

Pronto, agore teste o php criando um arquivo de teste:
nano /var/www/info.php ou /var/www/html/info.php
<?php 
  infophp();
?>

Caso as informações referente a versão instalada do php apareçam na tela, está tudo certo :)
