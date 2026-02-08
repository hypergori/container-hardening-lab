## build stage in Dockerfile
separate build part and runtime part in Dockerfile.

## docker image size
- Final image size : 155MB  
- size was a little but reduced.
```aiignore
ubuntu@Masashi-SER5:~$ docker images api-hardened:day3
REPOSITORY     TAG       IMAGE ID       CREATED          SIZE
api-hardened   day3      1f5e3ae86227   24 minutes ago   155MB
```

## CVE scan result
- TLDR it id not changed

- Debian package - CRITICAL 0 : HIGH 2  No fixed version
- python package - CRITICAL 0 : HIGH 2  there are fixed version

Debian image did not change but build stage did not help the CVE reduction
