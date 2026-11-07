### Install

apt update && apt install -y linux-headers-$(uname -r) gnupg

gpg --keyserver keyserver.ubuntu.com --recv-keys 75c9dd72c799870e310542e24166f2c257290828
gpg --export 75c9dd72c799870e310542e24166f2c257290828 > /usr/share/keyrings/amnezia.gpg

cat > /etc/apt/sources.list.d/amnezia.sources <<EOF
Types: deb
URIs: https://ppa.launchpadcontent.net/amnezia/ppa/ubuntu
Suites: focal
Components: main
Signed-By: /usr/share/keyrings/amnezia.gpg
EOF

apt update && apt install -y amneziawg

wget https://raw.githubusercontent.com/MagoBuono/awgctl/main/awgctl -O /usr/local/sbin/awgctl
chmod +x /usr/local/sbin/awgctl

### Run
AWG_PORT=51820 AWG_NET=10.111.3 awgctl init
awgctl create user1
