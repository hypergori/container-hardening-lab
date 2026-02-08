## create distroless image
add user creation, file permission and USER instruction

## docker image size
- Final image size : 86.4MB  
```
ubuntu@Masashi-SER5:~$   docker images api-distroless:day5
REPOSITORY       TAG       IMAGE ID       CREATED              SIZE
api-distroless   day5      00dad7b67c33   About a minute ago   89.1MB
```

## final reports

api-distroless:day5 89.1MB  nonroot by default  HIGH:13  CRITICAL:6
Much smaller image; OS CVEs come from bundled Debian12+Python runtime libs; Python deps had 0 findings


## switching community edition of python-debian distroless image
The result ended with 1 CRITICAL vulnerability

┌─────────┬───────────────┬──────────┬──────────┬───────────────────┬───────────────┬──────────────────────────────────────────────────────────────┐
│ Library │ Vulnerability │ Severity │  Status  │ Installed Version │ Fixed Version │                            Title                             │
├─────────┼───────────────┼──────────┼──────────┼───────────────────┼───────────────┼──────────────────────────────────────────────────────────────┤
│ libc6   │ CVE-2026-0861 │ HIGH     │ affected │ 2.36-9+deb12u13   │               │ glibc: Integer overflow in memalign leads to heap corruption │
│         │               │          │          │                   │               │ https://avd.aquasec.com/nvd/cve-2026-0861                    │
└─────────┴───────────────┴──────────┴──────────┴───────────────────┴───────────────┴──────────────────────────────────────────────────────────────┘


