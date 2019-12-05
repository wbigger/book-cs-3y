# Tipi

Tutto comincia con i tipi. 

Per dare una forma ed un senso a quello che ci circonda, dobbiamo poter _assegnare_ a quello che ci percepiamo un _nome_ che rappresenta una categoria, un insieme di proprietà e caratteristiche che accumunano un qualcosa ad altre cose che conosciamo già. Questo "nome comune" di cosa, persona o animale" che ci ricorda i nostri studi elementari e che ha posto le basi alla nostra comprensione della lingua parlata e scritte, si ripropone ora all'inizio dei nostri studi dei linguaggi di programmazione. Questi nomi in programmazione prendono il nome di _tipi_.

## Tipi fondamentali
Esistono alcuni tipi che, più o meno universalmente, costituiscono i mattoncini base per tutti gli altri tipi nella programmazione. Questi tipi rappresentano delle caratteristiche base di ciò che ci circonda.

Guardiamoci intorno. Io adesso sono ne salotto di casa mia. Cosa vedo? Cosa sento? Cosa percepisco? Vedo una libreria con un certo numero di libri dentro. Sento una musica a basso volume. Sento un po' caldo. Vedo una tastiera con tanti caratteri scritti sopra, ed uno schermo con tante parole. 

I tipi fondamentali sono:
 - numeri interi: per rappresentare qualcosa che nella nostra descrizione del mondo non può essere diviso o non ci interessa che sia diviso. Ad esempio il numero di libri nella libreria.
 - numeri decimali: per rappresentare qualcosa che ha un valore continuo e divisibile. Ad esempio il volume della musica, la temperatura della stanza.
 - caratteri: per rappresentare un singolo carattere, numero o in generale simbolo. Ad esempio i singoli caratteri che vediamo sulla tastiera: `i`, `7`, `€`, etc.
 - stringhe: per rappresentare una sequenza di caratteri. Ad esempio una stringa può essere una parola sullo schermo, o un'intera riga, o il titolo di un libro, etc.
 - liste: per rappresentare un insieme di cose. Ad esempio la lista di tutti i libri che si trovano nella libreria.
- boolean: per cose che possono essere solo vere o false. Ad esempio se la luce è accesa o spenta.


Di seguito un approfondimento su alcuni tipi sopra descritti.

