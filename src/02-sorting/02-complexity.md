# Complessità

Nella terminologia degli algoritmi di ordinamento, aumentare l'_efficienza_ significa ridurre la _complessità_ di un algoritmo. Meno è complesso l'algoritmo, più sarà efficiente.

<p class="centered">
Minore complessità -> Maggiore efficienza
</p>

Nella definizione di _complessità_, dobbiamo fare riferimento come sempre ai due componenti fondamentali di un sistema di elaborazione:

- processore (CPU)
- memoria primaria (RAM)

Ridurre la complessità relativa alla CPU significa riuscire ad arrivare allo stesso risultato (l'array ordinato) con meno operazioni, e quindi in meno tempo. Questo tipo di complessità viene quindi detta _computazionale_ o _temporale_.

Ridurre la complessità relativa alla RAM significa occupare meno "spazio" in memoria RAM possibile, quindi viene detta anche complessità _spaziale_.

## Misura della complessità
Quando calcoliamo la complessità temporale o spaziale, non ci interessa avere il numero esatto di operazioni o l'esatta quantità di memoria occupata, ma ci basta sapere "più o meno" quanto tempo ci metterà e quanta memoria occuperà. Questo valore approssimato viene detto _ordine di grandezza_. Esiste una simbologia specifica che serve ad indicare l'ordine di grandezza, ed è la notazione _[O-grande](https://it.wikipedia.org/wiki/O-grande)_, che si scrive _O(n)_.

Ad esempio, immaginiamo che, per un'attività didattica, al professore servano degli smartphone e li chieda agli studenti della classe. Quanti smartphone più o meno si può aspettare di trovare in classe? Possiamo ipotizzare che ogni studente avrà il proprio dispositivo (alcuni forse ne avranno due, alcuni nessuno), quindi l'ordine di grandezza del numero di smartphone è _circa_ pari a quello degli studenti. Se gli studenti sono un numero _n_ (es. 20), i dispositivi nella classe saranno anch'essi circa _n_. In questo caso si dice che il numero di smartphone nella classe è _O(n)_ (si legge "o di enne"), dove n è il numero di studenti.

Immaginiamo ora di voler organizzare un torneo di ping pong tra gli studenti di una classe. Vogliamo che tutti gli studenti giochino contro tutti gli altri studenti. Quante partite dovremo pianificare, più o meno? Se ci sono _n_ studenti ed ognuno deve fare circa _n_ partite, il numero di partite è (circa) _n * n = n<sup>2</sup>_. In notazione O grande, si dice che il numero di partite è _O(n<sup>2</sup>)_. Anche qui il numero di partite non sarà _esattamente_ n<sup>2</sup>, ma a noi serve sapere una stima approssimativa.

## Complessità computazionale (o temporale)
Tornando al grafico del selection sort, abbiamo visto che il tempo necessario per l'ordinamento va come il quadrato del numero di elementi da ordinare. Se indichiamo con _n_ il numero di elementi della lista, possiamo quindi dire che:

<p class="centered">
 tempo di ordinamento selection sort = O(n<sup>2</sup>)
</p>

con n = numero di elementi della lista.

Il nostro obiettivo sarà trovare degli algoritmi che abbiano una relazione tra tempo e numero di elementi più vantaggiosa.

## Complessità spaziale
Con la nostra implementazione del selection sort, in memoria RAM ci serve l'array `sorted_list` della stessa grandezza dell'array di partenza. La complessità spaziale è quindi:

<p class="centered">
 O(n)
</p>

Questa complessità è buona, e non possiamo ottenere ordini di grandezza migliori.

Ciò non toglie che possiamo comunque "limare" la nostra soluzione per guadagnare un po' di memoria. Lo vedremo nella prossima pagina.