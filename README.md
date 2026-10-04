# bidly-actions-only

Worker pubblico per Bidly (stesso pattern di `cemform-actions-only`).

- I workflow vivono qui (minuti Actions gratuiti/illimitati su repo pubblica).
- Fanno checkout del repo privato [`mpiscitelli98/bidly`](../bidly) via secret `PAT_BIDLY` (PAT con accesso Contents R/W a `bidly`).
- Eseguono `scripts/tender-watcher.js` e pushano `gare-privata/tenders.json` aggiornato su `bidly`.

## Secret necessari (questo repo → Settings → Secrets → Actions)

| Secret | Cosa |
|---|---|
| `GH_TOKEN` | PAT con Contents+Actions read+write su `bidly` e `bidly-actions-only` (checkout + push + dispatch) |
| `CRON_JOB_API` | API key cron-job.org (solo per `cron-setup`) |

## Attivazione cron

Actions → `cron-setup` → Run workflow: crea i 2 job (daily 07:00, weekly lun 07:30) che chiamano il dispatch di questo repo.
