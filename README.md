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
- **Status:** installed 2026-11-09 22:45:27-22:45:30 UTC under decision #2613, with both new switches in shadow mode. After the install, the live files were re-hashed, and all three match this table (SHA-256 and git blob id).

| File | Bytes | SHA-256 | Git blob id |
|---|---|---|---|
| `locked_test_gate.py` | 40008 | `630747f57f29a2212af05c96549977d0170a3a9163cd3032ec23f36f8c9f85f5` | `04b51877968d4d62f4367d9a0ce52a318a095542` |
| `gatehard.py` | 7432 | `0c1e5a42356535df29cc4129cea6fb963af806cbd23326751d1003e047debc9a` | `da6b4fd3a1cc17aec404439e4eaa7ef4c1e20f31` |
| `foreman.py` (patched) | 203430 | `5721b00e252fcdbfd2d7440774b2325d7e60859450062fa6412cd22db55d3be7` | `9379c4884b2fcbe0ec4e6bb73c3d698441e6570e` |

Machine-readable copy: [`2026-11-09-lockgate-part1.sha256`](2026-11-09-lockgate-part1.sha256).

Published as release [`lockgate-part1-20261109`](https://github.com/DKJager/3dogs-attestations/releases/tag/lockgate-part1-20261109) on 2026-11-09 at 22:30:35 UTC, before the install.

Install commits in the build server's harness repository:

| File | Install commit |
|---|---|
| `locked_test_gate.py` | `75411c64bb90ba018ffd22cd9ca1b8aff68c202f` |
| `gatehard.py` | `b83d30fe1a42e007a4b9ead238d10eaa78eaf340` |
| `foreman.py` | `53ab82c4e09ffffd0ae492f2ea575c248f9c7ab5` |
| install log (retention units, sealed audit log) | `a671bbfa538cfb01eb97746efc990f31da7b7aa7` |

## 2026-11-10: foreman.py, TESTS1LINE fix (harness-fix Job 2)

- **Decision:** 3Dogs committee #2625 (APPROVE WITH CHANGES).
- **Installed:** 2026-11-10 00:14:03 UTC. The TESTS1LINE switch stays in shadow mode.
- **Replaces:** the `foreman.py` from the lockgate part 1 entry above (SHA-256 `5721b00e252fcdbfd2d7440774b2325d7e60859450062fa6412cd22db55d3be7`).
- **Recorded after the install**, from the live file and the install commit.

| File | Bytes | SHA-256 | Git blob id | Install commit |
|---|---|---|---|---|
| `foreman.py` | 203640 | `7653eb4e755648d4786e68360d3d1be34d09a2085a4802c71418373046a1fbed` | `e457489feddd07d06a975471914e001058a90586` | `d605bccfe7a53109c884093da91f0458d6791f45` |

Machine-readable copy: [`2026-11-10-foreman-tests1line.sha256`](2026-11-10-foreman-tests1line.sha256).

## 2026-11-10: foreman.py, tamper logging and final lock check (harness-fix Job 2)

- **Decision:** 3Dogs committee #2627 (APPROVE WITH CHANGES).
- **Installed:** 2026-11-10 00:55:35 UTC.
- **Replaces:** the `foreman.py` from the TESTS1LINE entry above (SHA-256 `7653eb4e755648d4786e68360d3d1be34d09a2085a4802c71418373046a1fbed`).
- **What changed:** the tamper alarm is now logged before the harness acts on it, and the test-lock final check runs on every exit.
- **Recorded after the install**, from the live file and the install commit.

| File | Bytes | SHA-256 | Git blob id | Install commit |
|---|---|---|---|---|
| `foreman.py` | 205394 | `b54067758baf33f79e6cbff662920e6ca0d891f6bc325594bdaf04e2dcd60e62` | `414b6533310821ddbd62a2435ab09a39905654b4` | `4400f092e2817320747690e848c18cb34fae9127` |

Machine-readable copy: [`2026-11-10-foreman-2627.sha256`](2026-11-10-foreman-2627.sha256).
