
#!/bin/bash
vpspackversion=5.8
OS=`uname -m`;
fecha=`date`;
IP=$(wget -qO- ipv4.icanhazip.com)
fun_bar () {
comando[0]="$1"
comando[1]="$2"
(
[[ -e $HOME/fim ]] && rm $HOME/fim
${comando[0]} -y > /dev/null 2>&1
${comando[1]} -y > /dev/null 2>&1
touch $HOME/fim
) > /dev/null 2>&1 &
tput civis
echo -ne "  \033[1;33mESPERE \033[1;37m- \033[1;33m["
while true; do
for((i=0; i<18; i++)); do
echo -ne "\033[1;31mΔ"
sleep 0.1s
done
[[ -e $HOME/fim ]] && rm $HOME/fim && break
echo -e "\033[1;33m]"
sleep 1s
tput cuu1
tput dl1
echo -ne "  \033[1;33mESPERE\033[1;37m- \033[1;33m["
done
echo -e "\033[1;33m]\033[1;37m -\033[1;32m OK !\033[1;37m"
tput cnorm
}
#rm -rf /etc/VpsPackdir
vp="/etc/VpsPackdir"
echo -e "\e[1;31m ESPERE POR FAVOR......."
echo -e "\e[1;31m ATENCION POR FAVOR.......\n 🏁🏁 ya casi.. enter y seguimos 5\n "
read -p "Escribir S y continuar🐸 (s/n)?: " responder
if [[ "$responder" = 's' ]]; then

if [ $(id -u) != 0 ]
then
echo "Ejecute el script como root"
exit
fi
clear
cd /root
[[ ! -d ${vp} ]] && mkdir ${vp}
#extrallendo
#SCRIPT SOLO PARA TESTEO : PUEDA QUE SALGA ALGUN ERROR..., NOTIFIQUELO AL GRUPO @

#reventado por : fulano🐥🦉

