BalenaEtcher https://etcher.balena.io
もしくはrufus
新しいパソコンはGPT UEFIにする

ubuntu https://ubuntu.com/download
UEFI ORICO UFSD
try or install ubuntu
MobaXterm：https://mobaxterm.mobatek.net

sudo apt install openssh-server
sudo -i
apt install curl
#一键安装CasaOS
curl -fsSL https://get.casaos.io | sudo bash
#CasaOS第三方应用源
https://play.cuse.eu.org/Cp0204-AppStore-Play.zip

curl -fsSL https://opencode.ai/install | bash
source /root/.bashrc

#Ollama 官方版 Docker Compose 配置

version: '3.8'

services:
  ollama:
    image: ollama/ollama:latest
    container_name: ollama
    restart: always
    ports:
      - "11434:11434"
    volumes:
      - /DATA/AppData/ollama:/root/.ollama
    environment:
      - TZ=Asia/Shanghai
      - OLLAMA_HOST=0.0.0.0:11434
      - OLLAMA_ORIGINS=*
      - OLLAMA_VULKAN=1
    devices:
      - /dev/dri:/dev/dri


图像识别模型：moondream:latest

嵌入向量模型：mxbai-embed-large:latest