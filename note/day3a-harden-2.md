## build stage in Dockerfile
separate build part and runtime part in Dockerfile.

## docker image size
- Final image size : 158MB  
```
ubuntu@Masashi-SER5:~$ docker images api-hardened:day3a
REPOSITORY     TAG       IMAGE ID       CREATED          SIZE
api-hardened   day3a     7011c860666c   38 minutes ago   158MB
```

## CVE scan result
- TLDR it id not changed

-[expected] Debian package - CRITICAL 0 : HIGH 2  No fixed version (glibc)
- python package - CRITICAL 0 : HIGH 1  : fixed version there (starlette)

the removing build/package tooling reduced 3 CVEs
