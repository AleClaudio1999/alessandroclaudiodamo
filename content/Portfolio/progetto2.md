---
title: "Analisi di Logseq"
date: 2022-09-15T11:30:03+00:00
# weight: 1
# aliases: ["/first"]
tags: ["first"]
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Lavoro conclusivo per il corso di Ingegneria del software"
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page

---

### Introduzione su Logseq

Logseq è una piattaforma per la gestione della propria conoscenza attraverso un database di file di testo (chiamati “pagine”) e relativi allegati.
Consente di collegare e relazionare pagine — e quindi concetti — tra loro, creando così il **grafo di conoscenza**, che permette di visualizzare al meglio le connessioni tra le idee.

È possibile utilizzare file **Markdown** o la modalità **Org** per scrivere, modificare e salvare facilmente nuove note.

Logseq non è il primo tool di questo tipo, ma a differenza dei concorrenti (come i più noti **Roam Research** e **Obsidian**) è **completamente gratuito** e si concentra su **privacy**, **longevità** e **controllo da parte dell’utente**, grazie alla sua natura **open source**.

Attualmente il programma è ancora in **beta**; al momento della stesura si trova nella versione **stable 0.8.2**.
È disponibile per **Windows**, **Mac** e **Linux**, ed esiste anche una **web app** utilizzabile direttamente dal browser.

### Superamento dei criteri di scelta del progetto