### Numeri interi
In matematica, i [numero interi](https://it.wikipedia.org/wiki/Numero_intero) possono essere o naturali (zero e i numeri positivi: 0,1,2,3,... ) e relativi (numeri naturali più numeri negativi: ...,-3,-2,-1,0,1,2,3,...). Non c'è un limite inferiore o superiore al valore che un certo numero può assumere

In informatica, oltre a questo, dobbiamo fare i conti anche con le risorse finite della macchina su cui operiamo. Dobbiamo quindi sempre tener presente che un certo numero intero, occuperà in base alla sua grandezza un certo numero di byte in memoria. Il numero di byte che tipicamente può assumere un intero in memoria è: 1 byte, 2 byte, 4 byte o 8 byte. Un intero di 8 byte è sufficientemente enorme da rappresentare qualsiasi cosa, e di solito non ne servono di più.

Riassumendo, bisogna avere in mente due cose quando parliamo di interi:
- se il numero sarà sicuramente sempre positivo, o ha senso che possa essere negativo
- quant'è il valore massimo o minimo che nella pratica il numero può avere, che determina il numero di byte da riservare in memoria.

> In C/C++, il segno e la grandezza si dichiara esplicitamente. In Python, i numeri interi sono sempre con il segno ed il compilatore assegna automaticamente il numero di byte in base al valore.

### Numeri decimali
I numeri decimali sono quelli con la virgola, e vengono detti anche numeri a virgola mobile, o _floating point numbers_.

I numeri decimali in informatica sono sempre con il segno. Anche in questo caso dobbiamo però decidere il numero di byte che occupa in memoria. Il numero di byte che può assumere un numero decimale è: 4 byte o 8 byte. Anche in questo caso, un numero decimale di 8 byte può rappresentare bene praticamente qualsiasi cosa che conosciamo, e non servono più byte.

Nei processori a 64bit, la dimensione tipica dei numeri decimali è sempre 8 byte, che vengono detti anche _double precision floating point numbers_, o semplicemente _double_. Nei processori a 8, 16 o 32 bit, per motivi di performance di solito si assegnano 4 byte e solo in caso di necessità se ne assegnano 8.

> Come per gli interi, in C/C++ bisogna dichiarare esplicitamente se un float occupa 4 o 8 byte. In Python occupa sempre 8 byte.

### Caratteri e stringhe
Per la rappresentazione dei caratteri bisogna fare più attenzione rispetto a quella degli interi perché esistono tanti standard diversi che co-esistono tra di loro. Semplificando, attualmente esistono due standard principali:
- [ASCII](https://it.wikipedia.org/wiki/ASCII): rappresenta i caratteri inglesi (senza accenti o altri segni diacritici), i numeri e alcuni simboli base come `@`, `!`, `#` e simili. Usa un byte di memoria e viene utilizzato in casi particolari o in vecchi sistemi
- [UTF-8](https://it.wikipedia.org/wiki/UTF-8: rappresenta i caratteri di tutte le lingue (italiano, spagnolo, cinese, indiano, sanscrito, greco antico, etc), i segni matematici, le emoji e tanti altri simboli. Usa un numero variabile di byte: per i caratteri più comuni (essenzialmente quelli ASCII) usa un solo byte, in tutti gli altri casi usa due byte. Alcuni esempi di caratteri UTF-8 sono:,`Ẽ`,`≢`,`©`,`∂`,`🌷`, etc.

### Boolean
Come abbiamo detto, un boolean rappresenta qualcosa che può essere o  solo vero o solo falso. Una variabile boolean può essere assegnata in uno dei seguenti modi:
- direttamente a vero o falso, ad esempio `a = True`
- come risultato di una operazione logica, ad esempio `a = 3 > 2`

Attenzione a non abusare del tipo boolean: usarlo solo quando concettualmente nel nostro mondo non possono esserci altri valori o valori intermedi. Ad esempio immaginiamo che nel nostro mondo ci sono sedie rosse e gialle. Mettere una variabile boolean del tipo `is_red`, che mi dice se la sedia è rossa, è una pessima idea. Primo perché non è chiaro cosa succede quando il valore è falso e secondo perché se domani arrivano delle sedie blu, devo cambiare tutto il codice :(

> Uno dei punti su cui variano molto i diversi linguaggi è come e se convertire altri tipi in boolean. Ad esempio, posso considerare il valore `0` come falso, ed `1` come vero? Posso dire che una lista vuota è falsa, ed una lista non vuota è vera? Oppure che una stringa vuota è falsa, ed una stringa non vuota è vera? Questo in informatica viene detto "Truthy and Falsy" del linguaggio. Per sapere cosa è vero e falso in Python leggete [qui](https://docs.python.org/2.4/lib/truth.html), in C++ leggete [qui](https://www.geeksforgeeks.org/bool-data-type-in-c/).

## Approfondimento: tipi statici, dinamici, deboli e forti
La caratteristica che probabilmente differenzia maggiormente i vari linguaggi di programmazione tra di loro, è come il linguaggio gestisce i tipi. Ci sono due assi su cui ci si può muovere:
- static vs dynamic
- weak vs strong

L'argomento è molto interessante ma anche altrettanto complesso, e richiede una buona conoscenza di come funziona la gestione della memoria, sia durante la compilazione che a runtime.

Questo piccolo paragrafo è solo per mettervi un po' di curiosità e farvi capire che l'oceano è grande :) Ne parleremo in modo più approfondito l'anno prossimo :D



