# 3Dogs harness attestations

This repository publishes the SHA-256 fingerprints of 3Dogs Nexus harness files *before* those files go live. Later, anyone can check that what was installed is exactly what was reviewed. No source code is published here.

Each entry gives four things for each file:
- the file name
- its size in bytes
- its SHA-256
- its git blob id (the output of `git hash-object`)

To check a copy of a file, run `sha256sum <file>` and `git hash-object <file>`. Both must print the values listed below. The `.sha256` file next to each entry also works with `sha256sum -c`.

## 2026-11-09: lockgate part 1 (harness-fix Job 2)

- **Why:** the 3Dogs committee's decision #2589 (9 Nov 2026, APPROVE WITH CHANGES), condition 3, requires the fingerprints of these three modules to be published outside the build server before they are installed.
- **Source:** taken from the staged files at 2026-11-09 22:10:48 UTC.
- **Status:** staged, not installed.

| File | Bytes | SHA-256 | Git blob id |
|---|---|---|---|
| `locked_test_gate.py` | 40008 | `630747f57f29a2212af05c96549977d0170a3a9163cd3032ec23f36f8c9f85f5` | `04b51877968d4d62f4367d9a0ce52a318a095542` |
| `gatehard.py` | 7432 | `0c1e5a42356535df29cc4129cea6fb963af806cbd23326751d1003e047debc9a` | `da6b4fd3a1cc17aec404439e4eaa7ef4c1e20f31` |
| `foreman.py` (patched) | 203430 | `5721b00e252fcdbfd2d7440774b2325d7e60859450062fa6412cd22db55d3be7` | `9379c4884b2fcbe0ec4e6bb73c3d698441e6570e` |

Machine-readable copy: [`2026-11-09-lockgate-part1.sha256`](2026-11-09-lockgate-part1.sha256).

The install commit id will be added to this entry once the files are installed.
