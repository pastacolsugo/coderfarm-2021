# Esercizi per casa

Nella [pagina principale](../README.md) ho aggiunto i siti che vi ho mostrato a lezione che contengono esercizi in Python.  
Non li ho mai utilizzati estensivamente per cui non ve ne posso assicurare la qualità. Se non riuscite a risolvere qualche esercizio non vi preoccupate e magari provate a cambiare, non è detto che siano presentati per forza in ordine di difficoltà.  

Gli esercizi seguenti funzioneranno come [descritto a lezione](README.md), cioè vi è richiesto solamente di implementare la funzione descritta e non di richiedere valori in input all'utente.

## Lettera o Numero

Scrivere una funzione `is_digit` che prende un carattere (stringa lunga 1) e ritorna True se è un numero e False altrimenti.

```py
def is_digit(c):
    ...

# esempi
print(is_digit('7')) # True
print(is_digit('0')) # True
print(is_digit('a')) # False
print(is_digit('B')) # False
```

## Rimuovi numeri

Scrivere una funzione `remove_numbers` che prende una stringa e ritorna una stringa come quella in input ma con tutti i numeri al suo interno rimossi.  
(es. la stringa `"a12bc"` diventerebbe `"abc"` perché `1` e `2` sono stati rimossi in quanto numeri)

Per implementare questa funzione sfruttate la funzione `is_digit` scritta in precedenza (come visto durante gli esercizi fatti a lezione).

_nota: è possibile concatenare due stringhe utilizzando il `+`. Quindi per esempio `"ab" + "c"` fa `"abc"`._

```py
def remove_numbers(s):
    ...

# esempi
print(remove_numbers("a12bc")) # abc
print(remove_numbers("asd")) # asd
print(remove_numbers("42")) #  (stringa vuota)
print(remove_numbers("cia0")) # cia
print(remove_numbers("a1b2c3")) # abc
```

## Rimuovi lettere

Scrivere una funzione `remove_letters` che prende una stringa e ritorna una stringa come quella in input ma mantenendo solo i numeri scritti al suo interno (rimuovendo quindi lettere e punteggiatura/simboli).  
(es. la stringa `"a12bc"` diventerebbe `"12"` perché `a`, `b` e `c` sono state rimosse in quanto non numeri (lettere))

Per implementare questa funzione sfruttate la funzione `is_digit` scritta in precedenza.


```py
def remove_letters(s):
    ...

# esempi
print(remove_letters("a12bc")) # abc
print(remove_letters("asd")) #  (stringa vuota)
print(remove_letters("42")) # 42
print(remove_letters("cia0")) # 0
print(remove_letters("a1b2c3")) # 123
```

## Media pesata

Scrivere una funzione `media_pesata` che prende come argomento una lista contenente dei voti e il loro rispettivo peso e ne ritorni la [media pesata](https://www.youmath.it/domande-a-risposte/view/6298-media-ponderata.html).

Ogni elemento all'interno della lista è a sua volta una lista contenente due elementi: il primo elemento è il voto e il secondo è il peso del voto.

_nota: nonostante forse non lo abbiamo mai visto, all'interno delle liste è possibile mettere qualsiasi cosa, quindi anche altre liste._

```py
def media_pesata(voti):
    ...

# esempi
print(media_pesata([[8, 1.0], [9, 0.5], [5, 0.5], [6, 0.75], [3, 0.25]])) # 6.75
print(media_pesata([[10, 0.5], [6, 1.0], [7, 0.25], [2, 0.75], [5, 1.0]])) # 5.5
```
Nel primo esempio stiamo passando alla funzione 5 voti:  
- `8` con il peso di `1.0`
- `9` con il peso di `0.5`
- `5` con il peso di `0.5`
- `6` con il peso di `0.75`
- `3` con il peso di `0.25`

la cui media pesata è:  
`(8 * 1.0 + 9 * 0.5 + 5 * 0.5 + 6 * 0.75 + 3 * 0.25) / (1.0 + 0.5 + 0.5 + 0.75 + 0.25) = 6.75`
