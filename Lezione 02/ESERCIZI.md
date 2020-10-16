# Esercizi per casa

## Somma numeri
Chiedere numeri in input fintanto che l'utente non inserisce 0.  
Stampare in output la somma dei numeri inseriti.
### Esempi input/output
```
Inserisci un numero: 5
Inserisci un numero: 30
Inserisci un numero: -10
Inserisci un numero: 0
La somma dei numeri inseriti è 25
```

## Calcolatrice
Chiedere in input un operazione matematica e 2 numeri.  
Stampare il risultato dell'operazione sui due numeri.

Continuare fintanto che l'utente non inserisce `'exit'` come operatore.  
Supportare almeno le seguenti operazioni `+`, `-`, `*`, `/`. Se vi va potete aggiungere altre operazioni tipo `>` e `<` oppure potenza e radice quadrata.

_Extra_: permettere di utilizzare, al posto di uno dei due numeri, un simbolo rappresentante il valore del risultato precedente (similmente a come funziona `mem` sulla calcolatrice).
### Esempi input/output
```
Inserisci un operatore: +
Inserisci il primo numero: 40
Inserisci il secondo numero: -15
Il risultato è 40 + -15 = 25
Inserisci un operatore: *
Inserisci il primo numero: 6
Inserisci il secondo numero: 7
Il risultato è 6 * 7 = 42
Inserisci un operatore: /
Inserisci il primo numero: 3
Inserisci il secondo numero: 2
Il risultato è 3 / 2 = 1.5
Inserisci un operatore: exit
```
#### Esempio parte extra (mem)
```
Inserisci un operatore: *
Inserisci il primo numero: 6
Inserisci il secondo numero: 7
Il risultato è 6 * 7 = 42
Inserisci un operatore: /
Inserisci il primo numero: mem
Inserisci il secondo numero: 2
Il risultato è 42 / 2 = 21
Inserisci un operatore: exit
```

## Trova il numero maggiore
Chiedere numeri in input fintanto che l'utente non inserisce 0.  
Stampare in output il numero più grande che è stato inserito.
### Esempi input/output
```
Inserisci un numero: 5
Inserisci un numero: 30
Inserisci un numero: -10
Inserisci un numero: 0
Il numero più grande è 30
```

## Trova il numero più frequente
Chiedere numeri in input fintanto che l'utente non inserisce 0.  
Stampare in output il numero che è stato inserito più volte, in caso ce ne sia più di uno va bene uno qualsiasi.

_Hint_: Leggete prima tutti i numeri all'interno di una lista e solo successivamente cercate quello più frequente.
### Esempi input/output
```
Inserisci un numero: 5
Inserisci un numero: 7
Inserisci un numero: 3
Inserisci un numero: 5
Inserisci un numero: 3
Inserisci un numero: 5
Inserisci un numero: 0
Il numero più frequente è 5
```

## Statistiche
Chiedere numeri in input fintanto che l'utente non inserisce 0.  
Successivamente chiedere in input una operazione e 2 numeri.

L'operazione andrà eseguita sulla lista di numeri letti in precedenza e più essere `somma`, `media`, `maggiore`, `minore`.  
I due numeri rappresentano rispettivamente gli indici di inizio e fine dell'operazione sulla lista (considerando il primo elemento della lista di indice `0`), quindi l'operazione non andrà eseguita su tutta la lista ma solo ai numeri compresi tra le posizioni indicate.

Continuare fintanto che l'utente non inserisce `'exit'` come operazione.  

### Esempi input/output
```
Inserisci un numero: 5
Inserisci un numero: 7
Inserisci un numero: 3
Inserisci un numero: 10
Inserisci un numero: 9
Inserisci un numero: 8
Inserisci un numero: 0
Inserisci un'operazione: somma
Inserisci l'indice di partenza: 1
Inserisci l'indice di fine: 3
La somma dei numeri dalla posizione 1 alle posizione 3 è 20
Inserisci un'operazione: media
Inserisci l'indice di partenza: 0
Inserisci l'indice di fine: 5
La media dei numeri dalla posizione 0 alle posizione 5 è 7
Inserisci un'operazione: exit
```

In questo esempio la lista inserita è `[5, 7, 3, 10, 9, 8]`.  
La prima operazione è la somma dei numeri da indice 1 a indice 3, quindi `7 + 3 + 10 = 20`.  
La seconda operazione è la media dei numeri da indice 0 a indice 5, cioè la media di tutta la lista, quindi `(5 + 7 + 3 + 10 + 9 + 8) / 6 = 7`.
