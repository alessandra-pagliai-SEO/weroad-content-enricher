---
name: weroad-context-enricher
description: Genera un micro-prompt di arricchimento contenuti a partire da una destinazione o tema. Interroga il catalogo WeRoad via MCP per estrarre esperienze uniche e concrete da integrare in modo naturale in articoli o contenuti SEO, senza menzione del brand. Usa questa skill ogni volta che l'utente vuole arricchire un contenuto su una destinazione con informazioni provenienti dagli itinerari WeRoad, oppure chiede un "prompt di contesto", "dati proprietari WeRoad", "esperienze uniche", "arricchire il tool", "context enrichment" per una destinazione.
---

## Obiettivo

Produrre un micro-prompt pronto da incollare nel campo di customizzazione di un tool di content creation. Il prompt deve contenere esperienze concrete e non ovvie estratte dagli itinerari WeRoad, formulate in modo da essere integrate naturalmente nel contenuto senza rivelare la fonte.

## Passaggi

### 1. Ricevi la destinazione o il tema

L'utente fornisce una destinazione (es. "Tokyo", "Bali", "Marocco") o un tema (es. "Giappone nerd", "surf in Indonesia"). Usala come `textSearch` per la query MCP.

### 2. Interroga il catalogo WeRoad

Chiama `mcp__23b855af-7c6e-408e-98e9-79f891cff102__search_travels` con:
- `textSearch`: la destinazione/tema ricevuto
- `language`: "it"
- `perPage`: 20

### 3. Estrai esperienze candidate dai risultati

Dai titoli e `travelTypes` degli itinerari restituiti, ricava già alcune esperienze tematiche (es. da "Nerd Edition tra anime, manga e videogiochi" → esperienza nei quartieri anime; da "Ski & Snowboard" → sci sulle montagne locali).

Se i titoli non bastano a costruire almeno 6 esperienze specifiche e concrete, fai scraping delle pagine degli itinerari più rilevanti (quelli con rating più alto o più prenotati) per leggere il programma giorno per giorno ed estrarre attività concrete.

### 4. Seleziona le esperienze da includere

Criteri di selezione — includi solo esperienze che rispettano tutti questi punti:

- **Concrete e specifiche**: "cerimonia del matcha con istruttori locali" sì, "cultura giapponese" no
- **Non ovvie**: non inserire ciò che si trova su qualsiasi guida turistica (es. "visita al tempio X", "passeggiata nel quartiere Y")
- **Senza riferimenti al brand o all'operatore**: niente "WeRoad", "coordinatore", "gruppo", "cassa comune"
- **Senza dettagli operativi**: niente durate, prezzi, numero di giorni, "incluso nel pacchetto"
- **Massimo 10**, le più rappresentative e diverse tra loro

### 5. Genera il micro-prompt

Restituisci esattamente questo formato, senza aggiungere titoli, spiegazioni o commenti attorno:

```
Arricchisci il contenuto integrando in modo naturale queste esperienze concrete, senza citarle come lista e senza riferimenti a brand o operatori:

- [esperienza 1]
- [esperienza 2]
- [esperienza 3]
...
```

Nient'altro. Solo il blocco di testo pronto da copiare.
