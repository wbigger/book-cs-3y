# Complessità

Nella terminologia degli algoritmi di ordinamento, aumentare l'_efficienza_ significa ridurre la _complessità_ di un algoritmo. Meno è complesso l'algoritmo, più sarà efficiente.

<p class="centered">
Minore complessità -> Maggiore efficienza
</p>

Nella definizione di _complessità_, dobbiamo fare riferimento come sempre ai due componenti fondamentali di un sistema di elaborazione:

- CPU (processore)
- RAM (memoria primaria)

Ridurre la complessità relativa alla CPU significa riuscire ad arrivare allo stesso risultato (l'array ordinato) con meno operazioni, e quindi in meno tempo. Questo tipo di complessità viene quindi detto _computazionale_ o _temporale_.

Ridurre la complessità relativa alla RAM significa occupare meno "spazio" in memoria RAM possibile, quindi viene detta anche complessità _spaziale_.

## Misura della complessità
Quando calcoliamo la complessità temporale o spaziale, non ci interessa avere il numero esatto di operazioni o l'esatta quantità di memoria occupata, ma ci basta sapere "più o meno" quanto tempo ci mette o quanta memoria occupa. Questo valore approssimato viene detto anche _ordine di grandezza_. Esiste una simbologia specifica che serve ad indicare l'ordine di grandezza, ed è la notazione _[O-grande](https://it.wikipedia.org/wiki/O-grande)_, la vedremo tra poco.

Ad esempio, immaginiamo che, per un'attività didattica particolare, al professore servano delle matite e le chiede agli studenti della classe. Quante matite più o meno si può aspettare di ricevere il docente? Possiamo ipotizzare che ogni studente avrà nell'astuccio circa una matita (alcuni due, alcuni nessuna), quindi l'ordine di grandezza del numero di matite è circa pari a quello degli studenti. Se gli studenti sono un numero _n_ (es. 20), le matite nella classe saranno anch'esse circa _n_. In questo caso si dice che il numero di matite nella classe è _O(n)_, dove n è il numero di studenti.

Immaginiamo ora di voler organizzare un torneo di ping pong tra gli studenti di una classe. Vogliamo che tutti gli studenti giochino contro tutti gli altri studenti. Quante partite dovremo pianificare, più o meno? Se ci sono _n_ studenti ed ognuno deve fare circa _n_ partite, il numero di partite è circa _n<sup>2</sup>_. In notazione O grande, si dice che il numero di partite è _O(n<sup>2</sup>)_. Da notare che il numero di partite non sarà _esattamente_ n<sup>2</sup>, ma a noi in questo momento interessa sapere un numero approssimativo.

## Complessità computazionale (o temporale)
Tornando al grafico del selection sort, abbiamo visto che il tempo necessario per l'ordinamento va come il quadrato del numero di elementi. Se indichiamo con _n_ il numero di elementi della lista, possiamo quindi dire che:
<p class="centered">
 tempo di ordinamento = O(n<sup>2</sup>) con n = numero di elementi della lista
</p>

Il nostro obiettivo sarà trovare degli algoritmi che abbiano una relazione tra tempo e numero di elementi più vantaggiosa.

## Complessità spaziale
Con la nostra implementazione del selection sort, in memoria RAM ci serve l'array `sorted_list` della stessa grandezza dell'array di partenza. La complessità spaziale è quindi:

<p class="centered">
 O(n)
</p>

Questa complessità è buona, e non possiamo ottenere ordini di grandezza migliori.

Ciò non toglie che possiamo comunque "limare" la nostra soluzione per guadagnare un po' di memoria. In particolare, possiamo evitare del tutto di creare l'array di appoggio `sorted_list` e ordinare direttamente l'array di partenza. Questo tipo di ordinamento che modifica direttamente l'array in input si chiama __ordinamento sul posto__ (in inglese _in place_).