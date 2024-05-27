docker build . -t hardhat

wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
source ~/.bashrc
nvm install 20

docker run -it -d -p 22:22 -p 8545:8545 -v "C:\Docker\volume\hardhat:/app" --name hardhat hardhat
