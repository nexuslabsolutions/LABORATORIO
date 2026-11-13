# LABORATORIO

Raccolta di pagine HTML pubbliche dell’account **nexuslabsolutions**.

Ogni strumento vive in una cartella dedicata ed è indipendente dalle altre pagine. L’indice principale permette di aprire i laboratori disponibili.

## Struttura

| Percorso | Contenuto |
| --- | --- |
| `index.html` | Pagina iniziale con l’elenco degli strumenti |
| `tir-van/index.html` | Calcolatore interattivo TIR, VAN e interpolazione |
| `tests/tir-van.test.cjs` | Controlli numerici e di sintassi del calcolatore |
| `.nojekyll` | Consente la pubblicazione statica senza elaborazione Jekyll |

## Laboratorio TIR e VAN

[Apri il file del laboratorio](tir-van/index.html).

La pagina consente di:

- modificare l’investimento iniziale e fino a 20 flussi di cassa;
- scegliere periodi annuali o mensili;
- visualizzare assi, punti, curva del VAN e retta di interpolazione;
- calcolare TIR positivo o negativo e riconoscere più soluzioni ammissibili;
- verificare un tasso specifico e leggere i valori attuali dei singoli flussi;
- impostare la scala del grafico e i due tassi di interpolazione;
- scaricare grafico SVG, tabella CSV e HTML con i parametri correnti;
- stampare i risultati.

I flussi si intendono alla fine di periodi regolari. L’investimento iniziale si inserisce come importo positivo; per i flussi futuri un valore negativo rappresenta un’uscita.

### Esempio iniziale

| Momento | Flusso |
| --- | ---: |
| Oggi | -1.000 € |
| Fine anno 1 | +600 € |
| Fine anno 2 | +600 € |

Risultati attesi:

- VAN al 10%: circa **41,32 €**;
- TIR annuo: circa **13,0662%**;
- interpolazione fra 10% e 15%: circa **13,1354%**.

I calcoli mantengono la precisione numerica disponibile; gli importi visualizzati sono arrotondati ai centesimi.

## Uso sul computer

Scarica il repository e apri `index.html` con un browser moderno. Puoi anche aprire direttamente `tir-van/index.html`.

La pagina del calcolatore è autonoma: contiene HTML, CSS e JavaScript nello stesso file e funziona senza connessione. Non usa servizi di calcolo esterni.

Il pulsante **Scarica HTML** crea una copia con i parametri inseriti.

## Verifica

È necessario soltanto Node.js, senza installare dipendenze:

```sh
node tests/tir-van.test.cjs
```

In alternativa:

```sh
npm test
```

I controlli comprendono VAN, TIR positivo e negativo, più TIR, radici tangenti allo zero, assenza di TIR, interpolazione e 20 periodi.

## Aggiungere un altro HTML

1. Crea una cartella con un nome breve, per esempio `nome-strumento/`.
2. Inserisci la pagina principale come `nome-strumento/index.html`.
3. Aggiungi il collegamento nel catalogo `index.html` alla radice.
4. Inserisci nel progetto soltanto codice e contenuti destinati alla pubblicazione.

Per una pagina autonoma, mantieni CSS e JavaScript nel suo HTML. Se servono risorse separate, inseriscile nella stessa cartella e usa percorsi relativi.

## Pubblicazione web

La struttura è compatibile con GitHub Pages, usando la radice del ramo `main` come sorgente. L’indice apre ogni strumento con un collegamento relativo, così la raccolta funziona anche sotto il percorso del repository.

Non sono richiesti build, pacchetti esterni o variabili segrete.

