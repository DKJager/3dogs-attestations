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

## 2026-11-10: foreman.py, alert-coalescing window fix (harness-fix Job 2)

- **Decision:** 3Dogs committee #2630 (APPROVE).
- **Installed:** 2026-11-10 01:21:07 UTC. The switch stays in shadow mode.
- **Replaces:** the `foreman.py` from the #2627 entry above (SHA-256 `b54067758baf33f79e6cbff662920e6ca0d891f6bc325594bdaf04e2dcd60e62`).
- **What changed:** the alert-coalescing window now defaults to 300 s and is clamped to 0-300 s, and dead shadow code was removed.
- **Recorded after the install**, from the live file and the install commit.

| File | Bytes | SHA-256 | Git blob id | Install commit |
|---|---|---|---|---|
| `foreman.py` | 205272 | `0691c099c5c826a851919ea187e9facf5d7f189d970113f57dc0d01f5ecebaf0` | `18bb63126feeea74273886f64e53823a1a8d9090` | `3b37b6f8aa4fb523fc8644a4717d1c1fe705cea9` |

Machine-readable copy: [`2026-11-10-foreman-2630.sha256`](2026-11-10-foreman-2630.sha256).

## 2026-11-10: locked_test_gate.py, safer retention command line and audit checksum (harness-fix Job 2)

- **Why published now:** decision #2589 requires every new fingerprint of this module to be published before it is installed. The change carries out 3Dogs committee decisions #2619 and #2617 (change 2).
- **Status:** staged, not installed. Published 2026-11-10 at about 01:48 UTC. The install commit will be added to this entry once it is installed.
- **Replaces:** the `locked_test_gate.py` from the lockgate part 1 entry above (SHA-256 `630747f57f29a2212af05c96549977d0170a3a9163cd3032ec23f36f8c9f85f5`).
- **What changes:**
  - the command line does a dry run by default;
  - live retention runs only with an explicit flag plus an environment switch;
  - the audit log is sealed again after its first write;
  - an audit-log checksum is recorded hourly.

| File | Bytes | SHA-256 | Git blob id |
|---|---|---|---|
| `locked_test_gate.py` | 48924 | `82216fd9b20913c6d64ebdbddd9230a38bfe9dbb973a462e36e25cfc7aa74a7a` | `141f0f9e28e718653dbd1fc0df56ad3e9d5e5314` |

Machine-readable copy: [`2026-11-10-locked-test-gate-2619.sha256`](2026-11-10-locked-test-gate-2619.sha256).

## 2026-11-10: foreman.py, path-normalisation fix (harness-fix Job 2)

- **Decision:** 3Dogs committee #2631 (APPROVE WITH CHANGES; the required de-duplication is included).
- **Installed:** 2026-11-10 02:09:59 UTC. The switch stays in shadow mode.
- **Replaces:** the `foreman.py` from the #2630 entry above (SHA-256 `0691c099c5c826a851919ea187e9facf5d7f189d970113f57dc0d01f5ecebaf0`).
- **Recorded after the install**, from the live file and the install commit.

| File | Bytes | SHA-256 | Git blob id | Install commit |
|---|---|---|---|---|
| `foreman.py` | 205435 | `5085d823ed6953c8ba7e9a848b4df3b9420128962aeadca8b2dccd69f446f0c0` | `ba2519afcd3e22cf869bb1863e4a8a61113e2aee` | `1f9b87d3b981264f040dba5923f04e291bde0ee3` |

Machine-readable copy: [`2026-11-10-foreman-2631.sha256`](2026-11-10-foreman-2631.sha256).

## 2026-11-10: foreman.py, contract-extras fix (harness-fix Job 2)

- **Decision:** 3Dogs committee #2647 (with #2646). Installed 2026-11-10 03:40:26 UTC; the switch stays in shadow mode.
- **Replaces:** the `foreman.py` from the #2631 entry above (SHA-256 `5085d823ed6953c8ba7e9a848b4df3b9420128962aeadca8b2dccd69f446f0c0`).
- **Recorded after the install**, from the install commit.

| File | Bytes | SHA-256 | Git blob id | Install commit |
|---|---|---|---|---|
| `foreman.py` | 206531 | `d691a27f4574e80869985fd74afea37fb980073c7f9031e837ab0450d5594d36` | `7c5a0cf8db9cc273e367d296478f36d7bec0fde8` | `4c6b6c5e64f13a1a0d47129cf9e30fbff5e4dc1e` |

## 2026-11-10: foreman.py, judge-skip fix (harness-fix Job 2)

- **Decision:** 3Dogs committee #2645 (with #2643 and design #2636). Installed 2026-11-10 03:40:32 UTC, six seconds after the entry above; the switch stays in shadow mode.
- **Replaces:** the contract-extras `foreman.py` directly above.
- **Recorded after the install**, from the live file and the install commit.

