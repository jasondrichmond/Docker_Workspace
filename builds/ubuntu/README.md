docker build . -t my-ubuntu-image

docker run -it -d -p 22:22 -p 3000:3000 -v "C:\Docker\volume\ubuntu:/app" --name my-ubuntu-image my-ubuntu-image
