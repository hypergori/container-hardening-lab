## 1. Create first docker image with app
Just using python:3.10-slim as base image and build fastAPI hello-world app

## 2. Scan CVEs by trivy
scan by trivy  
Result is size 162MB, run as root  
debian layer is largest then python packages and python runtime layer  

debian package - CRITICAL:0 , HIGH 2  
python package - CRITICAL:0 , HIGH 4  

## 3. Separate builder and runtime stage, then remove build tool
This succeded to remove 3 HIGH CVEs from python side

Debian package - CRITICAL:0 : HIGH 2  No fixed version (glibc)  
python package - CRITICAL:0 : HIGH 1  fixed version there (starlette)

## 3a. upgrade the fastAPI
fastapi==0.125 then last python CVE is gone

Debian package - CRITICAL:0 : HIGH 2  No fixed version (glibc)  
python package - CRITICAL:0 : HIGH 0  

## 4. run as non-root and readonly mode
create non-root appuser  in runtime stage and confirm by whoami

```aiignore
docker run --rm -p 8000:8000 --read-only --tmpfs /tmp api-distroless:day5
```

## 5. debian distro-less image
use community version of distroless debian-python image

Debian package - CRITICAL:0 : HIGH 1  No fixed version (glibc)  
python package - CRITICAL:0 : HIGH 0

[Dockerfile.distroless](Dockerfile.distroless)

api-hardened:day5 (debian 12.13)
================================
Total: 1 (HIGH: 1, CRITICAL: 0)

┌─────────┬───────────────┬──────────┬──────────┬───────────────────┬───────────────┬──────────────────────────────────────────────────────────────┐  
│ Library │ Vulnerability │ Severity │  Status  │ Installed Version │ Fixed Version │                            Title                             │  
├─────────┼───────────────┼──────────┼──────────┼───────────────────┼───────────────┼──────────────────────────────────────────────────────────────┤  
│ libc6   │ CVE-2026-0861 │ HIGH     │ affected │ 2.36-9+deb12u13   │               │ glibc: Integer overflow in memalign leads to heap corruption │  
│         │               │          │          │                   │               │ https://avd.aquasec.com/nvd/cve-2026-0861                    │  
└─────────┴───────────────┴──────────┴──────────┴───────────────────┴───────────────┴──────────────────────────────────────────────────────────────┘  
