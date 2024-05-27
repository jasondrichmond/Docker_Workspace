https://dev.to/rogertorres/first-steps-with-docker-rust-30oi

docker build -t my-rust-image:1.0 .

docker run -d --name my-rust-image -p 22:22 -p 8080:3030 -v c:/docker/volume/rust:/data my-rust-image:1.0