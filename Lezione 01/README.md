# Lezione 1
### [Esercizi per la prossima settimana](#ESERCIZI.md)

# Indice
- [Output su console](#output-su-console)
- [Tipi](#tipi)
- [Variabili](#variabili)
- [Commenti](#commenti)
- [Operatori matematici](#operatori-matematici)
- [Input da console](#input-da-console)
- [Conversione da string a numero](#conversione-da-string-a-numero)
- [If-Else](#if-else)
- [Operatori di confronto](#operatori-di-confronto)

# Output su console

```py
print("Ciao, mi chiamo Mario")
```
`print` è una _funzione_ che permettere di scrivere sulla console.

In questo esempio quindi in output apparirà la _stringa_ `Ciao, mi chiamo Mario`.

È anche possibile stampare più valori sulla stessa riga:
```py
print("Il numero", 5, "è maggiore del numero", 4)
```
che in output apparirà come `Il numero 5 è maggiore del numero 4`.

# Tipi

I valori possono essere di vari tipi, tra cui:
- `int`: numeri interi. Quindi numeri sia negativi che positivi ma senza la virgola. (es. `1`, `0`, `200`, `-42`)
- `float`: numeri con la virgola, sia negativi che positivi. (es. `3.14`, `5.0`, `-1.234`)
- `str` (o `string`): stringa o lista di caratteri. In python delimitata da `"` o `'` (es. `"ciao"`, `'python'`, `"Mi chiamo Mario"`)

# Variabili

Le variabili sono dei contenitori di valori contrassegnate da un nome.  
Una variabile può contenere un valore di qualsiasi tipo.

```py
a = 1
pigreco = 3.14
saluto = "ciao"
```

Alla variabile chiamata `a` assegniamo il valore intero `1`, alla variabile `pigreco` assegniamo il valore float `3.14` e alla variabile `saluto` assegniamo la stringa `"ciao"`.

Una variabile può cambiare valore durante il programma.
```py
a = 1
b = 3.14
a = b
```
Alla fine di questo programma la variabile `a` varrà `3.14` (uguale alla variabile `b`) invece che `1` in quanto il suo valore è stato sovrascritto nell'ultima riga.

# Commenti
È possibile far sì che python ignori certe righe del proprio file, molto utile per spiegare parti di codice poco chiare.
```py
# questo è un commento, la prossima riga invece non fa parte del commento
a = 1

b = 2 # è anche possibile fare iniziare il commento solo a un certo punto della riga
```

# Operatori matematici
È possibile utilizzare eseguire operazioni matematiche tra numeri. Alcuni operatori presenti in python:
- `+` : somma. (es. `1 + 2` uguale `3`)
- `-` : sottrazione. (es. `1 - 2` uguale `-1`)
- `*` : moltiplicazione. (es. `2 * 3` uguale `6`)
- `/` : divisione. (es. `3 / 2` uguale `1.5`)
- `//` : divisione intera. (es. `3 // 2` uguale `1`)
- `**` : elevamento a potenza. (es. `2**3` uguale `8`)
- `%` : resto divisione. (es. `3 % 2` uguale `1`)

```py
raggio = 1.234
pigreco = 3.14
circonferenza = 2 * raggio * pigreco
area = raggio**2 * pigreco
print(circonferenza, area) # che in questo esempio stampa: 7.74952 4.78145384
```

# Input da console
```py
nome = input("Inserisci il tuo nome: ")
print("Ciao", nome)
```

`input` è una funzione che legge una riga da console e la ritorna come stringa.  
È possibile specificare cosa printare prima di richiedere l'input (in questo esempio `"Inserisci il tuo nome: "`).

Supponendo di inserire il nome Mario quando richiesto, in output verrà stampato ```Ciao Mario```.

# Conversione da string a numero
Se abbiamo un numero sotto forma di stringa non è possibile eseguirci operazioni matematiche sopra in quanto python non sa che la deve trattare come se fosse un numero.  
È perciò possibile convertire una stringa in un intero o un float utilizzando rispettivamente le funzioni `int` e `float`.

```py
s = "123"
print(s + 1) # questo da errore in quanto s è una stringa
n = int(s) # interpreta la stringa s come se fosse un numero intero
print(n + 1) # questo invece fa quello che ci aspettiamo e printa quindi 124
```
```py
s = "123.4"
n = int(s) # questo da errore in quanto s è con la virgola
n = float(s) # è necessario quindi usare float per convertire numeri con la virgola
```

Come detto precedentemente la funzione `input` ritorna una stringa. Se vogliamo quindi richiedere in input all'utente un numero è necessario convertire l'input ottenuto in un numero.

```py
string_raggio = input("Inserisci il raggio: ")
raggio = float(string_raggio)
pigreco = 3.14
circonferenza = 2 * raggio * pigreco
area = raggio**2 * pigreco
print(circonferenza, area)
```

# If-Else
`if` permette di eseguire delle righe di codice solo nel caso in cui una certa condizione sia vera.

```py
n = int(input("Inserisci un numero: "))
if n > 10: # se n è maggiore di 10, allora
    print("Bravo!")
    print("Queste print vengono eseguite solo se n è maggiore di 10")

print("Questa print viene eseguita sempre")
```
In questo esempio prendiamo un numero `n` in input e tramite l'`if` ci chiediamo se `n` è maggiore (`>`) di `10`. Solo in tal caso eseguiamo le due print subito successive.

Il codice eseguito dall'`if` sono tutte le righe più indentate subito di seguito.  
L'indentazione di una riga dipende da quanti caratteri di spazio sono presenti all'inizio.  
Per esempio, nel codice sopra, la riga `if n > 10` ha indentazione di 0 caratteri mentre invece la riga `print("Bravo!")` ha indentazione di 4 caratteri

È anche possibile eseguire del codice nel caso in cui la condizione dell'`if` sia falsa utilizzando `else` subito dopo.

```py
if n > 10: # se n è maggiore di 10, allora
    print("Il numero è maggiore di 10")
else: # altrimenti
    print("Il numero è minore o uguale a 10")
```

# Operatori di confronto
In python sono presenti vari operatori di confronto che vengono spesso usati come condizione all'interno dell'`if`:

- `>` : maggiore. (es. `2 > 1` è vero, `1 > 2` è falso)
- `<` : minore. (es. `2 < 1` è falso, `1 < 2` è vero)
- `>=` : maggiore o uguale. (es. `2 >= 1` è vero, `1 >= 2` è falso, `1 >= 1` è vero)
- `<=` : minore o uguale. (es. `2 <= 1` è falso, `1 <= 2` è vero, `1 <= 1`  è vero)
- `==` : uguale. (es. `1 == 1` è vero, `1 == 2` è falso)

Per l'uguaglianza viene utilizzato il doppio uguale (`==`) in vece che uno singolo (`=`) per distinguerlo dall'assegnamento di una variabile.

```py
numero_da_indovinare = 13
numero_utente = int(input("Inserisci un numero: "))

if numero_utente < numero_da_indovinare:
    print("Il numero inserito è minore")
if numero_utente > numero_da_indovinare:
    print("Il numero inserito è maggiore")
if numero_utente == numero_da_indovinare:
    print("bravo!")
```