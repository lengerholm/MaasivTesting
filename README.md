1: Retrieve Jenkins Docker Image
'docker pull jenkins/jenkins'

2: Move Dockerfile and jenkins.yaml to host
WinSCP or similar tool

3: Build Docker Image
'sudo docker build -t jenkins .'

4: Run container with docker.sock mounted
'sudo docker run -d --name jenkins \
--privileged \
--restart=on-failure \
-p 8080:8080 -p 50000:50000 \
-v /var/run/docker.sock:/var/run/docker.sock \
jenkins'

5: Get Jenkins default password
'sudo docker logs [CONTAINER ID]'

6: Give Jenkins docker.sock permission (Run in host)
'sudo chmod 666 /var/run/docker.sock'

7: Setup Jenkins

- Go to IPADDRESS:8080
- Install suggested plugings
- Create Account

8: Create Pipeline

- New item
- Maasiv CICD
- Pipeline
- Copy pipeline script
