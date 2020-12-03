# Lezione 8
### [Esercizi per la prossima settimana](ESERCIZI.md)

#

- [File](#file)
  * [with](#with)
  * [Lettura da file](#lettura-da-file)
  * [Scrittura su file](#scrittura-su-file)
  * [Esempio](#esempio)
- [Manipolazione stringhe](#manipolazione-stringhe)
  * [strip](#strip)
  * [Esempio ordinamento nomi da file](#esempio-ordinamento-nomi-da-file)
  * [Esempio ordinamento per voto](#esempio-ordinamento-per-voto)
- [Slicing](#slicing)
- [String interpolation (f-strings)](#string-interpolation-f-strings)

# File

Per poter interagire con i file in python è prima necessario aprirli tramite la funzione [`open`](https://docs.python.org/3/library/functions.html#open). Quando si ha finito di usarlo è opportuno ricordarsi di chiudere il file in modo che le altre applicazioni possano accedervi:
```py
f = open("percorso/del/file")
# fa qualcosa con il file
f.close()
```
È possibile passare un secondo argomento a `open` per specificare in che modalità aprire il file. Le modalità più frequenti sono:
- `"r"`: (read) lettura
- `"w"`: (write) scrittura dove il contenuto originale viene cancellato
- `"a"`: (append) scrittura aggiungendo in fondo al contenuto già presente
## with
Dato che spesso capita di dimenticarsi di chiamare `close`, o comunque può succedere che a causa di qualche errore non venga chiamata, esiste un costrutto speciale che permette di chiudere il file in automatico quando si ha finito di usarlo.  
Il consiglio è di usare sempre il `with` per lettura e scrittura su file salvo casi particolari:

```py
with open("percorso/del/file") as f:
    # dentro a questo blocco (quindi indentato) fa qualcosa con il file f
# dopo essere usciti dal blocco, il file è stato chiuso in automatico
```
per poter utilizzare il file appena aperto è necessario dargli un nome utilizzando la keyword `as`. In questo caso ho deciso di chiamarlo `f` (`as f`).  
Potete vedere il pezzo `open("percorso/del/file") as f` come se fosse un assegnamento a variabile ma con il nome della variabile a destra, quindi tipo `f = open("percorso/del/file")`.

Più in generale, il costrutto `with` permette di disfarsi delle risorse in automatico all'uscita del blocco, più avanti vedremo che non viene usato solo nel contesto dei file.

## Lettura da file
```py
with open("input.txt", "r") as f:
    text = f.read()
print(text)
```
Qui abbiamo aperto un file chiamato `"input.txt"` in modalità `"r"` (quindi di lettura) e lo possiamo utilizzare all'interno del blocco tramite la variabile `f`.  
In questo caso l'unica cosa che facciamo con il file è leggerne tutto il contenuto tramite la funzione `read` e assegnarlo a una variabile `text` che useremo successivamente.  
Nonostante abbiamo già chiuso il file, è consentito utilizzare la variabile `text` al di fuori del blocco `with` in quanto il contenuto del file è ora in una stringa di python in memoria, non potremmo però utilizzare direttamente il file `f` ovviamente. È quindi necessario fare tutte le letture all'interno del `with`.

Le funzioni più utili per la lettura dei file sono:
- `read`: per leggere tutto il contenuto del file, ritorna una stringa
- `readlines`: per leggere tutte le righe del file, ritorna una lista di righe dove ogni riga è una stringa. Attenzione che viene mantenuto il carattere di "a capo" alla fine delle righe, uno dei possibili modi per rimuoverlo è tramite la funzione `strip` che vedremo tra poco.

## Scrittura su file
```py
with open("output.txt", "w") as f:
    f.write("ciao")
    # è possibile chiamare write più volte per aggiungere del testo
    f.write("miao")
```
Qui abbiamo aperto un file chiamato `"output.txt"` in modalità `"w"` (quindi di scrittura) e semplicemente ci abbiamo scritto dentro `"ciaomiao"` (tutto attaccato in quanto non erano presenti spazi in nessuna delle due stringhe).

## Esempio
Dato un file "input.txt" con al suo interno un insieme di numeri (uno per riga), scriviamo all'interno di "output.txt" i numeri moltiplicati per 2:
```py
numeri = []
with open("input.txt", "r") as f:
    # leggiamo tutti i numeri e li convertiamo in interi
    for r in f.readlines():
        numeri.append(int(r))
with open("output.txt", "w") as f:
    for n in numeri:
        # write vuole una stringa, è necessario quindi convertire il numero
        f.write(str(n * 2))
        # poi andiamo a capo
        f.write("\n")
```

# Manipolazione stringhe
## strip
`strip` è una funzione delle stringhe che permette di rimuovere certi caratteri dalle estremità di una stringa. Di default rimuove tutti i caratteri di whitespace (cioè principalmente lo spazio, il tab e l'a capo) ma è possibile specificare quali.

- `"ciao ".strip()` -> `"ciao"` (rimosso lo spazio alla fine)
- `"ciao ciao ".strip()` -> `"ciao ciao"` (rimosso lo spazio alla fine ma non nel mezzo)
- `" ciao ciao  ".strip()` -> `"ciao ciao"` (rimosso lo spazio all'inizio e gli spazi alla fine)
- `" \tciao ciao \n".strip()` -> `"ciao ciao"` (rimossi sia gli spazi, che i tab (`\t`) che gli a capi (`\n`))
- `"ciao".strip()` -> `"ciao"` (non erano presenti spazi alle estremità, quindi non è cambiato nulla)
- `"### ciao".strip("#")` -> `" ciao"` (rimosso i cancelletti ma non lo spazio)
- `"### ciao@".strip("#@")` -> `" ciao"` (rimosso i cancelletti e la chiocciola)

`strip` è utilizzata di frequente quando si ha a che fare con stringhe ottenute da file o comunque in generale su cui non abbiamo controllo.

## Esempio ordinamento nomi da file
Dato un file di testo contenente un elenco di nomi separati in righe, printare i nomi ordinati.  
Assicurarsi di ignorare le righe vuote e di rimuovere eventuali spazi all'inizio o fine del nome.

```py
with open("input.txt", "r") as f:
    l = f.readlines()

nomi = []
for nome in l:
    # chiamiamo strip per rimuovere il carattere di "a capo" in fondo alla riga
    # e per rimuovere gli eventuali spazi prima o dopo il nome.
    # inoltre convertiamo la stringa in caratteri minuscoli
    # così da non aver problemi durante l'ordinamento
    nome = nome.strip().lower()
    # aggiungiamo il nome solo se non è vuoto
    # è importante fare questo controllo dopo aver chiamato strip
    if nome != "":
        nomi.append(nome)

# stampiamo i nomi ordinati
for nome in sorted(nomi):
    print(nome)
```

## Esempio ordinamento per voto
Dato un file di testo contenente in ogni riga un nome e un voto separati da spazio, printare i nomi ordinati in funzione del loro voto.

```py
with open("input.txt", "r") as f:
    l = f.readlines()

voti = []
for r in l:
    r = r.strip().lower()
    if r != "":
        # dividiamo la riga dove c'è lo spazio
        # così da ottenere una lista contenente nome e voto
        # e fare unpacking nelle rispettive variabili
        nome, voto = r.split(" ")
        voto = int(voto)
        # inseriamo prima voto così da avere la priorità per l'ordinamento
        voti.append((voto, nome))

# stampiamo i nomi ordinati per voto
for voto, nome in sorted(voti):
    print(nome, voto)
```

# Slicing

Data una qualsiasi sequenza, è possibile ottenere una sottosequenza (o una "fetta") tramite l'utilizzo dello slicing.  
Con sequenza si intende un qualsiasi tipo di dato che contiene al suo interno più valori e che permette l'indicizzazione (quindi l'accesso tramite parentesi quadre).

Un esempio concreto è che, data una stringa, è possibile ottenere una sottostringa tramite lo slicing:
```py
s = "abcdef"
print(s[2:5]) # cde
```

Lo slicing si fa mettendo i due punti (`:`) all'interno delle quadre.  
Il numero alla sinistra rappresenta l'indice di partenza (inclusivo) e quello alla destra rappresenta l'indice di fine (esclusivo).

Quindi `s[2:5]` significa prendere la sottostringa di `s` che parte dall'indice `2` incluso e arriva fino all'indice `5` escluso e quindi contiene tutti i valori agli indici `2`, `3` e `4`.

È possibile non limitare l'indice di fine e/o inizio semplicemente non mettendo alcun numero:
```py
s = "abcdef"
print(s[:3]) # abc (limita solo l'indice di fine)
print(s[3:]) # def (limita solo l'indice di inizio)
print(s[:]) # abcdef (non limita niente, ritorna una copia della stringa)
```

Come accade per l'indicizzazione normale, sono ammessi anche indici negativi per rappresentare posizioni a partire dalla fine (quindi per esempio l'indice `-1` rappresenta l'ultimo elemento, `-2` il penultimo e così via).

```py
s = "abcdef"
print(s[1:-1]) # bcde (esclude il primo e l'ultimo elemento)
print(s[:-2]) # abcd (esclude gli ultimi 2)
```

Normalmente vengono presi tutti gli elementi compresi tra i due indici inseriti, è tuttavia possibile specificare (aggiungendo altri `:`) lo "step", cioè di quanti indici ci si sposta prima di prendere il prossimo elemento.

```py
s = "abcdef"
print(s[1:6:2]) # bdf (parte da indice 1 fino al 6 con step di 2)
```
quindi in questo esempio si prendono gli elementi agli indici `1`, `3` e `5`.  
Cioè partiamo dall'indice `1`, poi abbiamo uno step di `2` e quindi passiamo all'indice `3`, poi altro step di `2` e quindi indice a `5`, infine indice `7` che è però maggiore della fine e quindi lo ignoriamo.

Quando si introduce lo step inizia a diventare complesso ragionare su cosa viene selezionato, quindi in verità, nel mondo reale, si usa solo in certi casi molto specifici.  
In modo particolare il motivo principale per cui viene usato lo step è per invertire una sequenza:
```py
s = "abcdef"
print(s[::-1]) # fedcba
```
e cioè non si mettono limiti agli indici però si mette lo step a `-1` e quindi scorre la sequenza al contrario, dall'ultimo elemento al primo.

Altri usi un meno comuni dello step sono per esempio ottenere tutti gli elementi a indici pari o quelli a indici dispari:
```py
s = "abcdef"
print(s[::2]) # ace (valori a indici pari)
print(s[1::2]) # bdf (valori a indici dispari)
```

Tutti gli esempi sopra li ho fatti su stringhe per comodità, ma si applicano allo stesso identico modo anche su altri tipi di sequenza, per esempio le liste:
```py
l = [4, 6, 2, 1, 7, 2]
print(l[1:3]) # [6, 2]
print(l[1:-1]) # [6, 2, 1, 7]
print(l[::-1]) # [2, 7, 1, 2, 6, 4]
```

# String interpolation (f-strings)
Supponiamo di voler generare una stringa tipo `"Mi chiamo Giovanni e ho 30 anni."` dove però il nome e l'età li otteniamo tramite delle variabili, magari lette dall'utente.  
Con quello che abbiamo visto fin'ora una possibile soluzione potrebbe essere:
```py
nome = "Giovanni"
eta = 30
s = "Mi chiamo " + nome + " e ho " + str(eta) + " anni."
print(s)
```
che è funzionante ma non particolarmente bella. Per esempio è stato necessario convertire l'intero `eta` in una stringa esplicitamente in quanto python non permette la concatenazione tra stringhe e interi, inoltre è necessario mettere un sacco di `+` e stare attenti agli spazi.

Esistono svariati modi diversi per formattare le stringhe, ma a partire da python 3.6 è stato introdotto un nuovo metodo molto comodo:
```py
nome = "Giovanni"
eta = 30
s = f"Mi chiamo {nome} e ho {eta} anni."
print(s) # Mi chiamo Giovanni e ho 30 anni.
```
Questo genere di stringhe viene chiamato f-string proprio perché per usarle è necessario inserire una `f` prima dell'apice di apertura della stringa.

All'interno di una f-string è possibile inserire espressioni di python tra parentesi graffe, le quali verranno poi valutate e il valore di ritorno verrà scritto direttamente all'interno della stringa.  
Quindi nell'esempio sopra `{nome}` verrà sostituito con il valore della variabile `nome` e cioè `"Giovanni"` mentre `{eta}` verrà sostituito con `30`.

La variabili potrebbero essere l'espressione più comune da inserire tra le graffe ma è in realtà possibile inserire qualsiasi tipo di calcolo:
```py
nome = "Giovanni"
eta = 30
s = f"Mi chiamo {nome} e ho {eta*2} anni."
print(s) # Mi chiamo Giovanni e ho 60 anni.
```
