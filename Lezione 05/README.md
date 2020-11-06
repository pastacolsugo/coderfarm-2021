# Lezione 5
### [Esercizi per la prossima settimana](ESERCIZI.md)

# Indice
- [Tuple](#tuple)
  * [Quando usare una tupla e quando usare una lista?](#quando-usare-una-tupla-e-quando-usare-una-lista-)
  * [Unpacking](#unpacking)
  * [Utilizzi](#utilizzi)
- [Dizionari](#dizionari)
- [Operatore `in`](#operatore-in)

# Tuple

Le `tuple` sono un tipo di dato che può contenere al suo interno più valori, anche di tipi diversi.

Una tupla viene definita tramite le parentesi tonde:
```py
t = ("ciao", 123)
print(t)
```
in questo esempio `t` è una tupla con due elementi, il primo la stringa `"ciao"` e il secondo l'intero `123`.

È possible inserire più elementi di qualsiasi tipo all'interno di una tupla, inoltre ci sono certi casi in cui le parentesi tonde non sono obbligatorie in quanto python riconosce in automatico che si vuole creare una tupla solo separando con la virgola:

```py
# nell'assegnamento non è necessario mettere le parentesi
t = "ciao", 123, 567, (1, 2, 3)
print(t)
```

in questo esempio la tupla contiene 4 elementi. I primi due sono gli stessi di prima, il terzo è l'intero `567` e il quarto è a sua volta una tupla contenente tre interi (`1`, `2` e `3`).  
È quindi possibile anche avere tuple che contengono tuple (cosa che vale ovviamente anche per altri tipi di python, come le liste).

Le tuple potrebbero sembrare molto simili alle liste e in effetti è così, tuttavia ci sono delle differenze che fanno sì che vengano usate in contesti diversi.  
A differenza delle liste le tuple sono immutabili, una volta creata quindi una tupla non può più essere modificata: nessun elemento può essere aggiunto o cancellato e nemmeno modificato.

```py
t = 1, 2, 3
# è possibile accedere normalmente agli elementi di una tupla
print(len(t)) # 3
print(t[0]) # 1
# NON è però possibile modificarla
t.append(5) # ERRORE: append non esiste proprio per le tuple
t[0] = 5 # ERRORE: non è possibile modificare gli elementi di una tupla
```

## Quando usare una tupla e quando usare una lista?

Una tupla viene usata quando si ha un numero finito e noto di valori da memorizzare, al contrario una lista viene usata quando si ha un elenco potenzialmente infinito (o comunque di dimensione non nota) di valori.  

Per esempio un punto sul piano cartesiano lo rappresentiamo con una tupla contente la `x` e la `y` del punto perché sappiamo che avrà sempre e solo due valori.  
Invece una lista di voti la rappresentiamo appunto con una lista perché non sappiamo quanti ce ne saranno e magari vogliamo poter aggiungere un voto alla lista dopo essere stati interrogati.

Inoltre è spesso vero che le liste contengono al loro interno valori tutti dello stesso tipo (per esempio una lista di voti contiene tutti valori float al suo interno), invece succede spesso che le tuple abbiano valori di svariati tipi al loro interno (per esempio se volessimo associare un voto a una persona potremmo fare una tupla contenente come primo valore il nome della persona (stringa) e come secondo il voto (float)).

## Unpacking

Il modo principale con cui si accede ai valori all'interno di una tupla non è tramite indice (e quindi con le quadre) come si fa con le liste, bensì tramite unpacking:

```py
t = 1, 2, 3
a, b, c = t # unpacking di t nelle variabili a, b, c
print(a + b + c) # 6
```

Data una tupla è quindi possibile "decomporla" direttamente all'interno di delle variabili, l'importante è che il numero delle variabili sia uguale al numero di elementi all'interno della tupla.

Nell'esempio sopra alla variabile `a` viene assegnato `1`, a `b` viene assegnato `2` e a `c` viene assegnato `3`.

Potete vedere l'esempio sopra come se fosse circa equivalente al seguente codice:
```py
t = 1, 2, 3
a = t[0]
b = t[1]
c = t[2]
```
con la differenza che utilizzando l'unpacking viene eseguito tutto in una volta.

È anche possibile scrivere direttamente una tupla anche alla destra dell'assegnamento:

```py
a, b, c = 1, 2, 3
```
che è equivalente a:
```py
a = 1
b = 2
c = 3
```

Tutto ciò permette per esempio di scambiare il valore di due variabili senza la necessità di utilizzare una variabile temporanea intermedia:

```py
a = 1
b = 2
print(a, b) # 1 2
a, b = b, a # scambio il valore di a e b
print(a, b) # 2 1
```

## Utilizzi

Uno degli usi principali delle tuple è quello di permettere a una funzione di ritornare più di un valore.

Per esempio scriviamo una funzione che calcola la divisione con resto tra due numeri:

```py
def divisione_con_resto(dividendo, divisore):
    quoziente = dividendo // divisore
    resto = dividendo % divisore
    # ritorniamo una tupla contente quoziente e resto
    # in questo caso le parentesi tonde non sono necessarie
    # ma python capisce che è una tupla tramite la virgola
    return quoziente, resto

# possiamo fare unpacking per ottenere i due risultati
q, r = divisione_con_resto(5, 3)
print("5 diviso 3 fa", q, "resto", r) # 5 diviso 3 fa 1 resto 2
```

Un altro esempio di uso può essere per esempio voler memorizzare una lista di punti.  
Lo si può fare tramite una lista di tuple, dove ogni tupla contiene due interi:
```py
# lista di punti
points = [
    (1, 2),
    (5, -2),
    (0, 3),
]
# è possibile anche aggiungere punti alla lista
points.append((4, 5))

print(points)

# calcoliamo la distanza di ogni punto dall'origine
from math import sqrt
for point in points:
    x, y = point
    dist = sqrt(x**2 + y**2)
    print(x, y, dist)
```

Un altro esempio visto a lezione è un registro di voti.  
Si può rappresentare come una lista di tuple dove ogni tupla contiene il nome della persona e il voto ottenuto:

```py
# dato una lista (registro) dove ogni elemento
# è una tupla contenente nome e voto
# trovare tutti i voti di una persona con un dato nome
def trova_voti_persona(registro, nome):
    voti = []
    for persona, voto in registro:
        if persona == nome:
            voti.append(voto)
    return voti

registro = [
    ("samuele", 10),
    ("andrea", 4),
    ("samuele", 6),
    ("david", 8),
    ("gabriele", 7),
    ("david", 5),
]

print(trova_voti_persona(registro, "samuele")) # [10, 6]
print(trova_voti_persona(registro, "david")) # [8, 5]
print(trova_voti_persona(registro, "pietro")) # []
```

# Dizionari

Un dizionario è una struttura dati che permette di associare a una chiave un valore.

È simile a una lista nel senso che permette di memorizzare più valori, nella lista però ogni elemento è associato al proprio indice che dipende puramente dalla posizione, mentre invece in un dizionario ogni elemento è associato a una chiave decisa al momento dell'inserimento.

Un dizionario si costruisce utilizzando le parentesi graffe e separando chiave e valore tramite i due punti (`:`).
```py
# d è un dizionario
# alla chiave intera 5 è associata la stringa "ciao"
# alla chiave intera -2 è associato l'intero 10
# alla chiave stringa "cane" è associata la stringa "gatto"
d = {5: "ciao", -2: 10, "cane": "gatto"}
print(d) # {5: 'ciao', -2: 10, 'cane': 'gatto'}
```

notate come la chiave e il valore possano essere di svariati tipi, non solo interi per esempio.

È possibile accedere e modificare gli elementi del dizionario utilizzando le parentesi quadre, a differenza delle liste però l'indice dell'elemento non è la sua posizione bensì la chiave.

```py
d = {5: "ciao", -2: 10, "cane": "gatto"}

# accedo all'elemento con chiave 5
print(d[5]) # 'ciao'
# accedo all'elemento con chiave "cane"
print(d["cane"])

# aggiungo un nuovo elemento con chiave "banana" e valore "gialla"
d["banana"] = "gialla"
# modifico il valore di "cane" in "giraffa"
d["cane"] = "giraffa"

# possiamo vedere come le modifiche sopra si applicano al dizionario
print(d) # {5: 'ciao', -2: 10, 'cane': 'giraffa', 'banana': 'gialla'}

# se invece provo ad accedere a un elemento non esistente mi da errore
print(d[1]) # ERRORE: la chiave 1 non esiste all'interno del dizionario d
```

Un esempio di utilizzo di un dizionario può essere quello di associare a un certo utente la sua password:  
_(Ovviamente questo non è in alcun modo sicuro ed è solo fatto a scopo dimostrativo. Nella vita reale le password vengono gestite maniera differente (si spera).)_

```py
# si può creare un dizionario vuoto non mettendo niente tra le graffe
password_utenti = {}

# esempio di aggiunta di utenti
password_utenti["samuele"] = "python"
password_utenti["ugo"] = "gattino42"

# esempio modifica password
# (anche se nella vita reale prima bisognerebbe controllare che l'utente conosca la vecchia password)
password_utenti["samuele"] = "giraffa"

# esempio login
username = input("Inserisci il nome utente: ")
password = input("Inserisci la password: ")
if password == password_utenti[username]:
    print("Bravo, la password è corretta!")
else:
    print("Password errata :(")
```

# Operatore `in`

Ci è capitato più volte di fare un esercizio nel quale dovevamo controllare se un certo valore era presenta in una lista e lo abbiamo risolto con un ciclo `for`.

C'è un realtà un modo più semplice per farlo in python e cioè utilizzando l'operatore `in`:

```py
l = [1, 2, 3]
print(1 in l) # True
print(4 in l) # False
```

In generale `in` permette di verificare la presenza di un elemento all'interno di una sequenza e non funziona solo con le liste ma anche con altri tipi di dato che contengono più valori al loro interno.

È infatti possibile utilizzarlo nello stesso modo anche con le tuple:
```py
t = 1, 2, 3
print(1 in t) # True
print(4 in t) # False
```

Ma soprattutto è possibile utilizzarlo con i dizionari, dove dice se una determinata chiave è presente o meno all'interno di un dizionario:
```py
d = {"a": 1, "b": 2}
print("a" in d) # True
print("c" in d) # False
```

Potreste aver notato che nell'esempio login, python da errore nel momento in cui inseriamo un utente non esistente in quanto tenta di accedere al dizionario con una chiave non presente.

Un nodo per risolvere questo problema è per l'appunto di controllare l'esistenza del utente all'interno del dizionario prima di leggerne la password:

```py
username = input("Inserisci il nome utente: ")
# se l'utente esiste (cioè se è presente all'interno del dizionario)
if username in password_utenti:
    password = input("Inserisci la password: ")
    if password == password_utenti[username]:
        print("Bravo, la password è corretta!")
    else:
        print("Password errata :(")
else:
    print("Questo utente non esiste :(")
```