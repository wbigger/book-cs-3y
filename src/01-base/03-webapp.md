# Creare una web app con HTML5 e Python
Anche se non è un tipico metodo di insegnamento, vorrei collegarmi subito a quello che state studiando in TPSI quest'anno e creare una semplicissima applicazione con HTML e Python.

## Caso di studio
Immaginiamo di voler gestire una biblioteca scolastica. Da un lato ci serve del codice che gira da qualche parte nel cloud che gestisce la biblioteca, ed una pagina web per poter visualizzare la lista dei libri.

Useremo Python per la prima parte (server), e HTML per la seconda parte (pagina web).

<svg height='140' width='100%'>
   
   <rect width='40%' height='100%' style='fill:rgb(0,0,0);stroke-width:3;stroke:rgb(0,0,0)'/>

   <text x="15%" y="50%" font-size="30" text-anchor="middle" fill="white">
   HTML
   </text>

   <rect width='40%' height='100%' style='fill:rgb(0,255,0);stroke-width:3;stroke:rgb(0,0,0)' x="60%"/>

   <text x="75%" y="50%" font-size="30" text-anchor="middle" fill="white">
   Python
   </text>
</svg>

## Python
Immaginiamo in maniera veramente minimale che il nostro catalogo sia formato solo dal seguente file Python, a cui diamo il nome di `library.py`.

```py
# library.py
catalogue = ["Harry Potter e il calice di fuoco", "Il rosso e il nero", "Il piccolo principe"]
```

Più essenziale di così, si muore... eppure è un codice valido e funzionante.

### Web server
Per poterlo far comunicare con la pagina HTML però, mi serve qualcuno che faccia da intermediario. Non posso infatti chiamare del codice Python direttamente dalla pagina web! Le pagine web possono infatti interagire unicamente tramite dei link, o più precisamente degli URL, e noi ancora non abbiamo nulla del genere.

L'intermediario che mette in comunicazione pagina web e codice sul server si chiama, in modo non troppo sorprendente, **web server**. Vediamo come si fa su Python.

Esistono diverse librerie che forniscono un web server, noi in questo tutorial useremo [Flask](https://www.palletsprojects.com/p/flask/), che è estremamente leggero e semplice da usare, anche se magari non ha tutte le funzionalità che offrono altre librerie.

Essendo una libreria esterna non di sistema, bisogna prima di tutto installarla. Come abbiamo visto, apriamo un terminale e scriviamo:
```
pip3 install flask
```

et voilà! La libreria è installata e pronta all'uso.

Ora creiamo un nuovo file nel nostro progetto, che chiamiamo `app.py`. Attenzione: il nome deve essere esattamente questo, altrimenti non funziona tutto automagicamente 🎩.

```py
from flask import Flask
from library import catalogue
import json

app = Flask("marconi")

@app.route("/")
def data_book():
    return json.dumps(
        [book for book in full_catalogue]
        )
```

Vediamo cosa abbiamo fatto. Abbiamo importato `Flask` e il nostro catalogo dal file che abbiamo creato precedentemente. Importiamo anche la libreria di sistema `json`, che è utile per convertire le variabili Python nel formato stringa JSON (vedi dopo. 

La riga `app = Flask("marconi")` crea un web server e gli da il nome di "marconi" (potevamo mettere quello che preferivamo).

La riga `@app.route("/")` è un'annotazione: sta ad indicare che la funzione successiva deve essere chiamata quando qualcuno prova ad accedere alla pagina web.

La funzione `data_book()` viene quindi chiamata quando interroghiamo il web server. Questa funzione ritorna il nostro catalogo in formato JSON.

### Il formato JSON
Fate attenzione: [JSON](https://www.json.org/) è un formato per scambiarsi i dati tra macchine (machine-to-machine), ma che può essere letto e scritto abbastanza facilmente anche dagli esseri umani. JSON quindi non è un codice, o un'applicazione, o una libreria, ma è un formato di stringa che permette alle macchine di comunicare fra loro in modo comprensibile. Volendo fare un paragone con la lingua umana, è come la sintassi della frase: per capirsi le persone devono mettere nel corretto ordine soggetto, verbo e complementi, altrimenti non ci si capisce.

JSON usa le seguenti convenzioni:
- le parentesi graffe per definire gli oggetti
- le parentesi quadre per le liste
- la virgola per separare gli elementi di una lista
- i due punti per definire le proprietà di un oggetto

Ad esempio, per definire una lista di due oggetti, ognuno con le proprietà `title` e `author`, scriveremo:
```json
[
    {
        "title":"Harry Potter e il calice di fuoco",
        "author":"J.K.Rowling"
    },
    {
        "title":"Il rosso e il nero",
        "author":"Stendhal"
    },
    {
        "title":"Il piccolo principe",
        "author":"Antoine de Saint-Exupéry"
    }
]
```
Per generare o validare stringhe JSON, è possibile usare servizi online come ad esempio [JSON lint](https://jsonlint.com/?json=[{%22title%22:%22Harry%20Potter%20e%20il%20calice%20di%20fuoco%22,%22author%22:%22J.K.Rowling%22},{%22title%22:%22Il%20rosso%20e%20il%20nero%22,%22author%22:%22Stendhal%22},{%22title%22:%22Il%20piccolo%20principe%22,%22author%22:%22Antoine%20de%20Saint-Exup%C3%A9ry%22}]).

### Lanciare il web server
Per lanciare il web server, aprite un terminale nella cartella del vostro progetto e scrivete:

```
python3 -m flask run
```
Se tutto va bene, vi dovrebbe comparire la scritta "Running on http://127.0.0.1:5000/". Ecco quindi il link che ci serviva per far comunicare la pagina web con la nostra applicazione!

## HTML
