To get started, either clone or download the project as a ZIP file to your local machine.


 git clone https://github.com/docker/getting-started-todo-app
And after the project is cloned, navigate into the new directory created by the clone:


   ```bash
 cd getting-started-todo-app
```
Build the project by running the following command, swapping out DOCKER_USERNAME with your username.

 ```bash
 docker build -t DOCKER_USERNAME/getting-started-todo-app .
 ```
For example, if your Docker username was mobydock, you would run the following:

 ```bash
 docker build -t mobydock/getting-started-todo-app .
 ```
To verify the image exists locally, you can use the docker image ls command:


 docker image ls
You will see output similar to the following:


REPOSITORY                          TAG       IMAGE ID       CREATED          SIZE
mobydock/getting-started-todo-app   latest    1543656c9290   2 minutes ago    1.12GB
...
To push the image, use the docker push command. Be sure to replace DOCKER_USERNAME with your username:


 docker push DOCKER_USERNAME/getting-started-todo-app
Depending on your upload speeds, this may take a moment to push.
