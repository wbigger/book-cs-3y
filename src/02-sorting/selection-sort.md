# Un primo algoritmo

Per cominciare, ipotizziamo di avere una lista di numeri e di volerli mettere in ordine crescente.

```py
my_list = [7, 12, 18, 5, 6]
```

Creiamo una nuova lista vuota, che conterrà gli elementi ordinati.

```py
sorted_list = []
```

Una strategia che possiamo per l'ordinamento è scorrere tutta la lista originale e cercare il valore più basso, e copiarlo nella nuova lista.

```py
min_val = min(my_list)
sorted_list.append(min_val)
```

OK, ora dobbiamo ripetere queste istruzioni per tutti gli elementi della lista originale.

```py
for _ in range(len(my_list)):
    min_val = min(my_list)
    sorted_list.append(min_val)
```

Proviamo a vedere cosa succede se stampiamo la lista ordinata.

```py
>>> print(sorted_list)
[5, 5, 5, 5, 5]
```

Abbiamo una lista della stessa lunghezza dell'originale, ma tutti gli elementi sono il valore minimo 🤔. In effetti, ogni volta che trovo un valore minimo lo devo togliere dalla lista originale, per evitare che venga trovato sempre quello quando faccio il minimo! 

Il nuovo algoritmo diventa quindi così:

```py
for _ in range(len(my_list)):
    min_val = min(my_list)
    sorted_list.append(min_val)
    my_list.remove(min_val)
```

Se stampo il risultato ottengo:
```
>>> print(sorted_list)
[5, 6, 7, 12, 18]
```

Bene, ha funzionato!! Ho creato il mio primo algoritmo di ordinamento 😊.

## Osservazioni
Se è così facile ordinare una lista, perché se ne parla tanto? Il fatto è che quando la lista cresce di dimensioni, le risorse necessarie per poterla ordinare può crescere in maniera vertiginosa, rendendo nella pratica impossibile l'ordinamento stesso oppure molto svantaggioso.

Proviamo ad esempio ad usare il nostro algoritmo per liste di lunghezza diversa e calcoliamo il tempo che ci mette l'algoritmo per ordinare la lista.

<p class="centered">
<img class="w80p" src="assets/selection-sort.png" alt="Selection sort" title="Selection sort">
</p>

Nel grafico vediamo il tempo (in secondi) che ci mette l'algoritmo per ordinare liste di lunghezza 10000, 20000, 30000, 40000, 50000 elementi. Possiamo vedere che il tempo aumenta in modo non lineare, ovvero al raddoppiare degli elementi aumenta più del doppio. Facendo un'analisi un po' più approfondita, si può vedere che l'andamento è esponenziale, e in particolare il tempo aumenta come il quadrato degli elementi della lista: al raddoppiare degli elementi, il tempo aumenta di quattro volte.

Questo è un bel problema, perché se ho liste di milioni o miliardi di elementi, il tempo di ordinamento può schizzare a valori proibitivi. 

Per questo si cercando degli algoritmi più efficienti. Prima di andare avanti però è necessario dare una definizione della parola "efficiente".