iniciar(){
mkdir /etc/vp &>/dev/null
cd /etc/vp
wget https://raw.githubusercontent.com/lacasitamx/vpspack5.8/master/source/clean.zip &>/dev/null
unzip clean.zip &>/dev/null
cp pack/* ${vp}/
chmod +x ${vp}/*
echo -e " codigo extraido con exito😋😋 "
rm -rf /etc/vp/clean.zip
rm -rf /etc/pack
sleep 2
cd /root
}
iniciarbin(){
linkbin=https://raw.githubusercontent.com/lacasitamx/vpspack5.8/master/source/rebin.zip
cd /etc/vp
wget $linkbin &>/dev/null
unzip rebin.zip &>/dev/null
cp rebin/* /bin/

chmod +x /bin/vpspack /bin/toolmaster /bin/renovarusuario /bin/redefinirusuario /bin/deletarusuario /bin/criarusuario /bin/limite /bin/speedtest.py /bin/instaladores
echo -e " bin extraido con exito 😎😎🐸🐸🐝😎 "
sleep 2
rm -rf /etc/vp
cd /root
}
echo -e "\e[43m OK... ESPERE UN MOMENTU😴😴🐴🐴uu>\e[0m"
echo ""
fun_bar 'apt-get install zip -y'
fun_bar 'apt-get install unzip -y'
iniciar
cat /etc/VpsPackdir/logo
echo -e "[\033[1;31m-\033[1;33m]\033[1;30m ───────────────────────────────────────\033[1;33m"
echo -e "\033[1;33mInstalando \033[1;32mVPSPack $vpspackversion\033[0m"
echo -e "\033[1;33mEspere por favor🤔🤔\033[0m"
echo -e "\033[1;33mSe instalaran los paquetes necesarios🙂🙂\033[0m"
echo -e "\033[1;33mGrupo de Telegram: @vps10 & @diegovip7\033[0m"
echo -e "[\033[1;31m-\033[1;33m]\033[1;30m ───────────────────────────────────────\033[1;33m"
sleep 5
echo -e "[\033[1;31m-\033[1;33m]\033[1;30m Preparando Sistema 😋😋\033[1;33m"
function preparar(){
touch /root/usuarios.db
touch /root/badvpn.log
mkdir /etc/VpsPackdir/limite 2>/dev/null
mkdir /etc/VpsPackdir/senha 2>/dev/null
mkdir /etc/VpsPackdir/v 2>/dev/null
mkdir /etc/VpsPackdir/socks 2>/dev/null
rm -rf /etc/VpsPackdir/fecha 2>/dev/null
rm -rf /root/name 2>/dev/null
#
rm /etc/VpsPackdir/socks/s.zip
curl -o /etc/VpsPackdir/socks/s.zip https://raw.githubusercontent.com/lacasitamx/tests/master/s.zip
cd /etc/VpsPackdir/socks/
unzip s.zip
rm /etc/VpsPackdir/socks/s.zip
cd /root
if grep vpspack /etc/ssh/sshd_config; then
echo "vps10 casi listo"
else
cp /etc/VpsPackdir/sshconf /etc/ssh/sshd_config;
service ssh restart
echo "Configurado"
fi
chmod +x /root/dropbear
}
fun_bar 'preparar'
function paquetes(){
echo -e "[\033[1;31m-\033[1;33m]\033[1;30m Instalando Paquetes ✈✈√√√\033[1;33m"
sed -i '/neofetch/d' /etc/apt/sources.list
apt-get update
apt-get -y install nano 1> /dev/null 2> /dev/null
apt-get -y install net-tools 1> /dev/null 2> /dev/null
apt-get -y install iptables 1> /dev/null 2> /dev/null
#apt-get -y install unzip 1> /dev/null 2> /dev/null
apt-get -y install htop 1> /dev/null 2> /dev/null
apt-get -y install curl 1> /dev/null 2> /dev/null
apt-get -y install figlet 1> /dev/null 2> /dev/null
apt-get -y install locate 1> /dev/null 2> /dev/null
#apt-get -y install zip 1> /dev/null 2> /dev/null
apt-get -y install git 1> /dev/null 2> /dev/null
apt-get -y install build-essential libpq-dev libffi-dev zlib1g-dev 1> /dev/null 2> /dev/null
apt-get -y install screen 1> /dev/null 2> /dev/null
apt-get -y install python-pip 1> /dev/null 2> /dev/null
apt-get -y install python3-pip 1> /dev/null 2> /dev/null
apt-get -y install nload 1> /dev/null 2> /dev/null
apt-get -y install dos2unix 1> /dev/null 2> /dev/null
apt-get -y install lsof 1> /dev/null 2> /dev/null
apt-get -y install speedtest-cli 1> /dev/null 2> /dev/null
apt-get -y install openssl libssl-dev pkg-config 1> /dev/null 2> /dev/null
pip install speedtest-cli > /dev/null 2>&1
apt-get remove apache2 -y && apt-get purge apache2 -y 1> /dev/null 2> /dev/null
rm -rf /var/wwww/html/* 1> /dev/null 2> /dev/null
service apache2 stop 1> /dev/null 2> /dev/null
apt-get install apache2 -y 1> /dev/null 2> /dev/null
sed -i 's/Listen 80/Listen 85/g' /etc/apache2/ports.conf 1> /dev/null 2> /dev/null
rm /var/www/html/index.html 1> /dev/null 2> /dev/null
wget -o /dev/null -O- wget https://raw.githubusercontent.com/kirrathmx/dl/master/index.txt > /var/www/html/index.html
cd /root
service apache2 restart 1> /dev/null 2> /dev/null
mkdir /var/www/html/openvpn
apt-get install -y neofetch 1> /dev/null 2> /dev/null
echo -e "[\033[1;31m-\033[1;33m]\033[1;30m 🐞🌲Instalacion Finalizada🐸🐝 √√♬♬\033[1;33m"
}
fun_bar 'paquetes'
iniciarbin
sleep 5
clear
if cat /root/.bashrc | grep vpspack; then
echo -e ":)"
else
echo "clear" >> .bashrc
echo 'cat /etc/VpsPackdir/logo' >> .bashrc
echo 'DATE=$(date +"%d-%m-%y")' >> .bashrc
echo 'TIME=$(date +"%T")' >> .bashrc
echo 'echo -e ""' >> .bashrc
echo 'echo -e "Nombre del Servidor 🙂🐥 : $HOSTNAME"' >> .bashrc
echo 'echo -e "Fecha del Servidor🐴🦉 : $DATE"' >> .bashrc
echo 'echo -e "Hora del Servidor🇦🇷 : $TIME"' >> .bashrc
echo 'echo -e ""' >> .bashrc
echo 'echo -e "Bienvenido! a script vps10"' >> .bashrc
echo 'echo -e "Teclee vpspack para ingresar✏✏🖌."' >> .bashrc
echo 'echo -e ""' >> .bashrc
fi
clear
rm /etc/VpsPackdir/ip &>/dev/null
touch /etc/VpsPackdir/ip
echo "$IP" > /etc/VpsPackdir/ip
cat /etc/VpsPackdir/logo
echo -e "\033[1;32mInstalacion Finalizada\n\033[1;30m"
echo -e "\n\033[1;32mvpspack     \033[1;30mMENU DE OPCIONES"
echo -e "\033[1;32mOpcion 1    \033[1;30mINSTALAR SQUID/SSH"
echo -e "\033[1;32mOpcion 2    \033[1;30mADMINISTRACION DE USUARIOS"
echo -e "\033[1;32mOpcion 8    \033[1;30mPUERTOS HABILITADOS"
echo -e "\033[1;32mOpcion 9    \033[1;30mHERRAMIENTAS"
echo -e "\033[1;32mOpcion 10   \033[1;30mINSTALADORES"
echo -e "\033[1;32m@- \033[1;30mcréditos : pepa pick 🤣🤣 \033[0m"
echo -e "\033[1;32m@- \033[1;31mREV: :bob sponja 🐥🦉\033[0m"
echo -e "\033[1;32m@- \033[1;31mBY TEAM pepa pick 🐴🐑\033[0m"
echo -e "\033[1;32mVersion     \033[1;30m$vpspackversion \033[0m"
echo -e "$fecha" >> /etc/VpsPackdir/fecha
echo -e "\033[1;32m Personalizacion - 🇦🇷 Escribe tu Nick 🇦🇷☆☆:\033[0m"
echo -e "\033[1;32m (Maximo 10 Caracteres)\033[0m"
read -p ": " nickname
echo "$nickname" >> /root/name
cd /root
rm instalavps
vpspack
fi
rm -rf /root/instalavps
