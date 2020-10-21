# Lezione 3
### [Esercizi per la prossima settimana](ESERCIZI.md)

# Indice
- [Valori booleani (True/False)](#valori-booleani--true-false-)
- [break](#break)
- [for](#for)
- [Funzioni](#funzioni)

# Valori booleani (True/False)

Finora abbiamo visto che sia nell'`if` che nel `while` è possibile mettere delle condizioni di uguaglianza, tuttavia non abbiamo mai visto in che modo funzionano.

Gli operatori di confronto (es. `<`, `>`, `==`, etc..) non hanno in realtà nulla di speciale, se non che ritornano un tipo di dato chiamato `bool`.

Un `bool` è un tipo che può assumere solo due valori: `True` e `False` (rispettivamente vero e falso).  
Quindi per esempio `2 > 1` ritorna `True` mentre `2 < 1` ritorna `False`.

```py
print(2 > 1) # printa True
```

`while` e `if` semplicemente vogliono come condizione un valore booleano, è possibile utilizzare quindi qualsiasi espressione che ritorni un valore di tipo bool e non solo gli operatori di confronto.

È quindi possibile scrivere per esempio:
```py
if True:
    print("ciao")
```
anche se ha ovviamente poco senso in quanto è come se non ci fosse alcuna condizione e quindi printa `"ciao"`.

Più sensato è invece:
```py
while True:
    print("ciao")
```
che è un modo per fare un ciclo infinito.

# break

Dato che sopra abbiamo visto un modo per creare un ciclo infinito potrebbe tornare utile un modo per interrompere un ciclo.

`break` server proprio a questo: se utilizzato all'interno di un ciclo, ne esce immediatamente.

```py
i = 0
while True:
    if i == 10:
        break
    print(i)
    i = i + 1
```
che è equivalente a:
```py
i = 0
while i < 10:
    print(i)
    i = i + 1
```
ovviamente in questo esempio complica solo le cose e quindi pare stupido usarlo, però esistono casi in cui può tornare utile.

Per esempio, nell'esercizio della calcolatrice della settimana scorsa, era necessario leggere l'operatore e, nel caso fosse `"exit"`, bisognava interrompere il programma. Un modo per farlo potrebbe essere:
```py
while True:
    operatore = input("Inserisci un operatore: ")
    if operatore == "exit":
        break
    # qui ci andrà il codice in cui si chiedono gli operandi e si fanno i calcoli necessari
```

Oppure per leggere in input una lista di numeri fintanto che non viene inserito `0`:
```py
numeri = []
while True:
    n = float(input("Inserisci un numero (0 per terminare): "))
    if n == 0:
        break
    numeri.append(n)
print(numeri)
```

# for

Finora per scorrere gli elementi di una lista e in generale per fare cicli abbiamo sempre utilizzato il `while`. C'è però un altro modo che è molto spesso più comodo, il `for`.

Il concetto con cui funziona il `for` è abbastanza diverso: l'unica cosa che sa fare è iterare una lista e permetterci di fare qualcosa con ognuno degli elementi al suo interno.  
(_per quelli che già lo conoscono in `C/C++`_: il for in python è molto diverso da quello del C, per cui no date per scontato di conoscerlo già ema cercate di capirlo)

```py
numeri = [3, 2, 4]
for n in numeri:
    print(n) # questa print viene eseguita 3 volta, la prima printa 3, poi 2 e infine 4
```

A differenza del `while` qui non accediamo più alla lista tramite gli indici, bensì iteriamo tutti gli elementi e accediamo al loro valore direttamente.  
Nell'esempio sopra vengono printati tutti i valori all'interno della lista.

`for` è una keyword (appunto usata per dire che vogliamo fare un ciclo `for`),  
`n` in questo caso è il nome della variabile che ad ogni iterazione assumerà il valore di un elemento della lista,  
`in` è un'altra keyword e semplicemente fa parte della sintassi del `for`,  
`numeri` in questo caso è il nome della lista che vogliamo scorrere.

Possiamo leggere l'esempio sopra in italiano come "per ogni elemento `n` all'interno della lista `numeri`, printa `n`".

Per fare un paragone con il `while` potremmo immaginarci che l'esempio sopra venga tradotto così:
```py
numeri = [3, 2, 4]
i = 0
while i < len(numeri):
    n = numeri[i]
    print(n)
    i = i + 1
```

Questo codice fa la stessa identica cosa di quello sopra.  
Vorrei sottolineare come con il `while` sia necessario utilizzare gli indici per accedere al valore della lista e metterlo all'interno della variabile `n`, mentre invece con il `for` l'accesso viene fatto automaticamente e il valore viene scritto già dentro la variabile `n`.

Il codice scritto con il `for` è molto più facile da leggere e scrivere, per cui quando possibile è meglio utilizzare quello al posto del `while`.

Esempio somma numeri di una lista:

```py
numeri = [3, 2, 4]
somma = 0
for n in numeri:
    somma = somma + n
print(somma)
```

# Funzioni

Le funzioni sono un modo per dare un nome a dei blocchi di codice e permettere di riusarli.

Senza sapere bene cosa fossero abbiamo già usato delle funzioni. Per esempio `print`, `input`, `int`, `float`, `list.append`, `len` sono tutte delle funzioni.  
Semplificando, ogni volta che c'è un nome con di fianco delle parentesi tonde (esempio `print("ciao")`), abbiamo a che fare con una funzione.

Python ci mette già a disposizione delle funzioni di default ma è possibile creare delle nostre funzioni da utilizzare all'interno del nostro codice.

```py
def saluta():
    print("ciao, sono una funzione")
```
in questo modo abbiamo definito una funzione chiamata `saluta` che, quando eseguita, printa "ciao, sono una funzione".

`def` è una keyword che serve a dire a python che stiamo definendo una nuova funzione, successivamente dobbiamo scrivere il nome della funzione (in questo caso `saluta`) e poi ci vanno le parentesi tonde all'interno delle quali inseriremo gli argomenti (o parametri) della funzione.

Dopo averla definita è subito possibile utilizzare la funzione:
```py
# saluta due volte
saluta()
saluta()
```

<!--Una funzione può avere dei parametri e quindi richiedere all'utilizzatore di inserire degli argomenti quando la chiama:  
#(_nota_: nonstante non siano proprio la stessa cosa, utilizzerò i termini "parametri" e "argomenti" interscambiabilmente. Per semplicità, d'ora in poi cercherò di usare sempre "argomenti")-->
Una funzione può richiedere all'utente di inserire degli argomenti quando la chiama:

```py
def saluta(nome):
    print("ciao", nome)
```
in questo caso la funzione richiede un argomento chiamato nome che rappresenta il nome della persona da salutare.  
Quando la si chiama è quindi obbligatorio passare un nome:
```py
saluta("Samuele") # ciao Samuele
saluta("Ugo") # ciao Ugo
saluta() # da errore perché non abbiamo inserito l'argomento richiesto
```

È possibile avere più parametri in una funzione. Un esempio più complesso può essere:
```py
def saluto(nome, lingua):
    if lingua == 'italiano':
        print("ciao", nome)
    elif lingua == 'inglese':
        print("hi", nome)
    elif lingua == 'spagnolo':
        print("hola", nome)
    else:
        print("non conosco questa lingua")
```
Che si utilizza:
```py
saluto("Samuele", "italiano") # ciao Samuele
saluto("Ugo", "inglese") # hi Ugo
saluto("Stefano", "italiano") # ciao Stefano
```

Una funzione può anche ritornare un valore (come fa per esempio `input()` che ritorna la stringa inserita dall'utente piuttosto che `int()` che, data una stringa, la interpreta e ritorna un numero intero).

Per poter ritornare un valore si usa `return` seguito dal valore che si vuole ritornare:

```py
# funzione che prende come argomento una lista di numeri e ne ritorna la media
def media(lista):
    somma = 0
    for n in lista:
        somma = somma + n
    return somma / len(lista)
```

Che poi possiamo utilizzare come già siamo abituati con le altre funzioni:

```py
m = media([3, 5, 2, 1]) # il valore ritornato possiamo metterlo in una variabile
print(m) # 2.75
peint(m * 2) # farci delle operazioni sopra
print(media([9, 6, 2, 4])) # oppure anche printarlo direttamente
```

Le funzioni sono un ottimo modo per organizzare meglio il proprio codice ed evitare ripetizioni.  
Vi invito a trovare parti di codice che svolgono un ruolo ben preciso (un buon esempio è se dovete calcolare la media di una lista) e a "convertirle" in una funzione, questo vi permette sia di rendere pià leggibile il codice sia di poterle eventualmente riutilizzare per altri esercizi.  
È anche possibile condividere le proprie funzioni con gli altri, quindi per esempio se un vostro amico ha fatto una funzione per sommare tutti i numeri all'interno di una lista a voi basta copiare il codice e "magicamente" avete una funzione che fa quello che volevate senza neanche dover sapere in che modo funziona.

Esempio di una funzione che legge numeri in input dall'utente fintanto che non inserisce `0` e poi ritorna una lista contenente i numeri letti:

```py
def richiedi_numeri():
    numeri = []
    while True:
        n = float(input("Inserisci numero: "))
        if n == 0:
            break
        numeri.append(n)
    return numeri
```
È ovviamente possibile chiamare una funzione dall'interno di un'altra funzione.  
Esempio di somma e media numeri inseriti dall'utente sfruttando la funzione appena creata:

```py
def somma(numeri):
    somma = 0
    for n in numeri:
        somma = somma + n
    return somma

def media(numeri):
    return somma(numeri) / len(numeri)

def somma_numeri():
    # utilizzo la funzione creata precedentemente per chiede i numeri all'utente
    numeri = richiedi_numeri()
    print(somma(numeri))
    
def media_numeri():
    # utilizzo la funzione creata precedentemente per chiede i numeri all'utente
    numeri = richiedi_numeri()
    print(media(numeri))
```
