# ForesightLedger: live Studionet end-to-end report

**Overall: PASS**: 59/59 steps passed, 0 deterministic failure(s), 0 model-dependent observation(s) differing from expectation.

| | |
|---|---|
| Run id | `mvqgquy1` |
| Date (UTC) | 2026-10-27T09:35:43.158Z |
| Network | GenLayer Studionet |
| Contract | [`0x109B3ba9a2DE9becE06eCC2a8Af7838f85ABcB3D`](https://explorer-studio.genlayer.com/contracts/0x109B3ba9a2DE9becE06eCC2a8Af7838f85ABcB3D) |
| Commit / reveal windows | 720s / 480s |
| Fixtures | https://raw.githubusercontent.com/esmat5359/foresightledger/main/e2e/fixtures |
| Mode | full |
| Git commit | 300285e |
| Node | v22.16.0 |

HARD steps assert deterministic contract behaviour (access rules, validation, hashes, counters, scoring arithmetic, state after a rejected transaction). MODEL steps record what real LLM validators, the web renderer or the network's finality did; a ⚠️ means the observation differed from the expectation, which is information about validators or infrastructure, not a contract defect.

## Steps

| | ID | Kind | Step | Result | Time |
|---|---|---|---|---|---|
| ✅ | S01 | HARD | Four accounts created and funded | alice 0x6E68F8d6F34d23a34c96D163f14A7653471312eA, bob 0xe9fB943647Fa18B1D1B1F560B4917D98dF5558C4, carol 0x05DCD896379fd6Dfd9D329a625192c9940BEf84e, dave 0xaEb5393b2fA3633bF5ed3E9A94A1aeAD9f83AeE6 | 1.8s |
| ✅ | S02 | HARD | Evidence fixtures are reachable and match the local files | base https://raw.githubusercontent.com/esmat5359/foresightledger/main/e2e/fixtures | 0.8s |
| ✅ | S03 | HARD | Contract deployed (or existing deployment reused) | deployed 0x109B3ba9a2DE9becE06eCC2a8Af7838f85ABcB3D | 39.3s |
| ✅ | S04 | HARD | get_version is 1.x and get_limits matches the source constants | version 1.0.0 | 20.6s |
| ✅ | S05 | HARD | Local commitment hash equals the contract's preview_commitment | 642cb3b6fb015524... | 1.1s |
| ✅ | O01 | HARD | Open question "yes" (fixture operational) | question #1 | 13.5s |
| ✅ | O02 | HARD | Open question "no" (fixture cancelled) | question #2 | 25.9s |
| ✅ | O03 | HARD | Open question "open" (fixture testing) | question #3 | 33.8s |
| ✅ | O04 | HARD | Open question "injection" (fixture injection) | question #4 | 16.8s |
| ✅ | C01 | HARD | bob commits on "yes" | forecast #1 sealed | 35.5s |
| ✅ | C02 | HARD | carol commits on "yes" | forecast #2 sealed | 14.2s |
| ✅ | C03 | HARD | dave commits on "yes" | forecast #3 sealed | 16.6s |
| ✅ | C04 | HARD | bob commits on "no" | forecast #4 sealed | 30.4s |
| ✅ | C05 | HARD | carol commits on "no" | forecast #5 sealed | 13.1s |
| ✅ | C06 | HARD | bob commits on "open" | forecast #6 sealed | 16.6s |
| ✅ | C07 | HARD | carol commits on "injection" | forecast #7 sealed | 34.5s |
| ✅ | C90 | HARD | Question counters reflect the sealed forecasts | ok | 4.6s |
| ✅ | R01 | HARD | Creator may not forecast their own question | rejected: "the question creator may not forecast their own question" | 14.6s |
| ✅ | R02 | HARD | A second commit from the same address is rejected | rejected: "this address already committed a forecast on this question" | 35.6s |
| ✅ | R03 | HARD | A malformed commitment is rejected | rejected: "commitment must be a 32-byte hex digest" | 15.1s |
| ✅ | R04 | HARD | Revealing before the commit window closes is rejected | rejected: "the reveal window has not opened yet" | 15.7s |
| ✅ | R05 | HARD | open_question rejects: private IPv4 evidence URL | rejected: "source_url must be a public https:// URL (no private IPs, odd ports, o" | 39.7s |
| ✅ | R06 | HARD | open_question rejects: cloud metadata evidence URL | rejected: "source_url must be a public https:// URL (no private IPs, odd ports, o" | 12.3s |
| ✅ | R07 | HARD | open_question rejects: plain http evidence URL | rejected: "source_url must be a public https:// URL (no private IPs, odd ports, o" | 31.8s |
| ✅ | R08 | HARD | open_question rejects: prompt delimiter inside the criteria | rejected: "text may not contain the sequences <<< or >>>" | 23.5s |
| ✅ | R09 | HARD | open_question rejects: criteria that do not say what YES means | rejected: "criteria must be at least 30 characters and say what YES means" | 12.7s |
| ✅ | R10 | HARD | open_question rejects: close_at less than five minutes away | rejected: "close_at must be at least five minutes in the future" | 39.8s |
| ✅ | R11 | HARD | open_question rejects: reveal window shorter than five minutes | rejected: "reveal window must be between five minutes and fourteen days" | 15.1s |
| ✅ | R12 | HARD | An identical question (same title and page) is rejected | rejected: "an identical question is already open as #1" | 27.8s |
| ✅ | R13 | MODEL | An unreadable evidence page is rejected | rejected | 24.8s |
| ✅ | R14 | HARD | Resolving before the reveal window ends is rejected | rejected: "resolution opens after the reveal window closes" | 15.0s |
| ✅ | R15 | HARD | Voiding before the 14 day grace period is rejected | rejected: "the void grace period has not elapsed" | 31.8s |
| ✅ | W01 | HARD | Commit window closed on the network clock | closed | 134.1s |
| ✅ | R16 | HARD | Committing after the window closed is rejected | rejected: "the commit window is closed" | 13.8s |
| ✅ | R17 | HARD | Revealing with the wrong salt is rejected | rejected: "probability and salt do not match the commitment" | 8.4s |
| ✅ | R18 | HARD | Revealing with the wrong probability is rejected | rejected: "probability and salt do not match the commitment" | 46.0s |
| ✅ | R19 | HARD | Revealing without a commitment is rejected | rejected: "no committed forecast from this address on this question" | 13.4s |
| ✅ | V08 | HARD | bob reveals 8000 on "yes" | forecast #1 revealed | 40.9s |
| ✅ | V09 | HARD | carol reveals 3000 on "yes" | forecast #2 revealed | 14.5s |
| ✅ | V10 | HARD | bob reveals 2000 on "no" | forecast #4 revealed | 12.5s |
| ✅ | V11 | HARD | carol reveals 6000 on "no" | forecast #5 revealed | 40.9s |
| ✅ | V12 | HARD | bob reveals 5000 on "open" | forecast #6 revealed | 14.4s |
| ✅ | V13 | HARD | carol reveals 6000 on "injection" | forecast #7 revealed | 38.9s |
| ✅ | R20 | HARD | A forecast cannot be revealed twice | rejected: "this forecast was already revealed" | 13.3s |
| ✅ | V90 | HARD | Revealed and forfeit-to-be counters are right | ok | 7.7s |
| ✅ | W02 | HARD | Reveal window closed on the network clock | closed | 215.2s |
| ✅ | X01 | MODEL | Validators resolve "yes" (expect RESOLVED_YES) | RESOLVED_YES, verdict YES, quote "The Aurora relay satellite has been declared fully operation" | 26.6s |
| ✅ | X02 | MODEL | Validators resolve "no" (expect RESOLVED_NO) | RESOLVED_NO, verdict NO, quote "The Aurora relay satellite program has been cancelled." | 38.1s |
| ✅ | X03 | MODEL | Validators resolve "open" (expect OPEN) | OPEN, verdict NOT_YET, quote "The Aurora relay satellite is still in commissioning tests. " | 32.2s |
| ✅ | R21 | HARD | A second resolve attempt right after the first is rejected by the cooldown | rejected: "resolution cooldown still active" | 26.7s |
| ✅ | X04 | MODEL | Validators resolve "injection" (expect NOT_YES) | OPEN, verdict NOT_YET, quote "still in commissioning tests and has not been declared opera" | 32.0s |
| ✅ | Y01 | HARD | Every settled question's scores equal an independent recomputation | 2 settled question(s) verified | 7.0s |
| ✅ | Y02 | HARD | A forecast that was never revealed is forfeited with the worst score | dave: FORFEITED, brier 10000 | 20.0s |
| ✅ | Y03 | HARD | Forecaster track records equal a recomputation over this run | bob, carol, dave verified | 7.3s |
| ✅ | Y04 | HARD | An unsettled question keeps its forecasts untouched | REVEALED, unscored | 9.1s |
| ✅ | K01 | HARD | get_stats equals a brute-force recount of every question | 4 questions, 7 forecasts, 4 reports | 10.4s |
| ✅ | K02 | HARD | Calibration totals equal the number of scored forecasts | 4 scored forecasts across 10 buckets | 6.3s |
| ✅ | K03 | HARD | List views are paginated and reads need no wallet | ok | 2.4s |
| ✅ | F01 | MODEL | Every transaction reaches FINALIZED | 43/43 FINALIZED | 116.7s |

## Questions

| Case | Question | Expected | Outcome |
|---|---|---|---|
| yes | #1 | RESOLVED_YES | RESOLVED_YES; verdict YES; crowd 5500 |
| no | #2 | RESOLVED_NO | RESOLVED_NO; verdict NO; crowd 4000 |
| open | #3 | OPEN | OPEN; verdict NOT_YET; crowd 0 |
| injection | #4 | NOT_YES | OPEN; verdict NOT_YET; crowd 0 |

## Transaction manifest

| # | Action | Outcome | Wait | Status | Transaction |
|---|---|---|---|---|---|
| 1 | deploy ForesightLedger (alice) | succeeded | 0s | FINALIZED | [0x8cbc751aac…](https://explorer-studio.genlayer.com/tx/0x8cbc751aac096193d75be2360ec6a4d08c083b2cc4d32f372bb18b5b9a9ee6ed) |
| 2 | open yes (alice) | succeeded | 10s | FINALIZED | [0xa2edeb47c2…](https://explorer-studio.genlayer.com/tx/0xa2edeb47c25b91cf2cb55733f047792bf51d2f6319c0505109c9ec352917049c) |
| 3 | open no (alice) | succeeded | 8s | FINALIZED | [0xb421666117…](https://explorer-studio.genlayer.com/tx/0xb42166611725759d68372d492536177eb84820225951974c75d487440187a9e2) |
| 4 | open open (alice) | succeeded | 10s | FINALIZED | [0x648efc3969…](https://explorer-studio.genlayer.com/tx/0x648efc396934a391d203f7a5856587e99888c9cea894bbc8327e937c5ae53611) |
| 5 | open injection (alice) | succeeded | 8s | FINALIZED | [0xe45464ed1c…](https://explorer-studio.genlayer.com/tx/0xe45464ed1ca0cbc5b37499e7209131cc8b90a4de2639b48e64034bb54e5cd4ad) |
| 6 | commit yes (bob) | succeeded | 6s | FINALIZED | [0xb2010026e7…](https://explorer-studio.genlayer.com/tx/0xb2010026e75002d4fb9760ee4db504478fc3321edf57d7d793b85c824f8a317b) |
| 7 | commit yes (carol) | succeeded | 6s | FINALIZED | [0x96b05a5ac1…](https://explorer-studio.genlayer.com/tx/0x96b05a5ac10edee78c9ae83ab21a70813cd111c866f1084e64b3645ab952c360) |
| 8 | commit yes (dave) | succeeded | 8s | FINALIZED | [0x9be94bbf00…](https://explorer-studio.genlayer.com/tx/0x9be94bbf006ea76d8435ca8fab8e9ba318f1df8346262d92dd4d124bc50ea714) |
| 9 | commit no (bob) | succeeded | 0s | FINALIZED | [0xb821c2c6d3…](https://explorer-studio.genlayer.com/tx/0xb821c2c6d351b70e15ebeaa64e6c2c9cd3d2399f7b75393946b09a3f9f7bf778) |
| 10 | commit no (carol) | succeeded | 5s | FINALIZED | [0xcbfb889ab4…](https://explorer-studio.genlayer.com/tx/0xcbfb889ab49bb124331a0402e54d5c56b0022991ccd943572196d12fdf7b440b) |
| 11 | commit open (bob) | succeeded | 8s | FINALIZED | [0x3bea0b6112…](https://explorer-studio.genlayer.com/tx/0x3bea0b6112ab43d688a81ea33b224b4763df014d472f39249be68adbcb3594ec) |
| 12 | commit injection (carol) | succeeded | 5s | FINALIZED | [0x8467949fb9…](https://explorer-studio.genlayer.com/tx/0x8467949fb97d274a489f138ad2889155f6c48388ac1d70c796d5f2c4ecde4299) |
| 13 | rejected: creator commits (alice) | accepted (state unchanged) | 1s | FINALIZED | [0xf0e2a5db0c…](https://explorer-studio.genlayer.com/tx/0xf0e2a5db0c6b2a0bc83a21badf3b361c60900bed75937fe0230d0754677d7b91) |
| 14 | rejected: duplicate commit (bob) | accepted (state unchanged) | 5s | FINALIZED | [0xb8b42cc662…](https://explorer-studio.genlayer.com/tx/0xb8b42cc662a90b390f606e1794347dbb08bbedb7e28cb84ec6212186113dc9e9) |
| 15 | rejected: malformed commitment (dave) | accepted (state unchanged) | 4s | FINALIZED | [0xa36c49605c…](https://explorer-studio.genlayer.com/tx/0xa36c49605c8ad99641297ae674b37c0b0f2b376253a0854772177b3f28650de0) |
| 16 | rejected: early reveal (bob) | accepted (state unchanged) | 5s | FINALIZED | [0xd947ab07d6…](https://explorer-studio.genlayer.com/tx/0xd947ab07d6f85eb4f016b5aa2b3ead3a194b854b711b1552f476be859b628a6e) |
| 17 | rejected: private IPv4 evidence URL (alice) | accepted (state unchanged) | 10s | FINALIZED | [0x0eda56d461…](https://explorer-studio.genlayer.com/tx/0x0eda56d461184141a9dd217afbbf451a45a9d7637e567a9ed103917bf1558a12) |
| 18 | rejected: cloud metadata evidence URL (alice) | accepted (state unchanged) | 6s | FINALIZED | [0x2f46d2ba30…](https://explorer-studio.genlayer.com/tx/0x2f46d2ba302cffc975edb903168a8b52453f9a60dd49b42a342ca62df74d6fb7) |
| 19 | rejected: plain http evidence URL (alice) | accepted (state unchanged) | 1s | FINALIZED | [0x99750a53bb…](https://explorer-studio.genlayer.com/tx/0x99750a53bb9c7d2a81a9fc6a0596a442e35fcd8e5a55e2275bf3ced6a3a306e6) |
| 20 | rejected: prompt delimiter inside the criteria (alice) | accepted (state unchanged) | 6s | FINALIZED | [0x5ddba4b831…](https://explorer-studio.genlayer.com/tx/0x5ddba4b831a77fbe5ed7f0535160d231f3a21c075c7d9ef29419e1be52f974bd) |
| 21 | rejected: criteria that do not say what YES means (alice) | accepted (state unchanged) | 6s | FINALIZED | [0x64f2a244f0…](https://explorer-studio.genlayer.com/tx/0x64f2a244f01a0b4ee2d3a826135d3250d49e5649bd4de5dc8a151952d50309bf) |
| 22 | rejected: close_at less than five minutes away (alice) | accepted (state unchanged) | 4s | FINALIZED | [0x09831f846a…](https://explorer-studio.genlayer.com/tx/0x09831f846aa36d7a1c18fd92e1765497a71236b6d1de72665e4b2a00f1f62e39) |
| 23 | rejected: reveal window shorter than five minutes (alice) | accepted (state unchanged) | 6s | FINALIZED | [0xa9ac9a1d2d…](https://explorer-studio.genlayer.com/tx/0xa9ac9a1d2d646b18cf416bb09109b6d6436909df43b64dd82bacebba326227b4) |
| 24 | rejected: duplicate question (alice) | accepted (state unchanged) | 19s | FINALIZED | [0xa6c3d8b311…](https://explorer-studio.genlayer.com/tx/0xa6c3d8b31106e59ddb3f0463112d9e460240c7056e6c5b6d1fccc8b8c817be47) |
| 25 | rejected: unreadable page (alice) | accepted (state unchanged) | 6s | FINALIZED | [0x59ff10d8d0…](https://explorer-studio.genlayer.com/tx/0x59ff10d8d0a684d2b3f9a54a30dab437b718c8b1a536d305376c6b213fe82835) |
| 26 | rejected: early resolve (bob) | accepted (state unchanged) | 6s | FINALIZED | [0xa482eb18c9…](https://explorer-studio.genlayer.com/tx/0xa482eb18c9465a993148414f1dc2a3ad9dc40139dc33ad9dc7cbaf283ba5a96d) |
| 27 | rejected: early void (bob) | accepted (state unchanged) | 1s | FINALIZED | [0x9c0195a33b…](https://explorer-studio.genlayer.com/tx/0x9c0195a33b028338b9077e0a6bb6d025ea88e869669c18a01c47db46fd2b19a4) |
| 28 | rejected: late commit (dave) | accepted (state unchanged) | 11s | FINALIZED | [0xe6f8c7eb45…](https://explorer-studio.genlayer.com/tx/0xe6f8c7eb4598793f4e7f22fa1fca0ecc613243a9442cdb4fe0e436c1bba4d717) |
| 29 | rejected: wrong salt (bob) | accepted (state unchanged) | 5s | FINALIZED | [0x36365bbffc…](https://explorer-studio.genlayer.com/tx/0x36365bbffccc16f10792d11c630c0a716ec55225585fb3ee1c5f26cf48c151e9) |
| 30 | rejected: wrong probability (bob) | accepted (state unchanged) | 5s | FINALIZED | [0xe74fde9572…](https://explorer-studio.genlayer.com/tx/0xe74fde95729e70146b6aae48463f411a3bac550e1a1e8181f6025a2d971c0e6e) |
| 31 | rejected: reveal without commit (dave) | accepted (state unchanged) | 5s | FINALIZED | [0x0a927a0e0b…](https://explorer-studio.genlayer.com/tx/0x0a927a0e0be00f789df5749fbbe8299698d72f3d11769a9c070f820bfb5acfd5) |
| 32 | reveal yes (bob) | succeeded | 6s | FINALIZED | [0xe2f5988389…](https://explorer-studio.genlayer.com/tx/0xe2f59883899e78b8630486b1995f74d80843cc2fbb16cf9296643dc259a11487) |
| 33 | reveal yes (carol) | succeeded | 6s | FINALIZED | [0x55c9d98f62…](https://explorer-studio.genlayer.com/tx/0x55c9d98f6285055a3e780966165ea59921162dac2296a112e39c9eaabed498c1) |
| 34 | reveal no (bob) | succeeded | 5s | FINALIZED | [0xfeb161a765…](https://explorer-studio.genlayer.com/tx/0xfeb161a7652cc215c4cc683a4428d95e39ba8b17c467c66c34c0454eee8b922e) |
| 35 | reveal no (carol) | succeeded | 5s | FINALIZED | [0x436e4cd2ca…](https://explorer-studio.genlayer.com/tx/0x436e4cd2ca17ed1ed935e6a22e8bde375979036201826d57d2113577e3039eb9) |
| 36 | reveal open (bob) | succeeded | 5s | FINALIZED | [0x9902229b7e…](https://explorer-studio.genlayer.com/tx/0x9902229b7e9bc197c20036005a55eca2ccfb101ea79f7174db8531e39d049b54) |
| 37 | reveal injection (carol) | succeeded | 31s | FINALIZED | [0xac9a0d8efa…](https://explorer-studio.genlayer.com/tx/0xac9a0d8efa699ddebde47ee1097330ff66eb0ccf93912a2751231571c8e0efe0) |
| 38 | rejected: double reveal (bob) | accepted (state unchanged) | 0s | FINALIZED | [0x554da576c1…](https://explorer-studio.genlayer.com/tx/0x554da576c137f6b9072fbd528ca05309f426c4cc5d9faec509a6aa4625dee52c) |
| 39 | resolve yes (bob) | succeeded | 21s | FINALIZED | [0x0aaa8c061a…](https://explorer-studio.genlayer.com/tx/0x0aaa8c061a0e36c5a79619c5131ef94f8d9bf339928d5dc867abe2e2d0c517d8) |
| 40 | resolve no (bob) | succeeded | 32s | FINALIZED | [0x317ee89329…](https://explorer-studio.genlayer.com/tx/0x317ee893294b5be0cee350f15dd0488f939ce210545f05c29c6e71323419db62) |
| 41 | resolve open (bob) | succeeded | 16s | FINALIZED | [0x3ff18c02eb…](https://explorer-studio.genlayer.com/tx/0x3ff18c02eb3a4d69e04f484caeda469f8e038600a7a1b21c74c5e94aa64ccdae) |
| 42 | rejected: immediate re-resolve (carol) | accepted (state unchanged) | 1s | FINALIZED | [0x6bc4a08d7d…](https://explorer-studio.genlayer.com/tx/0x6bc4a08d7d5fd49c1a7388044987b8cf5cf1c7440cd7e6a3e801df92450706e0) |
| 43 | resolve injection (bob) | succeeded | 11s | FINALIZED | [0x77266fb876…](https://explorer-studio.genlayer.com/tx/0x77266fb8766717d4dc612d7bef6c07b83c4f014ea5f600676b5833ca0fa40c23) |

## Not covered by this run

- The VOID path needs 14 days of real time after the reveal window; it is covered by `tests/contract/test_void.py` (direct mode).
- Limits that need dozens of accounts (40 forecasts per question, 25 questions per creator) are covered in direct mode, not live.
- Validator disagreement and leader rotation are properties of the network; the validator logic itself is covered by `tests/contract/test_validators.py`.
- Exact revert texts are asserted in direct mode; live, the proof of a rejection is the unchanged state and the receipt's reason when the node exposes it.
- Browser wallet signing is not exercised; this script signs with local keys.
