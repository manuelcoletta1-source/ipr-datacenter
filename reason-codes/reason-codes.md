# Reason Codes — IPR-Datacenter

## Principio
Ogni blocco deve essere spiegabile e verificabile.
I reason codes NON contengono dati personali.

## Catalogo base

- DENIED_NO_IPR  
  Nessun IPR associato all’azione.

- DENIED_IPR_INVALID  
  IPR non verificabile o struttura non valida.

- DENIED_IPR_EXPIRED  
  IPR fuori finestra temporale o scaduto.

- DENIED_HASH_MISMATCH  
  Differenza tra job richiesto e job autorizzato (hash mismatch).

- DENIED_SCOPE_VIOLATION  
  Azione fuori dallo scopo dichiarato nell’IPR.

- DENIED_POLICY_FAIL  
  Violazione di policy tecnica ex-ante.

- DENIED_GATE_UNAVAILABLE  
  Gate non disponibile → fail-closed.

- DENIED_EVIDENCE_REQUIRED  
  Evidence Pack richiesto ma non generabile.

## Nota
Il catalogo è estendibile, ma i codici devono restare stabili e documentati.
