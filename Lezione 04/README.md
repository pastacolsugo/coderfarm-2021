# Lezione 4

### [Esercizi per la prossima settimana](ESERCIZI.md)
<br>

Questa lezione è stata per lo più di ripasso e esercitazione sulle cose viste le volte scorse.  
Abbiamo visto delle cose nuove sulle stringhe e sulla documentazione che riporto sotto.

# Indice
- [Introduzione agli esercizi](#introduzione-agli-esercizi)
- [Info sulle stringhe in Python](#info-sulle-stringhe-in-python)
  * [Liste di caratteri](#liste-di-caratteri)
  * [Funzioni delle stringhe](#funzioni-delle-stringhe)
- [Esercizi fatti a lezione](#esercizi-fatti-a-lezione)
  * [Esercizio 1](#esercizio-1)
  * [Esercizio 1.1](#esercizio-11)
  * [Esercizio 2](#esercizio-2)
  * [Esercizio 2.1](#esercizio-21)


# Introduzione agli esercizi

D'ora in poi molti esercizi che vi darò consisteranno nell'implementare una funzione.  
Non dovrete più quindi preoccuparvi di come leggere l'input dall'utente, ma semplicemente utilizzare gli argomenti passati alla vostra funzione.

Un esempio di un esercizio molto banale potrebbe essere il seguente:

```py
# Implementare la funzione somma che, dati due numeri come argomenti, ne ritorna la somma

def somma(a, b):
    ...

# Test
print(somma(1, 2)) # 3
print(somma(5, -3)) # 2
```

Il vostro scopo sarà quello di implementare la funzione somma, per cui di togliere i tre puntini e di sostituirli con del codice che fa quello che richiede la consegna, in questo caso ritornare la somma di `a` e `b`.  
Il mio consiglio è di copiare tutto il codice sopra in un nuovo file di Python e di modificare poi quello, così avete già tutte le cose funzionanti e dovete solo preoccuparvi di implementare la funzione.

In questo caso la soluzione dell'esercizio sarebbe:
```py
# Implementare la funzione somma che, dati due numeri come argomenti, ne ritorna la somma

def somma(a, b):
    return a + b

# Test
print(somma(1, 2)) # 3
print(somma(5, -3)) # 2
```

Notate che l'unica cosa che ho modificato è stato all'interno della funzione `somma`, dove ho semplicemente scritto `return a + b`.

Di seguito alla definizione delle funzione vi metterò sempre dei test, in modo che quando eseguite il codice potrete verificare subito se funziona e così non avete bisogno di richiedere i valori in input all'utente.

# Info sulle stringhe in Python

Per poter risolvere al meglio gli esercizi `2` e `2.1` torna comodo conoscere qualche cosa in più sulle stringhe.

## Liste di caratteri

Python memorizza le stringhe (circa) come se fossero delle liste di caratteri, per cui è possibile fare molte delle cose che si possono fare con le liste.  
Per esempio è possibile conoscerne la lunghezza tramite `len` e scorrere tutti i caratteri utilizzando il `for` oppure accedere al carattere in un certo indice utilizzando le parentesi quadre:

```py
s = "ciao"
print(len(s)) # 4

# printa ogni lettera in una nuova riga
# (si può leggere come "per ogni carattere c all'interno della stringa s")
for c in s:
    print(c)

print(s[0]) # c
```

Per certi tipi di utilizzo possiamo dire per esempio che la stringa `"ciao"` e la lista `["c", "i", "a", "o"]` sono equivalenti.

## Funzioni delle stringhe

Python mette a disposizione delle [funzioni (anche chiamate metodi) delle stringhe](https://docs.python.org/3/library/stdtypes.html#string-methods) che implementano per noi delle operazioni comuni.  
(questa cosa ovviamente non accade solo per le stringhe e pian piano ne vedremo altre)

Il posto migliore per poter scoprire tutti queste funzioni è la [documentazione ufficiale di Python](https://docs.python.org), all'interno della quale potete trovare la [pagina](https://docs.python.org/3/library/stdtypes.html) con i dettagli su tutti i tipi di default, all'interno della quale parla, tra le altre cose, delle stringhe (`str`).

Alcune funzioni interessanti:
- [`lower`](https://docs.python.org/3/library/stdtypes.html#str.lower): ritorna una nuova stringa con tutti i caratteri maiuscoli convertiti in minuscolo.  
    es. `"CIAO".lower()` -> `"ciao"` e anche `"ciAo".lower()` -> `"ciao"`
- [`upper`](https://docs.python.org/3/library/stdtypes.html#str.upper): è il contrario di lower, quindi converte tutti i caratteri minuscoli in maiuscoli.  
    es. `"ciao".upper()` -> `"CIAO"`
- [`split`](https://docs.python.org/3/library/stdtypes.html#str.split): divide una stringa in una lista di stringhe "tagliando" ogni volta che incontra il carattere separatore. Può essere usato per esempio per ottenere la lista di parole all'interno di una frase.  
    es. `"Ciao mi chiamo Samuele".split(" ")` -> `["Ciao", "mi", "chiamo", "Samuele"]`, in questo caso dividendo la stringa in funzione del carattere `" "` (spazio).
    ```py
    s = "20,50,5,-33"
    numeri = s.split(",") # questa volta splittiamo sulla virgola
    print(numeri) # ["22", "50", "5", "-33"]

    # Inizialmente tutti i numeri erano in una sola stringa ma ora che li abbiamo divisi
    # possiamo scorrerli tutti e per esempio calcolarne la somma
    somma = 0
    for numero in numeri:
        n = int(numero)
        somma = somma + n
    print(somma) # 42
    ```

# Esercizi fatti a lezione
Questi esercizi utilizzano un po' tutte le cose viste fin'ora e avevano lo scopo principale di allenarsi con le funzioni.

Se non eravate presenti a lezione vi invito a provare a fare gli esercizi prima di visualizzare le soluzioni.

Ovviamente queste non sono le uniche soluzioni possibili, se lo avete risolto in un altro modo va benissimo.

## Esercizio 1
```py
# Scrivi una funzione che prende come argomenti una lista e un valore 
# e ritorna quante volte quel valore compare nella lista.

def conta(l, v):
    ...

print(conta([1, 2, 3, 4, 1], 1)) # 2
print(conta([1, 2, 3, 4, 1], 7)) # 0
```

<details> 
  <summary><b>Soluzione (clicca per mostrare)</b></summary>

```py
# Scrivi una funzione che prende come argomenti una lista e un valore 
# e ritorna quante volte quel valore compare nella lista.

def conta(l, v):
    tot = 0
    for n in l:
        if n == v:
            tot = tot + 1
    return tot

print(conta([1, 2, 3, 4, 1], 1)) # 2
print(conta([1, 2, 3, 4, 1], 7)) # 0
```

</details>
<br>

## Esercizio 1.1
Questo esercizio lo dovete copiare in fondo al file dell'esercizio precedente.  
I due esercizi sono collegati in quanto vorrei che implementaste la funziona `contiene` sfruttando la funzione `conta` creata in precedenza.  
Cioè dovete chiamare la funzione `conta` all'interno della funzione `contiene` e sfruttare il suo valore di ritorno per decidere se il valore è contenuto o meno.
```py
# Scrivere una funzione che prende in input una lista e un valore e,
# sfruttando la funzione fatta in precedenza, 
# ritorna un bool che indica se il valore è presente o meno nella lista
# (quindi True se è presente e False se non lo è).

def contiene(l, v):
    ...

print(contiene([1, 3, 4, 5, 1], 1)) # True
print(contiene([1, 3, 4, 5, 1], 2)) # False
```

<details> 
  <summary><b>Soluzione (clicca per mostrare)</b></summary>

```py
# Scrivere una funzione che prende in input una lista e un valore e,
# sfruttando la funzione fatta in precedenza, 
# ritorna un bool che indica se il valore è presente o meno nella lista
# (quindi True se è presente e False se non lo è).

def contiene(l, v):
    c = conta(l, v)
    if c > 0:
        return True
    else:
        return False

print(contiene([1, 3, 4, 5, 1], 1)) # True
print(contiene([1, 3, 4, 5, 1], 2)) # False
```

</details>
<br>

## Esercizio 2

```py
# Scrivere una funzione che prende come argomento una lettera (stringa lunga 1)
# e ritorna un bool che dice se è una vocale o meno

def is_vowel(c):
    ...

print(is_vowel("a")) # True
print(is_vowel("A")) # True
print(is_vowel("b")) # False
print(is_vowel("e")) # True
print(is_vowel("9")) # False
```
<details> 
  <summary><b>Soluzione (clicca per mostrare)</b></summary>

```py
# Scrivere una funzione che prende come argomento una lettera (stringa lunga 1)
# e ritorna un bool che dice se è una vocale o meno

def is_vowel(c):
    # convertiamo il carattere in minuscolo per non dover aggiungere il doppio di condizioni
    # per includere anche le vocali in maiuscolo
    c = c.lower()
    if c == "a" or c == "e" or c == "i" or c == "o" or c == "u":
        return True
    else:
        return False

print(is_vowel("a")) # True
print(is_vowel("A")) # True
print(is_vowel("b")) # False
print(is_vowel("e")) # True
print(is_vowel("9")) # False
```

</details>
<br>

## Esercizio 2.1
Questo esercizio lo dovete copiare in fondo al file dell'esercizio precedente.  
Anche qui vorrei che implementaste `count_vowels` sfruttando la funzione `is_vowel`.

```py
# Scrivere una funzione che prende come argomento una stringa e,
# sfruttando la funzione fatta in precedenza, 
# ritorna il numero di vocali presenti al suo interno

def count_vowels(s):
    ...

print(count_vowels("ciao")) # 3
print(count_vowels("bbc")) # 0
```
<details> 
  <summary><b>Soluzione (clicca per mostrare)</b></summary>

```py
# Scrivere una funzione che prende come argomento una stringa e,
# sfruttando la funzione fatta in precedenza, 
# ritorna il numero di vocali presenti al suo interno

def count_vowels(s):
    tot = 0
    for c in s:
        if is_vowel(c):
            tot = tot + 1
    return tot

print(count_vowels("ciao")) # 3
print(count_vowels("bbc")) # 0
```

</details>
<br>

