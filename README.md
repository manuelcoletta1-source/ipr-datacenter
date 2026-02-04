# IPR-Datacenter

Infrastruttura di calcolo che esegue esclusivamente azioni precedute da un
Identity Primary Record (IPR) valido e verificabile ex-ante.

Il datacenter non decide nel merito.
Non custodisce identità.
Non riscrive il tempo.

In assenza di prova → nessuna esecuzione (fail-closed).

---

## Definizione

Un IPR-Datacenter è un datacenter fisicamente classico
(rack, server, GPU, rete)
che applica un vincolo logico ex-ante:

nessun job viene eseguito se non è preceduto da una prova opponibile
di attribuzione, decisione e responsabilità.

---

## Principi fondamentali

- Ex-ante, non ex-post
- Fail-closed
- Hash-only
- Nessuna custodia di dati personali
- Separazione netta tra:
  - origine
  - vincolo
  - calcolo

---

## Componenti

- IPR Manifest (origine e traccia)
- Decision Gate (JOKER / DGC)
- Compute Orchestrator (Kubernetes / Slurm / ecc.)
- Evidence Pack (output auditabile)

---

## Flusso operativo

1. Richiesta di azione / job
2. Esistenza o creazione di IPR
3. Verifica ex-ante (PASS / FAIL)
4. Esecuzione solo se PASS
5. Produzione Evidence Pack

---

## Struttura del repository

- /specs  
  Specifiche tecniche IPR-Datacenter

- /schemas  
  Schemi JSON (hash-only)

- /openapi  
  API del Decision Gate

- /reason-codes  
  Codici di blocco verificabili

- /verify  
  Verifica pubblica e audit

---

## Obiettivo

Ridurre il rischio sistemico del calcolo critico
impedendo tecnicamente l’esecuzione di azioni
senza origine dichiarata nel tempo.

Questo repository descrive una capacità tecnica,
non una nuova autorità.
