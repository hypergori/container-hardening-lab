## Base image
python:3.10-slim
## docker image size
- Final image size : 162MB
## layers
- debian : 78.6MB
- pip uvicorn/fastAPI packages : 40.2MB
- python layer : 39.4MB
## run as root
yes
## python version
Python 3.10.19
## Observation
THe largest image is debian, then python packages then python itself

```
PS C:\Users\hyper\IdeaProjects\container-hardening-lab> docker history  api-original:day1                                                                                                                                                            
IMAGE          CREATED          CREATED BY                                      SIZE      COMMENT
1241ef2a469b   12 minutes ago   CMD ["uvicorn" "main:app" "--host" "0.0.0.0"…   0B        buildkit.dockerfile.v0
<missing>      12 minutes ago   EXPOSE map[8000/tcp:{}]                         0B        buildkit.dockerfile.v0
<missing>      12 minutes ago   COPY app/ . # buildkit                          589B      buildkit.dockerfile.v0
<missing>      12 minutes ago   RUN /bin/sh -c pip install --no-cache-dir -r…   40.2MB    buildkit.dockerfile.v0
<missing>      13 minutes ago   COPY app/requirements.txt . # buildkit          43B       buildkit.dockerfile.v0
<missing>      13 minutes ago   WORKDIR /app                                    0B        buildkit.dockerfile.v0
<missing>      3 days ago       CMD ["python3"]                                 0B        buildkit.dockerfile.v0
<missing>      3 days ago       RUN /bin/sh -c set -eux;  for src in idle3 p…   36B       buildkit.dockerfile.v0
<missing>      3 days ago       RUN /bin/sh -c set -eux;   savedAptMark="$(a…   39.4MB    buildkit.dockerfile.v0
<missing>      3 days ago       ENV PYTHON_SHA256=c8f4a596572201d81dd7df91f7…   0B        buildkit.dockerfile.v0
<missing>      3 days ago       ENV PYTHON_VERSION=3.10.19                      0B        buildkit.dockerfile.v0
<missing>      3 days ago       ENV GPG_KEY=A035C8C19219BA821ECEA86B64E628F8…   0B        buildkit.dockerfile.v0
<missing>      3 days ago       RUN /bin/sh -c set -eux;  apt-get update;  a…   3.81MB    buildkit.dockerfile.v0
<missing>      3 days ago       ENV LANG=C.UTF-8                                0B        buildkit.dockerfile.v0
<missing>      3 days ago       ENV PATH=/usr/local/bin:/usr/local/sbin:/usr…   0B        buildkit.dockerfile.v0
<missing>      5 days ago       # debian.sh --arch 'amd64' out/ 'trixie' '@1…   78.6MB    debuerreotype 0.17
```