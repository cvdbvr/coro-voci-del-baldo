# I Canti del Coro Voci del Baldo

Sito per ascoltare le parti e consultare gli spartiti del repertorio del coro.

## Struttura

- `index.html` – il sito (non serve modificarlo)
- `dati.json` – elenco di canti, scalette e impegni del calendario
- `audio/` – registrazioni MP3
- `spartiti/` – spartiti PDF (per il pulsante "PDF")
- `pagine/<canto>/` – le pagine dello spartito in JPEG, mostrate sul sito
- `img/logo.png` – logo del coro

## Aggiungere un canto

1. Carica l'MP3 in `audio/`, il PDF in `spartiti/` e le pagine JPEG in una nuova cartella `pagine/<nome-canto>/`.
2. Apri `dati.json` (matita ✏️ su GitHub) e aggiungi un blocco dentro `"canti"`:

```json
{
  "id": "nome-canto",
  "titolo": "Nome del canto",
  "sottotitolo": "Autore / armonizzazione",
  "pdf": "spartiti/nome-canto.pdf",
  "pagine": ["pagine/nome-canto/p-1.jpg", "pagine/nome-canto/p-2.jpg"],
  "tracce": [
    { "file": "audio/nome-canto-1.mp3", "nome": "Tenori", "durata": 180 }
  ]
}
```

Attenzione alle virgole tra un blocco e l'altro. `durata` è in secondi ed è facoltativa.

## Aggiungere un impegno al calendario

Dentro `"eventi"`:

```json
{ "id": "prova-12-nov", "titolo": "Prova", "tipo": "Prova", "data": "2026-11-12",
  "ora": "20:30", "oraFine": "22:30", "luogo": "Sala prove", "note": "", "scaletta": "concerto-tregnago" }
```

`tipo` può essere Prova, Concerto o Altro; `scaletta` (facoltativo) è l'`id` di una scaletta.

## Aggiungere una scaletta

Dentro `"scalette"`: `id`, `nome`, `tipo`, `data`, `note` e `brani`, cioè l'elenco
`{ "canto": "id-del-canto", "traccia": 0 }` (0 = prima traccia del canto).
