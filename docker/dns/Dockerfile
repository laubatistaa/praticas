FROM ubuntu:latest

#instalar ferramentas da rede
RUN apt update -y
RUN apt upgrade -y
#aqui ele pega a imagem com algumas configurações de DNS, 
#mas não tudo
RUN apt install bind9 dnsutils -y
#Copia arquivo dentro do container para personalizar,
#o caminho relativo se torna o dockerfile. 
COPY named.conf.local /etc/bind

COPY db.asa.br /etc/bind
#para abrir as portas
EXPOSE 53/tcp
EXPOSE 53/udp
# esse named é o servidor DNS é ele quem abre as portas

CMD ["/usr/sbin/named", "-g", "-c", "/etc/bind/named.conf", "-u", "bind"]