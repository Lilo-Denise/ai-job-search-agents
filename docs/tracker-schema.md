# Application tracker

A Google Sheets workbook, read and written by agents through a small Python helper. Columns are always addressed by name, never by letter, because columns have been inserted over time.

## Status values

Agents use exactly these nine values.

| Status | Meaning |
|---|---|
| Discovered | Logged, no action yet |
| Selected | I asked Tailor to analyze it |
| CV Ready | CV built, not submitted |
| Applied | Submitted; Date Applied is filled |
| Interviewing | Interview invitation received |
| Rejected | Rejection received |
| Withdrawn | I decided not to apply after the fit analysis (reason in its own column) |
| Dropped | I decided no from the job post alone (reason in its own column) |
| Dead | The post closed |

## Key columns

- **Created Date / Posted Date / Days Since Posted:** freshness. Posted Date comes from the job system's own metadata where possible; a blank is better than a guess.
- **Fit Score and fit note:** written by Scout or Tailor, never inflated.
- **Match Logic:** how the role was found (broad search, profile match, or my own link), to compare which discovery method leads to interviews.
- **Drop/Withdraw Reason:** a few words, filled only for Dropped or Withdrawn.
- **Interview rounds:** date, format, type, interviewer, outcome and thank-you sent, per round.

Separate tabs hold networking contacts and a log of real conversations.
