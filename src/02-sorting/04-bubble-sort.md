# Bubble sort

Un altro algoritmo di ordinamento molto semplice che vedremo ora è il _bubble sort_ (ordinamento a bolla).



L'algoritmo prende ispirazione dal fenomeno di sedimentazione: in un fluido composto da elementi di diversità diversa, con il tempo gli elementi più densi tenderanno ad andare verso il fondo e quelli meno densi verso la superficie.

Immaginiamo quindi che la nostra lista da ordinare sia una bottiglia d'olio, in cui il primo elemento corrisponde al fondo della bottiglia e l'ultimo elemento al tappo. Immaginiamo anche che gli elementi più grandi siano i più più leggeri (meno densi) e che per questo tendano ad andare come delle bolle verso la superficie.

<p class="centered">
<img class="w80p" src="assets/oil.jpg" alt="Sedimento" title="Sedimento">
</p>

Cerchiamo di emulare questo comportamento con un algoritmo:
- parto dal primo elemento (il fondo), e procedo passo passo verso la fine (il tappo)
- ad ogni passo confronto due elementi: se quello in basso è più grande di quello in alto (più leggero), li scambio, in modo da farlo "risalire" verso la superficie
- quando sono arrivato alla fine, ritorno dall'inizio e ricomincio finché non è tutto ordinato

Vediamo una prima implementazione di questa procedura.

```py
my_list = [7, 12, 18, 5, 6]
# scorro tutta la lista, partendo dal primo elemento
for index in range(len(my_list)):
        # per ogni elemento della lista da index fino alla fine
        for jdex in range(index, len(my_list)):
            # se l'elemento in index è maggiore di quello in jdex, li scambio
            if (my_list[index] > my_list[jdex]):
                my_list[index], my_list[jdex] = my_list[jdex], my_list[index]

print(my_list)
```
[<small>Versione online interattiva</small>](https://repl.it/@ClaudioCapobian/bubble-sort-simple)

Bene! Come potete vedere dalla versione online interattiva, questa versione funziona.

## Miglioramenti
Vediamo se riusciamo a migliorare l'algoritmo.

Possiamo osservare che, se quando prendiamo in esame un elemento e lo confrontiamo con tutti quelli sopra di lui, non c'è nessun elemento da scambiare, vuol dire che gli elementi sono già tutti quanti in ordine.

Con questa osservazione modifichiamo l'algoritmo in questo modo.
```py
for index in range(len(my_list)):
        # inizializziamo la variabile booleana di controllo "swapped" a False
        swapped = False
        for jdex in range(index, len(my_list)):
            if (my_list[index] > my_list[jdex]):
                my_list[index], my_list[jdex] = my_list[jdex], my_list[index]
                # se c'è anche un solo scambio, impostare la variabile di controllo a True
                swapped = True
        # solo se la variabile di controllo è rimasta False (quindi non c'è stato nessuno scambio), esco dal ciclo perché la lista è già ordinata
        if not swapped:
            break
```
[<small>Versione online interattiva</small>](https://repl.it/@ClaudioCapobian/bubble-sort-2)

## Calcolo della complessità
Proviamo a calcolare la complessità per il bubble sort.

### Caso medio e peggiore
Nel caso medio, abbiamo i seguenti passaggi:
- il ciclo esterno (indice `index`) viene ripetuto n volte
- per ogni iterazione del ciclo esterno, il ciclo interno (indice `jdex`) esegue n operazioni

Quindi nel caso medio:
<p class="centered">
complessità temporale caso medio = O(n*n) = O(n<sup>2</sup>)
</p>

Questo caso corrisponde anche al caso peggiore, in quanto l'algoritmo non può fare più operazioni di così.

### Caso migliore
Nel caso in cui la lista sia già ordinata, l'algoritmo se ne accorge con la variabile booleana di guardia "swapped".

In questo caso il ciclo interno (indice `jdex`) esegue n operazioni, mentre il ciclo esterno uscirebbe dopo la prima iterazione.

Quindi in questo caso:
<p class="centered">
complessità temporale caso migliore = O(n*1) = O(n)
</p>

Abbiamo trovato che il caso migliore per il bubble sort è O(n) e si ha quando la lista di partenza è già ordinata.

## Recap
| Bubble sort | complessità temporale |
|-------------|:-----:|
| caso migliore | O(n) |
| caso peggiore | O(n<sup>2</sup>) |
| caso medio | O(n<sup>2</sup>) |