| File | Bytes | SHA-256 | Git blob id | Install commit |
|---|---|---|---|---|
| `foreman.py` | 210089 | `d52567c7f8b43666efa7b099ee582728db3110c633ec853c8fb3eecb6348f524` | `57985edc922175e5f6f77a6db2e168ff93d91a03` | `4f1fd6cdc582263a509d54b9438a23a56f88f1f5` |

Machine-readable copies: [`2026-11-10-foreman-2647.sha256`](2026-11-10-foreman-2647.sha256) and [`2026-11-10-foreman-2645.sha256`](2026-11-10-foreman-2645.sha256).

## 2026-11-11: pin tool, three more figures in the line-coverage report (RSI loop, lane T)

- **Decision:** 3Dogs committee #2748 (APPROVE WITH CHANGES), on the plan #2743 and the promote #2745. Change 1 of #2748 requires these fingerprints to be published outside the build server before the install.
- **Status:** installed. Published 2026-11-11 17:52 UTC. Installed 2026-11-11 18:22:38 UTC, finished 18:22:50 UTC; the check after the install passed (result below). No loop switch was turned on.
- **What changes:** the pin tool's report gets three more entries in its `lines` block (the reachable lines, the functions never entered that do file or process work, and the missed lines). The four existing entries and everything else in the report stay as they are, and no executed count changes. Files only: no loop switch, no change to the pin set.
- **Replaces:** `runner.py`, `SPEC.md` and `manifest.sha256` of the pin tool (first table). `pin.py` is not changed.

Before (the live tool today):

| File | Bytes | SHA-256 | Git blob id |
|---|---|---|---|
| `runner.py` | 7587 | `807eae9cf9580b2d02784a35c14822e0029c8afd4a3a38ce8c4d181cd169819d` | `00ca4f9aa921abefa5d28ca5688493bc51b0d814` |
| `SPEC.md` | 82851 | `7851ca03de942f1074674d4d1c69814968174ce57f01a4aa1b502cac7bc86cc6` | `267abfc51d82c088e1798079814dac4b17621d1d` |
| `manifest.sha256` | 785 | `9cf4b55385f3b73ca20d7be8ae5533716cae5ba95adbca99ae85d024f097bbb8` | `8b7a712992f22cb5820d9299b004026f762deacb` |
| `pin.py` | 11536 | `26845c75a92c41f135946ea1283bf39ce2a76b355f9103abf5c97cc35e20f1e6` | `5fe2789d48dcc4b484a208c2e2759c3952503731` |

After (to be installed; the `manifest.sha256` row is the expected result of the rewrite, `pin.py` is the same file as before):

| File | Bytes | SHA-256 | Git blob id |
|---|---|---|---|
| `runner.py` | 9353 | `8dcd0207f927f731e1603fc6a32e8cd4ae57246b50414e8b9d89fa8928f59d82` | `362c0fb436b5a929956c87051006c2a67fd5b98a` |
| `SPEC.md` | 94716 | `e111b8bf6980da84bd6ce146df9340459fc5a03838b57cb6370b5ce4b82d27d5` | `d6df63b05387a31396db73c8be3d150335743fc7` |
| `manifest.sha256` | 785 | `b9188c2c18bd6f4ec3fd349a8261a2c6174533c2533599b6f8130bcdf560f671` | `84e29853a6484ca1c51c5d805bc43d30a95c02ca` |
| `pin.py` | 11536 | `26845c75a92c41f135946ea1283bf39ce2a76b355f9103abf5c97cc35e20f1e6` | `5fe2789d48dcc4b484a208c2e2759c3952503731` |

What the install must reproduce: a 16-file result table of 3,166 bytes with SHA-256 `d8df36b93abb1306e51a72afc27c68c7378c14278c7f2c7f9464567a18a2cf2f`, and, for each of the 16 pin runs (numbered in the order of that table, no names published), a result block whose digest is the one below. The digest is the SHA-256 of the compact JSON (keys sorted, no spaces) of the report's `counts`, `lines`, `ok` and `tests_sha256` entries. The raw SHA-256 of a whole report changes from run to run, because it holds the run's own folder name, so after the install the raw SHA-256 of the first live reports are published as a record and the digests are what is compared.

