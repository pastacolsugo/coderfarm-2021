# Lezione 2
### [Esercizi per la prossima settimana](ESERCIZI.md)

# Indice
- [Operatori condizionali](#operatori-condizionali)
- [elif](#elif)
- [while](#while)
- [Introduzione alle liste](#introduzione-alle-liste)


# Operatori condizionali
È possibile unire varie condizioni usando gli operatori `and` e `or`.

Per esempio se volessimo chiederci se la variabile a è compresa tra `0` e `10` potremmo scrivere:
```py
if a > 0 and a < 10:
    print(a)
```
quindi stiamo controllando se `a` è contemporaneamente sia maggiore di `0` sia minore di `10`.

Se invece, al contrario, volessimo chiedere se `a` è minore di `0` o maggiore di `10`:
```py
if a < 0 or a > 10:
    print(a)
```

Ovviamente è possibile usare entrambi all'interno della stessa condizione:
```py
if a > 0 and a < 10 or a > 20 and a < 30:
    print(a)
```
quindi in questo caso stiamo chiedendo se `a` è compreso tra `0` e `10` oppure se `a` è compreso tra `20` e `30`.

Da notare che `and` ha la precedenza rispetto a `or` (cioè prima vengono "eseguiti" tutti gli `and` e successivamente gli `or`).  
Come nella matematica possiamo usare le parentesi per forzare la precedenza.

```py
if (a == 1 or a == 3) and (b == 1 or b == 3):
    print(a, b)
```

# elif

Successivamente a un `if` è possibile utilizzare `elif` che è una combinazione tra `else` e `if`. Per esempio:

```py
if a == 10:
    print("a è 10")
elif a > 0:
    print("a è maggiore di 0 ma non 10")
```

che è equivalente a:

```py
if a == 10:
    print("a è 10")
else:
    if a > 0:
        print("a è maggiore di 0 ma non 10")

```

La versione con `elif`, oltre a essere più semplice, ha anche il vantaggio di permettere di "concatenare" svariate condizioni:

```py
if a == 10:
    print("a è 10")
elif a == 20:
    print("a è 20 (e ovviamente non è 10)")
elif a > 0:
    print("a è maggiore di 0 ma non 10 né 20")
else:
    print("Nessuna delle cose precedenti è vera, quindi a è minore o uguale a 0")
```

# while
Il `while` è un modo per eseguire più volte dei pezzi di codice, fintanto che una condizione è vera.

Il modo in cui si utilizza è, nella forma, molto simile all'`if`:
```py
i = 0
while i < 10:
    print(i)
    i = i + 1
```
la differenza è che, invece che eseguire il blocco di codice una sola volta se la condizione è vera, continua ad eseguirlo fintanto che non diventa falsa.

Nell'esempio sopra ogni volta viene printa la variabile `i` e poi incrementata di `1` fintanto che `i` è minore di `10`. Verranno quindi stampati tutti i numeri da `0` a `9`.

Esempio lettura numeri da input fintanto che non viene inserito `0`:
```py
n = int(input("Inserisci un numero: "))
while n != 0:
    print(n)
    n = int(input("Inserisci un numero: "))
```
Esempio indovina numero random:
```py
while numero_utente != da_indovinare:
	numero_utente = int(input("Inserisci un numero: "))

    if numero_utente > da_indovinare:
		print("Il numero da indovinare è più piccolo!")
	elif numero_utente < da_indovinare:
		print("Il numero da indovinare è più grande!")

print("Bravo!")
```

# Introduzione alle liste
Le liste sono un tipo di dato che può contenere al suo interno un numero qualsiasi di valori.  
Per creare una lista è sufficiente mettere una lista di valori tra quadre.

```py
l = [1, 5, -2] # questa è una lista con 3 elementi, tutti interi
print(l) # [1, 5, -2]
```

È possibile, tra le altre cose: 
- aggiungere nuovi valori a una lista esistente tramite `.append()`
    ```py
    l = [] # si possono creare anche liste vuote
    l.append(1)
    l.append(5)
    print(l) # [1, 5]
    ```
- conoscere la dimensione di una lista tramite `len()`
    ```py
    l = [1, 5, -2]
    print(len(l)) # 3
    ```
- accedere ad ogni singolo valore al suo interno in base alla posizione tramite `[]`
    ```py
    l = [1, 5, -2]
    print(l[0]) # 1
    print(l[1]) # 5
    print(l[2]) # -2
    ```

Le posizioni dei valori all'interno delle liste vengono dette indici.  
A differenza di quello che potrebbe venire naturale pensare gli indici partono da `0` e proseguono in ordine crescente, quindi il primo elemento si trova ad indice `0` e il secondo a indice `1` e così via.

Se per esempio volessimo accedere al terzo elemento all'interno di una lista `l` dovremmo scrivere `l[2]`.  
Possiamo quindi dire che gli indici valgono sempre `1` in meno rispetto alla "posizione vera".

Esempio stampa tutti i numeri all'interno di una lista:
```py
# per questo esempio conosciamo già i valori
# ma nella realtà idealmente sono inseriti dall'utente
l = [1, 5, -2]
# l'indice parte da 0 e arriva fino a len(l)-1
i = 0
while i < len(l):
    # in questo esempio la print verrà eseguita tre volte per: l[0], l[1] e l[2]
    print(l[i])
```

Esempio indovina numero random con history dei tentativi:

```py
tentativi = []

while numero_utente != da_indovinare:
	numero_utente = int(input("Inserisci un numero: "))

	if numero_utente > da_indovinare:
		print("Il numero da indovinare è più piccolo!")
	elif numero_utente < da_indovinare:
		print("Il numero da indovinare è più grande!")

	# aggiungo il numero inserito dall'utente alla lista dei tentativi effettuati
	tentativi.append(numero_utente)

print("Bravo! Ci hai messo", len(tentativi), "tentativi.")
print("Tentativi:", tentativi)
```

