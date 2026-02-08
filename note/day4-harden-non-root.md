## create non-root user and run as 
add user creation, file permission and USER instruction

## docker image size
- Final image size : 158MB  
```
ubuntu@Masashi-SER5:~$ docker images api-hardened:day3a
REPOSITORY     TAG       IMAGE ID       CREATED         SIZE
api-hardened   day4      5b93c66a16d3   8 minutes ago   158MB
```
## running as non-root
```
docker run --rm -p 8000:8000 --read-only --tmpfs /tmp  api-hardened:day4 whoami  
appuser

docker run --rm -p 8000:8000 --read-only --tmpfs /tmp  api-hardened:day4 id    
uid=10001(appuser) gid=10001(appuser) groups=10001(appuser)
```
## readonly mode still works
```
docker run --rm -p 8000:8000 --read-only --tmpfs /tmp api-hardened:day4