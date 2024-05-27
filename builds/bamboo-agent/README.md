docker run -d --name bambooAgent -p 80:80 -e BAMBOO_SERVER=http://bamboo.mycompany.com/agentServer/ -v d:/docker/volumes/jenkins:/var/atlassian/application-data/bamboo atlassian/bamboo-agent-base
