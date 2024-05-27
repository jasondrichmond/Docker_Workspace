docker pull a11ywatch/a11ywatch

# create the bridge network for front-end and backend
docker network create --driver bridge a11ywatch-net

# start the backend
docker run -p 3280:3280 -v d:/docker/volumes/a11ywatch:/a11ywatch/conf --network a11ywatch-net --name a11ywatch-backend -e SUPER_MODE=true a11ywatch/a11ywatch:latest

# start the frontend
docker run -p 3000:3000 -v d:/docker/volumes/a11ywatch:/a11ywatch/conf --network a11ywatch-net --name a11ywatch-frontend -e SUPER_MODE=true a11ywatch/web