Scaricando il sorgente da Github (https://github.com/logseq/logseq) e grazie al tool gratuito cloc (https://github.com/AlDanial/cloc) ho contato il numero di LOC del programma affinché superassero le 50KLOC previste dalla consegna: le LOC sono risultate 59549 cosi suddivise.

| Linguaggio    | Linee di codice | Commenti | Blank | Altro |
| ------------- | --------------- | -------- | ----- | ----- |
| ClojureScript | 45 166          | 249      | 5 824 | 1 465 |
| ClojureC      | 8 316           | 12       | 393   | 65    |
| CSS           | 5 289           | 31       | 1 116 | 45    |
| JavaScript    | 709             | –        | –     | –     |
| Clojure       | 69              | 6        | 4     | 97    |
| Altro         | 7               | 40       | 1     | –     |

**Totale:** 59 549 linee

### Introduzione all’analisi del processo di produzione

Logseq è un progetto **open source** con licenza **AGPL-3.0**, sviluppato dall’omonimo team composto da circa **10 persone**che lavorano **in remoto**, da diverse parti del mondo e con orari **asincroni**.

Per analizzare al meglio il **processo di produzione di Logseq**, partiremo dalla sua attuale release e cercheremo di capire **da dove nascono** e **come vengono sviluppate** le nuove feature.

Inoltre, daremo un’occhiata anche all’**ambito finanziario**, per comprendere come il team si finanzi e come questo influisca sui progetti a lungo termine.

Analizzeremo il **ruolo della community** all’interno del progetto, e come essa collabori con il team sia per lo sviluppo di **plugin**, sia per il **report di problemi e bug**.

Esamineremo poi l’**architettura del programma**, il modo in cui le nuove feature si interfacciano con essa e come l’architettura si sia evoluta nel tempo.

Infine, concluderemo guardando la **presentazione del team**, i loro **valori** e la loro **filosofia lavorativa**, con particolare enfasi sulla **metodologia di comunicazione**, cercando di individuare eventuali correlazioni con l’**Extreme Programming (XP)**.

### Da dove nascono le nuove feature?

Per l’ideazione di nuove feature, il team di Logseq si rivolge spesso alla **community**, attraverso il proprio **forum di discussione**:
👉 [https://discuss.logseq.com](https://discuss.logseq.com/)

All’interno del forum esiste una sezione chiamata **“Feature Request”**, dove qualsiasi utente registrato può proporre nuove funzionalità attraverso un post pubblico.
Con un sistema simile a **Reddit**, i post possono essere **votati**, permettendo così ai **main developer** di stabilire la priorità delle richieste in base al loro successo nella community.

📌 **Esempio:**
Un utente ha chiesto l’introduzione degli *Headings* (titoli più grandi) in questo post:
👉 Headings where they at?

Il post ha ricevuto molti commenti e voti, e nel giro di **5 mesi** la funzionalità è stata effettivamente implementata nel programma.

Anche le **richieste su GitHub** sono attive, ma vengono automaticamente **reindirizzate al forum**, così da raccogliere voti e misurare meglio l’interesse degli utenti (funzionalità che GitHub non offre nativamente).

📌 **Altro esempio:**
Un utente ha proposto la **personalizzazione delle scorciatoie da tastiera** in questo post:
👉 Customizable keyboard shortcuts
La proposta era stata inizialmente fatta su GitHub:
👉 [Issue #553 su GitHub](https://github.com/logseq/logseq/issues/553)

Oltre alle idee provenienti dalla community, il **team di sviluppo** concepisce anche **feature interne**, non presenti né sul blog né su GitHub.
Questo accade perché il team ha una **visione a lungo termine** del progetto e anche un piano per **sostenersi economicamente**, come vedremo più avanti.

In sintesi:

- Le **piccole feature** sono spesso guidate dalla **community**.
- Le **funzionalità più grandi o strategiche** sono invece dirette dal **team di sviluppo**.

### Dalle idee alla realizzazione

Le idee o feature, provenienti sia dalla community che dal team, devono essere **definite e pianificate** prima della realizzazione.
Per farlo, il team utilizza il metodo delle **“Cards”**.

#### 🔹 Le “Cards”

Una **Card** rappresenta visivamente un’attività o una feature.
Contiene informazioni come:

- il **riepilogo dell’incarico**,
- la **persona responsabile**,
- eventuali **scadenze** o **checklist**.

Nel caso di Logseq, le Cards sono **molto semplici**, spesso con pochi commenti e tag.
Per lavori più complessi, includono **liste di compiti** da completare.
Non sono invece definiti test espliciti da superare, anche se ogni lavoro viene **revisionato da un altro membro del team**.

#### 🔹 Kanban Board

Le Cards vengono organizzate in una **tabella Kanban**, uno strumento visivo che mostra lo stato dei lavori.
La board è divisa in **4 colonne**:

1. **To-Do**
2. **Doing**
3. **Done**
4. **Long Term**

📍 È consultabile pubblicamente su Trello:
👉 [Logseq Roadmap su Trello](https://trello.com/b/8txSM12G/logseq-roadmap)

Quando una Card viene creata, entra nella colonna **To-Do**.
Un membro del team può assegnarsela, spostandola in **Doing**.
Durante lo sviluppo, viene creato un **branch separato** dal *master* per lavorare sulla nuova feature.

Una volta completata, la Card entra nella fase di **Code Review**, dove un altro sviluppatore deve obbligatoriamente verificarla.
Esiste anche un parametro chiamato **List Limit**: se ci sono troppe Card in revisione, il team dà priorità alle review rispetto a nuovi lavori.

Dopo la revisione e i test, la Card viene spostata su **Done**, e il codice viene unito al branch principale.
Il rilascio avviene prima in **versione Early Access**, poi nella **versione stabile**.

#### 🔹 Caso speciale: la “Whiteboard”

Una menzione a parte merita la feature **Whiteboard**, progettata come una componente complessa ed esclusiva.
Per essa è stata creata una **Kanban Board dedicata su GitHub**:
👉 [Whiteboard Project Board](https://github.com/orgs/logseq/projects/2/views/1)

In passato, la Kanban principale si trovava su GitHub:
👉 [Vecchia roadmap (dismessa)](https://github.com/logseq/logseq/projects/1)
ma dal **2020** è stata spostata definitivamente su Trello.

### Bug

Anche per la gestione di **bug e problemi**, Logseq si affida molto alla **community**.
I developer prediligono la sezione **“Issues”** di GitHub per la segnalazione di fix o bug:

👉 https://github.com/logseq/logseq/issues

Per la risoluzione, sia i developer che la community possono lavorare direttamente sul codice e poi richiedere un **pull request** sul *master branch*.
Solitamente, di queste operazioni si occupano **membri interni del team** o sviluppatori selezionati.

È possibile anche utilizzare il **blog ufficiale** (che ha una sezione dedicata ai bug report) oppure i **canali Discord**, dove gli sviluppatori sono attivi e disponibili per assistenza diretta:

👉 Post ufficiale: Please post bug reports to GitHub if you can

------

### Ambito economico del progetto

Logseq è un progetto **open source** con licenza **AGPL-3.0**, quindi **completamente gratuito**.
Per supportare il team, è possibile effettuare **donazioni una tantum o ricorrenti** tramite la piattaforma **Open Collective**:

👉 https://opencollective.com/logseq

In base all’importo donato, si possono ottenere **vantaggi esclusivi**, come:

- accesso alle **versioni Early Access**,
- **badge su Discord**,
- **menzioni come sponsor** sul sito ufficiale e sulla pagina GitHub.

Il progetto è nato dalla mente del developer **Tienson**, inizialmente finanziato da **Angel Investors**.
Attualmente il team è composto da **10 developer**, con **compensi annuali** e una **quota di equity** sul progetto.

Inoltre, Logseq ha ricevuto investimenti da **grandi nomi del settore tech**, tra cui:
Airbnb, Instagram, Quora, Neuralink, SpaceX, Facebook, Stripe, GitHub, Shopify, Uber e AngelList.
(📄 Fonte: Design & Frontend Engineer – Notion Page)

Nonostante questo, il **reddito attuale non è ancora sufficiente**, e tra gli obiettivi futuri c’è quello di **aumentare la monetizzazione**.

Il team prevede infatti di lanciare una versione **Logseq Pro**, **a pagamento e closed source**, con vantaggi come:

- **database sincronizzato tra dispositivi** su server proprietari (sul modello di Roam Research),
- **feature esclusive** anche per chi sceglie di mantenere un database locale.

In futuro, quindi, Logseq si dividerà in due rami:

- **Logseq Pro** → closed source e a pagamento
- **Logseq Standard** → open source e gratuito, costantemente mantenuto

📚 Riferimenti:

- [FAQ ufficiale](https://docs.logseq.com/#/page/faq)
- [Discussione: What is Logseq’s business model?](https://discuss.logseq.com/t/what-is-logseqs-business-model/389/3)

------

### Community

La **community** gioca un ruolo fondamentale non solo nell’ideazione di nuove feature, ma anche nella **segnalazione di bug** e nella **collaborazione tecnica**.

Per quanto riguarda lo sviluppo, la community può contribuire **attraverso la creazione di plugin**.
Anche se, in teoria, chiunque può modificare il codice sorgente (essendo open source), la **branch principale (master)**rimane sotto il controllo del team ufficiale.

#### 🔹 Requisiti per i plugin

I plugin devono:

1. **Garantire privacy e sicurezza** dei dati dell’utente.
2. **Non duplicare funzionalità già presenti** nel programma.

Per pubblicare un plugin, basta creare un **fork** del repository e inviare una **pull request** al progetto *Marketplace Packages*su GitHub:
👉 https://github.com/logseq/marketplace

I plugin approvati vengono automaticamente inseriti nel **marketplace integrato** nel programma, completamente gratuito.

#### 🔹 Contributi alla documentazione

La community contribuisce anche alla **documentazione**, sia interna che esterna.

- **Documentazione interna:** tutorial e linee guida integrate nel programma.
  → Contributo via *fork + pull request* su GitHub.
- **Documentazione esterna:** articoli, guide e contenuti su blog o piattaforme esterne.
  → Partecipazione libera attraverso il forum.

📚 Riferimenti:

- How to contribute to Logseq’s documentation (post 1)
- How to contribute to Logseq’s documentation (post 2)

------

### Architettura

In origine, l’**architettura di Logseq** era **monolitica**: ogni nuova feature o componente interagiva direttamente con il **Datascript**, limitando la modularità e la scalabilità del codice.

Per risolvere questi problemi, il team ha effettuato un **profondo refactoring**.
Attualmente, Logseq è composto da due principali componenti:

1. **Logseq Plugin Core** – interfaccia tra i plugin e il sistema principale.
2. **Logseq Core** – motore dell’applicazione, gestisce editing, blocchi e funzioni base.

- I **plugin della community** interagiscono con il **Plugin Core**.
- Gli **Official Plugins**, invece, comunicano direttamente con il **Core** (es. motore di ricerca, temi base, ecc.).

Questa architettura modulare consente:

- maggiore **sicurezza** nell’esecuzione dei plugin,
- sviluppo più **isolato e indipendente** delle singole componenti,
- miglior **gestione degli errori** e **delle nuove feature**.

📚 Riferimento:
[The Refactoring of Logseq](https://docs.logseq.com/#/page/The Refactoring Of Logseq)

------

### Valori, metodologia di lavoro e correlazioni con l’XP

La filosofia e la metodologia di lavoro del team Logseq sono descritte nella seguente pagina:
👉 Who is Logseq – Notion

Pur non dichiarando esplicitamente l’adesione all’**Extreme Programming (XP)**, si possono notare **molte analogie**.

#### 🔹 Comunicazione

> “Noi condividiamo apertamente, ampiamente e deliberatamente e siamo straordinariamente sinceri gli uni con gli altri.”

Il team lavora **in modo asincrono**, da luoghi e fusi orari diversi.
La comunicazione avviene quindi tramite **note e messaggi scritti**, che rendono più diretto e veloce lo scambio di idee.

Tutti possono comunicare con chiunque — anche l’ultimo programmatore con il cliente — proprio come nel modello XP.
Questo approccio genera **feedback continui e immediati**, sia con la community sia all’interno del team.

📍 Forum: [https://discuss.logseq.com](https://discuss.logseq.com/)

#### 🔹 Valori condivisi

- **Coraggio e libertà di sperimentare:**

  > “Il rischio è direttamente proporzionale all’impatto.”
  > Come nell’XP, serve coraggio nel prendere decisioni importanti e nell’ammettere eventuali errori passati.

- **Ritmo sostenibile:**

  > “È una maratona, non uno sprint.”
  > Il lavoro è flessibile e bilanciato: ferie pagate, incentivi per studio e salute, piani assicurativi, ecc.

- **Action-Oriented:**
  Il team privilegia un approccio **pratico e iterativo**, con **release frequenti e leggere**.

📈 Esempio su GitHub:

- v0.8.2 → rilasciata 6 giorni fa
- v0.8.1 → 12 giorni fa
- v0.8.0 → 20 giorni fa
  👉 [Changelog su GitHub](https://github.com/logseq/logseq/releases)

#### 🔹 Organizzazione del lavoro

Il flusso di lavoro è strutturato come nell’XP:

- attività rappresentate da **Cards**,
- gestione tramite **tabella Kanban**,
- focus su **refactoring continuo** e miglioramento del codice.

Un grande refactoring ha già portato a un’architettura più pulita e performante, ma il team continua a ottimizzare:

- caricamento di pagine molto grandi,
- reattività delle query,
- uso della memoria oltre 10k note,
- gestione delle pagine lunghe.

📍 [Card di riferimento su Trello](https://trello.com/c/68pohS4z/1125-performance-improvement)

Il **core di Logseq** gestisce numerose operazioni su file, stringhe e caratteri Unicode, quindi la performance è un aspetto fondamentale e costantemente monitorato.

#### 🔹 Pair Programming

L’unico aspetto mancante rispetto all’XP è il **pair programming**, quasi impossibile da applicare in un team completamente remoto e asincrono.
Infatti, nella Kanban board, a ogni *Card* è solitamente assegnato **un solo sviluppatore**.

📚 Ulteriore riferimento:
[The Refactoring of Logseq](https://docs.logseq.com/#/page/The Refactoring Of Logseq)
