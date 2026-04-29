# Totango API Scripts

Shell scripts for querying Totango account and user data. Token is pre-configured — just clone and run.

---

## Setup

### 1. Clone the repo

```bash
git clone https://github.com/YOUR-ORG/totango-api.git
cd totango-api
```

### 2. Make scripts executable

```bash
chmod +x *.sh
```

That's it.

---

## Scripts

| Script | Endpoint | What it returns |
|---|---|---|
| `get_active_accounts.sh` | `/search/accounts` | All Working Level accounts in active onboarding |
| `get_aging_projects.sh` | `/search/accounts` | Aging projects still in active onboarding |
| `get_all_users.sh` | `/search/users` | All users across onboarding accounts, with activity + usage data |

---

## Running

```bash
./get_active_accounts.sh
./get_aging_projects.sh
./get_all_users.sh
```

Output is JSON. To save to a file:

```bash
./get_active_accounts.sh > active_accounts.json
```

To pretty-print in the terminal (requires Python):

```bash
./get_active_accounts.sh | python3 -m json.tool
```

---

## Fields returned

**Accounts** (`get_active_accounts.sh`, `get_aging_projects.sh`)

- Implementation Manager (Leader)
- Health rank
- Multidimensional Health Score
- Usage Health Score
- ACV (Contract Value)
- MI Usage Trend
- Contract Start Date
- Days in Onboarding
- Customer Kick Off Meeting date
- Onboarding Stage
- Product Groups
- Account ID
- Number of Active Objectives

**Users** (`get_all_users.sh`)

- Email
- Account Role
- Active days (30d)
- MI Usage (14d)
- Klear Usage (14d)
- User Intent Use Case
- Last activity date
- Parent Account ID, Implementation Manager, Product Groups

---

## Troubleshooting

**403 Forbidden** — The most common cause is copying the curl command from a file that was saved in RTF format (e.g. from macOS TextEdit). The RTF markup silently corrupts the request. Use these `.sh` scripts directly instead.

**Permission denied** — Run `chmod +x *.sh`
