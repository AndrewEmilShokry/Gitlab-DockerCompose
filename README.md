# Gitlab-DockerCompose



Installing Gitlab Using Docker Compose on Ubuntu



# first install docker-compose on your ubuntu machine


1-sudo apt install curl


2-sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose


3-chmod +x /usr/local/bin/docker-compose


4-docker-compose --version    //the output should be >> docker-compose version 1.29.2, build 5becea4c



# install Gitlab on docker compose



1- mkdir gitlab



2- export GITLAB_HOME=$(pwd)/gitlab 


3-go to gitlab directory then create nano docker-compose.yml file with the following content in Docker-Compose.yml.txt



4- docker-compose up -d



5-docker exec -it gitlab-ce grep 'Password:' /etc/gitlab/initial_root_password



6-launch your gitlab http://localhost:8080/admin/runners and click the Copy token button



7-then use this command docker exec -it gitlab-runner gitlab-runner register --url "http://gitlab-ce" --clone-url "http://gitlab-ce"



8-The module provides the following information:

Enter the GitLab instance URL: confirm the entered value (click enter)
Enter the registration token: enter the token copied before.
Enter a description for the runner: enter the name of the runner, e.g. docker-runner
Enter tags for the runner: leave the field blank here
Enter an executor: enter docker here
Enter the default Docker image: here we provide the default docker image, e.g. maven: latest



