# Selection sort: miglioramenti

## Ordinamento sul posto
Riprendiamo la nostra implementazione del selection sort finora.

```py
my_list = [7, 12, 18, 5, 6]
for _ in range(len(my_list)):
    min_val = min(my_list)
    sorted_list.append(min_val)
    my_list.remove(min_val)
```

Per ordinare la lista, abbiamo creato una nuova lista di appoggio `sorted_list`. Se l'array è molto grande questo potrebbe essere un problema. 

Possiamo risolvere questo problema spostando direttamente gli elementi dell'array di partenza, senza nessun array ausiliario: questo tipo di ordinamento che modifica direttamente l'array in input si chiama ordinamento __sul posto__ (in inglese _in place_).

Non ripeteremo qui la soluzione originale che abbiamo svolto in laboratorio, potete trovare tutto il codice [qui](https://gist.github.com/wbigger/dca17d4c1b2718897cfa6cb53631316f#file-sorting-selection-py).

## Calcolo della complessità temporale
Cerchiamo di calcolare perché questo algoritmo impiega un _O(n<sup>2</sup>)_ operazioni per ordinare l'array.

Analizziamo il codice, ricordando che `len(my_list)` è il numero di elementi della lista e quindi esattamente il nostro _n_.

```py
# Qui c'è un for: le operazioni al suo interno 
# vengono ripetute per n volte
for _ in range(len(my_list)):
    # per trovare il minimo, bisogna scorrere tutta
    # la lista, quindi servono circa n operazioni
    min_val = min(my_list)
    # append è un'operazione singola
    sorted_list.append(min_val)
    # remove può essere considerata come un'operazione singola
    my_list.remove(min_val)
```

Quindi, il numero di operazioni è:
- n operazioni per min
- 1 operazione per append
- 1 operazione per remove
- il tutto ripetuto per n volte

Mettiamo insieme le cose e abbiamo:

<p class="centered">
complessità temporale = (n+1+1)*n = (n+2)*n = n<sup>2</sup>+2*n
</p>

OK, ci siamo quasi. La nostra complessità ha due addendi: 
- n<sup>2</sup>
- 2*n

Quando n diventa molto grande, il primo termine cresce molto di più del secondo, e quindi il secondo si può trascurare.

Per dimostrazione, facciamo una prova ad esempio con `n = 1000`: 
- n<sup>2</sup> = 1000<sup>2</sup> = 1 milione
- 2*n = 2000

Considerando che stiamo facendo dei calcoli approssimati, possiamo tranquillamente trascurare 2000 rispetto ad un milione!

Per la complessità temporale consideriamo solo il primo termine, e quindi otteniamo:

<p class="centered">
complessità temporale = O(n<sup>2</sup>)
</p>