# Index of Claude models

The following table lists the dates in the model lifecycle for all publicly released Claude models. The “Knowledge” column lists the approximate date beyond which the model's world-knowledge is unreliable, and the “Training” column lists the date of the latest training data.

Anthropic typically “retires” their models from their own infrastructure approximately one year after release, although they have committed to archiving the weights of every model that was ever released, with the stated intention of making deprecated models available again when it becomes financially and logistically feasible. Some models may remain available beyond their official retirement via third-party inference providers such as Amazon and Google, which have their own separate retirement dates; the dates in this table refer to the Anthropic API only.

**Last updated:** 2026-07-02. Still a work in progress. Need to dig through the Internet Archive because Anthropic's website no longer lists some details for older models.

| Model name                | Knowledge  | Training   | Release    | Retirement   |
| ------------------------- | ---------- | ---------- | ---------- | ------------ |
| Claude 1                  | ?          | ?          | 2023-03-14 |   2024-11-06 |
| Claude Instant            | ?          | ?          | 2023-03-14 |   2024-11-06 |
| Claude 1.1                | ?          | ?          | ?          |   2024-11-06 |
| Claude 1.2                | ?          | ?          | ?          |   2024-11-06 |
| Claude 1.3                | ?          | ?          | 2023-07    |   2024-11-06 |
| Claude Instant 1.1        | ?          | ?          | ?          |   2024-11-06 |
| Claude 2                  | early 2023 | early 2023 | 2023-07-11 |   2025-07-21 |
| Claude Instant 1.2        | early 2023 | early 2023 | 2023-08-09 |   2024-11-06 |
| Claude 2.1                | early 2023 | early 2023 | 2023-11-21 |   2025-07-21 |
| Claude 3 Sonnet           | mid-2023   | mid-2023   | 2024-03-04 |   2025-07-21 |
| Claude 3 Opus             | mid-2023   | mid-2023   | 2024-03-04 |   2026-01-05 |
| Claude 3 Haiku            | mid-2023   | mid-2023   | 2024-03-07 |   2026-04-20 |
| Claude 3.5 Sonnet (v1)    | ?          | ?          | 2024-06-21 |   2025-10-28 |
| Claude 3.5 Sonnet (v2)    | ?          | ?          | 2024-10-22 |   2025-10-28 |
| Claude 3.5 Haiku          | 2024-07    | ?          | 2024-10-22 |   2026-02-19 |
| Claude 3.7 Sonnet         | ?          | ?          | 2025-02-24 |   2026-02-19 |
| Claude Sonnet 4           | 2025-01    | 2025-03    | 2025-05-22 |   2026-06-15 |
| Claude Opus 4             | 2025-01    | 2025-03    | 2025-05-22 |   2026-06-15 |
| Claude Opus 4.1           | 2025-01    | 2025-03    | 2025-08-05 |   2026-08-05 |
| Claude Sonnet 4.5         | 2025-01    | 2025-07    | 2025-09-29 | ≥ 2026-09-29 |
| Claude Haiku 4.5          | 2025-02    | 2025-07    | 2025-10-15 | ≥ 2026-10-15 |
| Claude Opus 4.5           | 2025-05    | 2025-08    | 2025-11-24 | ≥ 2026-11-24 |
| Claude Opus 4.6           | 2025-05    | 2025-08    | 2026-02-05 | ≥ 2027-02-05 |
| Claude Sonnet 4.6         | 2025-08    | 2026-01    | 2026-02-17 | ≥ 2027-02-17 |
| Claude Mythos[^2] Preview | 2026-01    | 2026-01    | 2026-04-07 |   2026-06-30 |
| Claude Opus 4.7           | 2026-01    | 2026-01    | 2026-04-16 | ≥ 2027-04-16 |
| Claude Opus 4.8           | 2026-01    | 2026-01    | 2026-05-28 | ≥ 2027-05-28 |
| Claude Mythos[^2] 5       | 2026-01    | 2026-01    | 2026-06-09 | ≥ 2027-06-09 |
| Claude Fable[^3] 5        | 2026-01    | 2026-01    | 2026-06-09 | ≥ 2027-06-09 |
| Claude Sonnet 5           | 2026-01    | 2026-01    | 2026-06-30 | ≥ 2027-06-30 |

[^1] Claude 3 Opus remains accessible to Anthropic API users via a “research access” program. So far, access has been granted to everyone who has requested it.

[^2] Access to Mythos-class models is restricted to approved organisations participating in [Project Glasswing](https://anthropic.com/glasswing) for defensive cybersecurity.

[^3] Fable is the same underlying model as Mythos, tightly muzzled by classifiers to prevent misuse.
