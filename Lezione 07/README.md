# Lezione 7

Ho utilizzato l'inizio della lezione per fare installare a tutti un ambiente di sviluppo Python nel proprio computer. In questo modo sarà possibile fare cose più interessanti e avere un'alternativa a repl.it quando non funziona.

Invito tutti quelli che non c'erano a installare nel vostro computer:  
- Python 3: lo potete scaricare dal sito ufficiale [python.org](https://www.python.org).  
_Vi consiglio di scaricare l'ultima versione disponibile che in questo momento è la 3.9.0 e, se vi permette di scegliere, la versione a 64bit._
- Visual Studio Code: anche questo lo trovate al suo sito ufficiale [code.visualstudio.com](https://code.visualstudio.com/).  
_È un ottimo editor per programmare e supporta tantissimi linguaggi di programmazione tra cui Python. Durante le lezioni io userò questo e quindi consiglio di fare lo stesso anche a voi. Ci sono alternative (tipo PyCharm) che potete ovviamente usare nel caso le preferiate._

# Indice
- [Disuguaglianze tra valori non numerici](#disuguaglianze-tra-valori-non-numerici)
- [Ordinamento](#ordinamento)
- [Indici negativi](#indici-negativi)
- [min/max](#minmax)
- [Esercizio: valore più frequente](#esercizio-valore-più-frequente)

# Disuguaglianze tra valori non numerici
Dovrebbe essere scontato per tutti il fatto che `2 > 1` sia vero e che `1 > 2` sia falso.  
Cosa succede però quando proviamo a confrontare valori che non sono numeri?

Parlando delle stringhe viene circa rispettato l'ordine alfabetico, quindi per esempio `"casa" < "zaino"` e `"cena" > "casa"` sono vere.  
Attenzione però che c'è differenza tra le lettere maiuscole e minuscole. In modo particolare quelle maiuscole vengono considerate come se venissero prima, quindi per esempio `"Zaino" < "casa"`.

Succede in realtà una cosa analoga per quanto riguarda anche le altre sequenze di valori (quindi per esempio liste e tuple):
- viene controllato il primo valore,
- se il primo valore della prima sequenza è maggiore rispetto a quello della seconda, allora la prima viene considerata maggiore,
- se invece il primo valore della prima sequenza è minore rispetto a quello della seconda, allora la prima viene considerata minore,
- nel caso in cui siano uguali si ripete lo stesso ragionamento per il secondo valore e così via.

Quindi per esempio è vero che `[1, 2] < [2, 3]` semplicemente perché `1` è minore di `2` e analogamente è vero che `[1, 2] < [2, 0]`.  
Nel caso invece di `[1, 2] < [1, 3]` è vero perché `2` è minore di `3`, cioè viene controllato il primo valore, ma dato che è uguale in entrambe le liste si considera quello in seconda posizione.

Anche per le stringhe vale questo procedimento e come valore di confronto utilizzano il valore con cui viene salvato il carattere in memoria. Per quanto riguarda i caratteri del nostro alfabeto potete controllare [questa tabella](http://www.asciitable.com) per sapere quali caratteri vengono considerati "più piccoli" di altri.  
In modo particolare potete verificare come le lettere e i numeri siano in ordine alfabetico e che le lettere maiuscole hanno valori più piccoli di quelle minuscole.

# Ordinamento

Spesso può essere comodo ordinare in ordine crescente o decrescente una sequenza di valori. In python è presente una funziona apposita per fare questo chiamata `sorted`:
```py
l = [4, 6, 2, 1, 7, 2]
print(sorted(l)) # [1, 2, 2, 4, 6, 7]
```
È possibile settare l'argomento `reverse` a `True` per invertire l'ordine di ordinamento e passare quindi da crescente a decrescente.

```py
l = [4, 6, 2, 1, 7, 2]
print(sorted(l, reverse=True)) # [7, 6, 4, 2, 2, 1]
```

In generale è possibile ordinare non solo liste di numeri, ma di qualsiasi tipo che sia confrontabile (come descritto sopra):

```py
l = [(3, 5), (2, 9), (5, 1)]
print(sorted(l)) # [(2, 9), (3, 5), (5, 1)]
print(sorted(l, reverse=True)) # [(5, 1), (3, 5), (2, 9)]
```

# Indici negativi

In python è possibile utilizzare indici negativi per accedere ai valori di una lista partendo dalla fine.

Quindi per ottenere l'ultimo elemento di una lista si può utilizzare l'indice `-1`, per il penultimo `-2` e così via.

```py
l = [3, 5, 4]
print(l[-1]) # 4
print(l[-2]) # 5
# accedere a un indice negativo è equivalente a accedere
# a quell'indice più la lunghezza della lista
print(l[len(l) - 1]) # 4
```

# min/max

Se volessimo ottenere il valore più piccolo o più grande all'interno di una lista senza scrivere troppo codice, un'idea potrebbe essere quella di ordinarla e poi prendere il primo/ultimo elemento.  
Mettere in ordine tutti i valori per poi interessarci solo a uno è però un po' uno spreco ed è ovviamente meno efficiente rispetto a semplicemente scorrere tutta la lista alla ricerca del nostro valore.

Essendo la ricerca del massimo e del minimo un'operazione molto comune in python esistono delle apposite funzioni: `min` e `max`.
```py
l = [4, 6, 2, -4, 3, 1]
print(min(l)) # -4
print(max(l)) # 6
```

# Esercizio: valore più frequente
Scrivere una funzione che, data una lista, ritorna il valore più frequente al suo interno.  
Simile a [un esercizio vecchio](/Lezione%2002/ESERCIZI.md#trova-il-numero-pi%C3%B9-frequente), tuttavia ora abbiamo le conoscenze per scrivere una soluzione ottimale.

<details> 
  <summary><b>Soluzione base (clicca per mostrare)</b></summary>

```py
def most_frequent(l):
    # costruiamo un dizionario delle frequenze
    # con gli elementi della lista come chiave e la loro frequenza come valore
    freq = {}
    for x in l:
        if x in freq:
            freq[x] = freq[x] + 1
        else:
            freq[x] = 1
    # poi cerchiamo manualmente qual è quello più frequente
    m = l[0]
    for x in freq:
        if freq[x] > freq[m]:
            m = x
    return m
```

</details>
<details> 
  <summary><b>Soluzione sort (clicca per mostrare)</b></summary>

```py
def most_frequent(l):
    # costruiamo un dizionario delle frequenze
    # con gli elementi della lista come chiave e la loro frequenza come valore
    freq = {}
    for x in l:
        if x in freq:
            freq[x] = freq[x] + 1
        else:
            freq[x] = 1
    # estraiamo le coppie chiave-valore (elemento-frequenza) dal dizionario
    # e le inseriamo in una lista, mettendo però prima la frequenza
    # così da poter confrontare prima per frequenza
    l_freq = []
    for x, f in freq.items():
        l_freq.append((f, x))
    # ordiniamo in ordine decrescente per la frequenza
    s = sorted(l_freq, reverse=True)
    # prendiamo il primo, cioè quello più frequente
    max_f, max_x = s[0]
    return max_x
```

</details>
<details> 
  <summary><b>Soluzione sort + indice negativo (clicca per mostrare)</b></summary>

```py
def most_frequent(l):
    # costruiamo un dizionario delle frequenze
    # con gli elementi della lista come chiave e la loro frequenza come valore
    freq = {}
    for x in l:
        if x in freq:
            freq[x] = freq[x] + 1
        else:
            freq[x] = 1
    # estraiamo le coppie chiave-valore (elemento-frequenza) dal dizionario
    # e le inseriamo in una lista, mettendo però prima la frequenza
    # così da poter confrontare prima per frequenza
    l_freq = []
    for x, f in freq.items():
        l_freq.append((f, x))
    # ordiniamo in ordine crescente per la frequenza 
    s = sorted(l_freq)
    # prendiamo l'ultimo, cioè quello più frequente 
    max_f, max_x = s[-1]
    return max_x
```

</details>
<details> 
  <summary><b>Soluzione max (clicca per mostrare)</b></summary>

```py
def most_frequent(l):
    # costruiamo un dizionario delle frequenze
    # con gli elementi della lista come chiave e la loro frequenza come valore
    freq = {}
    for x in l:
        if x in freq:
            freq[x] = freq[x] + 1
        else:
            freq[x] = 1
    # estraiamo le coppie chiave-valore (elemento-frequenza) dal dizionario
    # e le inseriamo in una lista, mettendo però prima la frequenza
    # così da poter confrontare prima per frequenza
    l_freq = []
    for x, f in freq.items():
        l_freq.append((f, x))
    # prendiamo direttamente il maggiore
    max_f, max_x = max(l_freq)
    return max_x
```

</details>