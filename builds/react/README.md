docker build . -t my-react-image

curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash

docker run -it -d -p 22:22 -p 3000:3000 -v "C:\Docker\volume\ubuntu:/app" --name my-react-image my-react-image
