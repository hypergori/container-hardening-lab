## create distroless image
 
## Docker file
Dockerfile.debian13


## trivy report summary
api-debian13:day6 (debian 13.3)

Total: 1 (HIGH: 1, CRITICAL: 0)

┌─────────┬───────────────┬──────────┬──────────┬───────────────────┬───────────────┬──────────────────────────────────────────────────────────────┐
│ Library │ Vulnerability │ Severity │  Status  │ Installed Version │ Fixed Version │                            Title                             │
├─────────┼───────────────┼──────────┼──────────┼───────────────────┼───────────────┼──────────────────────────────────────────────────────────────┤
│ libc6   │ CVE-2026-0861 │ HIGH     │ affected │ 2.41-12+deb13u1   │               │ glibc: Integer overflow in memalign leads to heap corruption │
│         │               │          │          │                   │               │ https://avd.aquasec.com/nvd/cve-2026-0861                    │
└─────────┴───────────────┴──────────┴──────────┴───────────────────┴───────────────┴──────────────────────────────────────────────────────────────┘

Python (python-pkg)

Total: 1 (HIGH: 1, CRITICAL: 0)

┌──────────────────┬────────────────┬──────────┬────────┬───────────────────┬───────────────┬──────────────────────────────────────────────────────┐
│     Library      │ Vulnerability  │ Severity │ Status │ Installed Version │ Fixed Version │                        Title                         │
├──────────────────┼────────────────┼──────────┼────────┼───────────────────┼───────────────┼──────────────────────────────────────────────────────┤
│ wheel (METADATA) │ CVE-2026-24049 │ HIGH     │ fixed  │ 0.46.1            │ 0.46.2        │ wheel: wheel: Privilege Escalation or Arbitrary Code │
│                  │                │          │        │                   │               │ Execution via malicious wheel file...                │
│                  │                │          │        │                   │               │ https://avd.aquasec.com/nvd/cve-2026-24049           │
└──────────────────┴────────────────┴──────────┴────────┴───────────────────┴───────────────┴──────────────────────────────────────────────────────┘