| # | Report before the install (SHA-256 of the file) | Expected digest of the result block after the install |
|---|---|---|
| 01 | `235a5261cc4e58c7c3e78886f1ae72ba5cbffab2a0c511bd5d293b68eca67bd6` | `581a75dfa12efc95891ba2b93dd1dd7f924281e31353ad4cb8201118af525b75` |
| 02 | `35b9e86cf7f442ccf127d9241b91f6dbeefa6ea19c968f8ec9ebee9a3a3dd69c` | `95d0fd86b0041f0e2ce49e0a1c5c6667735a3a27da652908c3aa9de5aa06c573` |
| 03 | `1d0fc5cd625ea4c3fc5990f002af0e925e02d80de2b2b32ce911b7be3653a6f1` | `ff4e854d2fa594bf168e24eaa03ec6448f4d2b0ed0e66e35d866c880e25cd31e` |
| 04 | `dc99f401a38889ad247c31f1a5bf634f23ea7753db3120c44bc59013adfeba99` | `d527eae8d35c28e1b993cc1cbe88dbe7f473eca9d0caeb4aa76c80dba1109384` |
| 05 | `8c3900e95886a492d070b9401232b20114fa068059532eed7276d1e4cea8d739` | `3b810018ce76cac1c28f21a31592e53fec52607ab767293d0ab67632f080310f` |
| 06 | `da02125b4dd9446cbd09952e2869fe68719d21e0d8d7ef45a2452c8226e2ebce` | `765537a0e5b07bf20094020d53a55bba9ccaad0b0ea322134e5ff8444a48093d` |
| 07 | `683d1bd383dd1f67d8e4c5a48b4abb54f7889de3d40563cb2d9381c210468687` | `7597db4f46f5701b5402fa8406de5490e74d617c15e895c9d786130e1b16728f` |
| 08 | `ccc4936486832492ea0d90aed3ef6934384aad36012cf06d3fab430ff25e9977` | `df582f800bce58fd5e10427763381bd7114b8cc698d86f3af73ccaee47b4b35a` |
| 09 | `1d4d3720aab800f6999b4d1affa6ea8ca625348993d9ae08f2527bcacc5415aa` | `534e6450bfb52dfba63fa989a193028458ed9d5718e057065612cf6c745a399d` |
| 10 | `d85083afa11753d6f05bdb74f393d687c6f1b43281fa72d4ba92fbd2843f2f0d` | `b5ba4ae50eb48cb2db5c23d279bf0ef678803abcd5a3ffa7bb6de2b8364f4aae` |
| 11 | `6889e7fd2bee9189d663c7ba982c08e70d4e84bf548591b96c91b26052989d1b` | `6e19ae3f292db731622ca2f6bc3efdb674fd9a734fbc093a949fb9d8e97b31d0` |
| 12 | `a3a204df99920877e39ae8fe40adcae6a152109330e1ea5a2d58e7982c7639cf` | `40d337044030d6e652a2eb3b50306db8f81a8b3159e6582fa7067d016a21ac3a` |
| 13 | `0802ff4a752026baa07f1ef27097612089adfb936ac82fde8757b8da5541eea2` | `3f29c200708705392de305a6e41e1331eb8a54bbfda7b22cc9b2fa809b12c789` |
| 14 | `fb297853149aacd878e9f1e83b7c3295e38ebbbbdbda8b03eaf668ec5d3fc550` | `848a1d6c6c9b0dadb3d78b923baa67742a388174be3b11e1ad43bedb4c1fedbc` |
| 15 | `456c436e7231d2618805cee47f5001bb6203af5348bb5e08df6a45939b113292` | `83505d983f46e38279d4a5cb6b2ee8d4ac8582b7b71815c8763979f3d61200d1` |
| 16 | `257d6c1097ce298433393fce90512e808a85931f60f7138ada955d398b11d411` | `bd92f100aa38da48157a2312b577b5a36a039820b5dc0ff008cdc2a4e722f82a` |

**Result of the install (2026-11-11 18:22 UTC):** the four files of the tool, read back after the install, carry exactly the fingerprints in the "After" table above. The 16-file result table has SHA-256 `d8df36b93abb1306e51a72afc27c68c7378c14278c7f2c7f9464567a18a2cf2f` (equal to the published value), and the digests of all 16 result blocks equal the expected ones in the table above. The 18-test order passed (18 of 18) and the check after the install passed.

Other fingerprints for this install:

| Item | SHA-256 |
|---|---|
| install script | `c40f40cff296cb7404e304341fd3438d41fe56643945b39bde23ee466e2bf24d` |
| audit list of the live tool and the files that must not change (41 lines) | `c0ba18c96db8551bb99f84a2346783be0b6d58d5fdbd8f1fc9d00b7cd77a26f1` |
| order text for the 18 tests | `66cb6819d811e887e6d75ba19346ec7246783126b68f273f37cac769a00cb5dc` |
| kill -9 test report (38 checks on copies) | `840c09c30af84de604f6db0060c0a8c15bbce643b00cceb11bbf830d8e5cd10b` |

Machine-readable copies: [`2026-11-11-pin-tool-2748-before.sha256`](2026-11-11-pin-tool-2748-before.sha256), [`2026-11-11-pin-tool-2748.sha256`](2026-11-11-pin-tool-2748.sha256) and [`2026-11-11-pin-tool-2748-reports-before.sha256`](2026-11-11-pin-tool-2748-reports-before.sha256) (named `report_01.json` to `report_16.json`).
