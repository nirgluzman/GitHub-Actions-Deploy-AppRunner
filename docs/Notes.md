## Overview
- Code base - React app (default created with `create-react-app`).
- docker-compose for start dev server and run tests.
- Production - multi-stage Dockerfile - build React artifacts and start Nginx server.
- GitHub Actions workflow - run tests and deploy to AWS AppRunner.

## GitHub repo

https://github.com/nirgluzman/GitHub-Actions-Deploy-AppRunner.git

## WSL and Windows Users Must Read !!

https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide/learn/lecture/18799500#questions/21483842

- When using WSL to run Docker Desktop on Windows, the project should have been created on the Linux file system and all docker commands should be run within WSL as per best practices:

https://docs.docker.com/desktop/windows/wsl/#best-practices

## Nginx

https://hub.docker.com/_/nginx

- Open source reverse proxy server.

- Hosting some simple static content:

```bash
docker run --name some-nginx -v /some/content:/usr/share/nginx/html:ro -d nginx
```

## Multi-stage builds

https://docs.docker.com/build/building/multi-stage/

- With multi-stage builds, you use multiple `FROM` statements in your Dockerfile.
- Each `FROM` instruction can use a different base, and each of them begins a new stage of the build.
- You can selectively copy artifacts from one stage to another, leaving behind everything you don't want in the final image.

## Docker bind mounts

https://stackoverflow.com/questions/41485217/mount-current-directory-as-a-volume-in-docker-on-windows-10

```bash
docker build -f Dockerfile.dev -t react-app-image .
docker run -p 3000:3000 -v /home/node/app/node_modules -v $(pwd):/home/node/app --name react-app-container react-app-image
```

## docker attach

- Attach local standard input, output, and error streams to the PRIMARY PROCESS (PID=1) running in the container.

- This lets you view its output or control it interactively, as though the commands were running directly in your terminal.

## docker exec

- executes a new command in a running container.

```bash
docker exec -it <container-name> sh
```
