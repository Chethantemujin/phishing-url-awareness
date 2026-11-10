# Test Results

Python version used: 3.13 | Operating system: Windows | Date: 2026-11-10

| # | Input | Expected result | Actual result | Pass/Fail |
|---|-------|-----------------|---------------|-----------|
| 1 | https://www.example.com/login | No listed warning signs | No listed warning signs found. This does NOT prove safety. | PASS |
| 2 | http://192.0.2.10/account | IP address + HTTP | Uses an IP address instead of a familiar domain. / Uses HTTP. HTTPS alone does not prove trust. / REVIEW CAREFULLY: 2 warning sign(s) found. | PASS |
| 3 | http://example.com@sample.invalid/login | @ symbol + HTTP | Contains an @ symbol; inspect carefully. / Uses HTTP. HTTPS alone does not prove trust. / REVIEW CAREFULLY: 2 warning sign(s) found. | PASS |
| 4 | https://a.b.c.d.e.example.invalid/path | Many hostname segments | Contains many hostname segments/subdomains. / REVIEW CAREFULLY: 1 warning sign(s) found. | PASS |
| 5 | https://xn--example.invalid/ | Punycode-style hostname | Contains a punycode-style hostname. / REVIEW CAREFULLY: 1 warning sign(s) found. | PASS |

## Notes

All five tests passed after the four improvements were added, so the loop, summary, reasons and error handling did not break the original checks.
A link with no warning signs is still not proof of safety, because a cleverly spelled name can slip through.
Typing http://[bad used to crash the program with a ValueError; the try/except fix now handles it safely.
