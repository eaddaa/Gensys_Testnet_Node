# Gensys_Testnet_Node

# 🛠️ RL-Swarm Kurulum Rehberi 
Önce sistem paketlerini güncelleyelim ve gerekli araçları kuralım:

````
sudo apt-get update && sudo apt-get upgrade -y

sudo apt install screen curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip -y
``````
# 🐍 Python Kurulumu

``````
sudo apt-get install python3 python3-pip python3-venv python3-dev -y
``````

# ⚙️ Node.js Kurulumu (2 yöntemden biri seçilebilir)
Yöntem 1: Resmi Nodesource üzerinden
``````
sudo apt-get update
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash -
sudo apt-get install -y nodejs
node -v
sudo npm install -g yarn
yarn -v
``````
Yöntem 2: Otomatik kurulum scripti (Alternatif)

``````
curl -sSL https://raw.githubusercontent.com/zunxbt/installation/main/node.sh | bash
``````

# 📦 Ek Bağımlılıkları Kur


``````
sudo apt update && sudo apt install -y python3 python3-venv python3-pip curl screen git yarn
``````
Eğer yarn eklenmemişse:

``````
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt update && sudo apt install -y yarn
``````

#  🔄 rl-swarm Repoyu Klonla

``````
rm -rf rl-swarm && git clone https://github.com/zunxbt/rl-swarm.git && cd rl-swarm
``````

# 🖥️ screen Oluştur

``````
screen -S gensyn
``````

# 🚀 Projeyi Çalıştır

``````
python3 -m venv .venv
source .venv/bin/activate
./run_rl_swarm.sh
``````

# 📩 Giriş Yapmak için E-Postanı Kullan
Terminal size bir bağlantı (URL) verecek. Tarayıcıda açarak giriş yapın.
OTP (şifre) e-postanıza gelmezse, aşağıdaki adımları uygulayın:

# 🧠 Ngrok Kurulumu (Alternatif Erişim için)

``````
wget https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-amd64.tgz
tar -xvzf ngrok-v3-stable-linux-amd64.tgz
sudo mv ngrok /usr/local/bin/
``````
Ardından: https://ngrok.com adresine gidin.

Üye olun ve giriş yapın.

Authtoken kısmına gidin, token'ınızı kopyalayın.

VPS terminalinize yapıştırın
Daha sonra: Ngrok bağlantısı oluşturulacak. Çıkan URL'yi tarayıcıda açarak giriş yapın.
``````
ngrok http 3000
``````

✅ Giriş Yapıldıktan Sonra
Terminalde şunu göreceksiniz:
``````
userData.json found. Proceeding...
``````
Son olarak şu soru gelecek:
``````
Would you like to push models you train in the RL swarm to the Hugging Face Hub? [y/N]
``````
Burada n yazıp Enter'a basın.
Her şey başarılıysa, artık RL Swarm çalışıyor olacaktır 🎉

Sorun oluşursa baştan kur.
🔁 Baştan Kurulum (RAM Sorunu Göz Önüne Alınarak)
1️⃣ Projeyi Temizle ve Yeniden Klonla

``````
rm -rf rl-swarm
git clone https://github.com/zunxbt/rl-swarm.git
cd rl-swarm
``````
``````
screen -S gensyn
python3 -m venv .venv
source .venv/bin/activate
./run_rl_swarm.sh
``````
Return:
``````
screen -r swarm
``````
Stop and Kill:
``````
screen -XS swarm quit
``````
Node ID bul
Telegram’daki @gensyntrackbot üzerinden Node ID’n’in bir EVM cüzdan adresiyle (CA) eşleşip eşleşmediğini kontrol et.
Eğer eşleşmemişse, şu adımları takip et:

``````
rl-swarm/modal-login/tempdata/ klasöründeki kullanıcı verilerini sil.
``````
Bu klasördeki iki dosyayı da tamamen sil.

Swarm'ı yeniden çalıştır.

Bu sefer farklı bir e-posta adresiyle giriş yap.

Bu işlem, Node ID'ni yeni bir EVM adresine bağlamana yardımcı olur.

💾 Sanal RAM (Swap) Artırımı

# 20 GB swap için
``````
sudo fallocate -l 20G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
``````
🔧 Swap Durumunu Kontrol Et
``````
free -h
``````
``````
htop
``````

🚫 Swap’i Geçici Olarak Kapatmak
``````
sudo swapoff -a
``````
❌ Swap’i Kalıcı Olarak Kapatmak
fstab dosyasını düzenle:
İçinde şu satırı bul:
``````
/swapfile none swap sw 0 0
``````
Bu satırın başına # koyarak yorum satırı yap (veya tamamen sil):
``````
# /swapfile none swap sw 0 0
``````
Dosyayı kaydet ve çık
Swap’i tekrar kapat:
``````
sudo swapoff -a
``````
🧹 (İsteğe Bağlı) Swap Dosyasını Tamamen Silmek
Eğer swap dosyasına artık hiç ihtiyacın olmayacaksa:
``````
sudo rm /swapfile
``````
