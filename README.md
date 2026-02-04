# IPR DataCenter Metrologico (HERMETICUM)

Infrastruttura europea per la **misura ex-ante** della legittimità tecnica delle azioni digitali
tramite **Identity Primary Record (IPR)**.

Questo repository descrive un **DataCenter metrologico**.  
**Non governa, non decide, non autorizza.**  
Misura ex-ante la coerenza tecnica di un’azione rispetto a un riferimento IPR.

In assenza di prova verificabile → **blocco** (fail-closed).

---

## Definizione (one-liner)

Un **IPR DataCenter Metrologico** è un’infrastruttura di **control-plane** che consente
l’esecuzione di azioni digitali, algoritmiche o robotiche **solo se precedute**
da un Identity Primary Record verificabile ex-ante, operando in regime fail-closed
e senza custodia di dati personali.

---

## Perché “metrologico”

Questo DataCenter non esercita autorità.

È **metrologico** perché:
- non valuta contenuti o finalità;
- non decide nel merito delle azioni;
- misura la coerenza tecnica rispetto a un riferimento immutabile (IPR);
- rende la verifica **riproducibile**, **deterministica** e **auditabile**.

> La legittimità non è concessa.  
> È **misurata**.

---

## Principio fondamentale

Un’azione **NON deve essere eseguita** se, prima dell’esecuzione,
non esistono condizioni tecnicamente verificabili di:
- attribuzione umana;
- decisione esplicita;
- tracciabilità opponibile;
- esposizione temporale auditabile.

In assenza di prova → **nessuna esecuzione**.

---

## Architettura — DataCenter fisico (control-plane / execution-plane)

```txt
IPR DATACENTER METROLOGICO (HERMETICUM)
ARCHITETTURA FISICA / LOGICA — FAIL-CLOSED

            CONTROL-PLANE (METROLOGICO)
+--------------------------------------------------+
|                                                  |
|  IPR Reference (hash-only, append-only)          |
|                                                  |
|  JOKER Gate / Precheck API                       |
|  - misura ex-ante                                |
|  - PASS / FAIL + reason_code                     |
|  - audit hash-only (append-only)                 |
|  - nessuna custodia dati                         |
|                                                  |
+-------------------------+------------------------+
                          |
                          | PASS only
                          | (condizione tecnica)
                          v
              EXECUTION-PLANE (DATACENTER)
+--------------------------------------------------+
|                                                  |
|  Compute / Jobs / AI / Robot / Automazione       |
|                                                  |
|  - esegue SOLO se autorizzato ex-ante             |
|  - nessun fallback permissivo                    |
|  - nessuna eccezione manuale                     |
|                                                  |
+--------------------------------------------------+
                          ^
                          |
                          | FAIL -> BLOCCO
                          | (nessuna esecuzione)
                          |
                audit_event + reason_code
                (verificabile nel tempo)


SEPARAZIONE DEI RUOLI (INVARIANTE)

- IPR              = riferimento
- JOKER / Precheck = misura (control-plane)
- DataCenter       = esecutore vincolato (execution-plane)

REGOLA CANONICA

Assenza di prova verificabile ex-ante  =>  Nessuna esecuzione
