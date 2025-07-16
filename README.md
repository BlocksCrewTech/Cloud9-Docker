Blockscrew Cloud9

Penjelasan singkat Cloud9

Fitur :
blockscrew/cloud9:latest
- Memiliki size image yang sangat kecil
- Depedensi masih kosong
- Bisa disesuaikan depedensi apa saja yang mau diinstall

blockscrew/cloud9:v2
- Siap dipakai, sudah tersedia banyak dependensi seperti python2, python3, python3-pip, nvm, nodejs v24 terbaru, npm v11 terbaru
- Bisa disesuaikan depedensi apa saja yang mau diinstall

# sudo apt update && upgrade
# sudo apt install -y docker.io docker-compose
# sudo systemctl enable --now docker

# sudo ufw allow 22/tcp
# sudo ufw allow 8181
# sudo ufw enable
# sudo ufw reload

# mkdir -p ~/cloud9 && cd ~/cloud9

Buat docker-compose-latest.yml
//
services:
  cloud9:
    image: blockscrew/cloud9:latest
    container_name: cloud9
    environment:
      - TZ=Asia/Jakarta
      - USERNAME=user	# Buat username kamu bebas
      - PASSWORD=pass	# Buat password kamu bebas
    volumes:
      - ~/cloud9:/BOT
    ports:
      - 8181:8000	# Port 8181 bisa custom sesuai keinginan
    restart: always
//

atau docker-compose-v2.yml
//
services:
  cloud9:
    image: blockscrew/cloud9:v2
    container_name: cloud9
    environment:
      - TZ=Asia/Jakarta
      - USERNAME=user	# Buat username kamu bebas
      - PASSWORD=pass	# Buat password kamu bebas
    volumes:
      - ~/cloud9:/BOT
    ports:
      - 8181:8000	# Port 8181 bisa custom sesuai keinginan, PORT DEFAULT CONTAINER 8000 (tidak bisa diganti!)
    restart: always
//

Jalankan compose
# docker-compose up -d

Tunggu 1-3 menit sedang proses pembuatan docker cloud9

Cek di browser dengan format http://IP:PORT misalnya http:127.0.0.1:8181

Source image docker : https://hub.docker.com/r/blockscrew/cloud9



Di dalam cloud9 (browser)
# sudo su
# apt-get update
# apt-get upgrade
# apt-get install -y htop
# htop

Install nodejs dan npm versi terbaru
# sudo su
# curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
# source ~/.bashrc
# nvm --version
# nvm ls-remote
# nvm install 24
# nvm alias default 24
# nvm use default

Install python2 python3
# apt-get install python2 python3
# apt-get install pip
