## WSL and Windows Users Must Read !!

https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide/learn/lecture/18799500#questions/21483842

- When using WSL to run Docker Desktop on Windows, the project should have been created on the Linux file system and all docker commands should be run within WSL as per best practices:

https://docs.docker.com/desktop/windows/wsl/#best-practices

## Docker bind mounts

https://stackoverflow.com/questions/41485217/mount-current-directory-as-a-volume-in-docker-on-windows-10

```bash
docker build -f Dockerfile.dev -t react-app-image .
docker run -p 3000:3000 -v /home/node/app/node_modules -v $(pwd):/home/node/app --name react-app-container react-app-image
```
