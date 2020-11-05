# Esercizi per casa

_Ricordo che nella [pagina principale](../README.md) c'è un elenco di siti contenenti esercizi che potete usare per esercitarvi._

## Statistiche testo

Scrivere una funzione `statistiche_testo` che data una stringa restituisca quante parole sono presenti al suo interno e la loro lunghezza media.

Per suddividere del testo in parole potete usare la funzione `split` spiegata nella [lezione precedente](/Lezione%2004/README.md#funzioni-delle-stringhe).

Dato che la funzione deve ritornare due informazioni distinte dovrete utilizzare una tupla per ritornarle insieme.

```py
def statistiche_testo(testo):
    ...

# Esempi
print(statistiche_testo("Ciao mi chiamo Samuele")) # (4, 4.75)
print(statistiche_testo("Nel mezzo del cammin di nostra vita")) # (7, 4.142857142857143)
print(statistiche_testo("Essere o non essere")) # (4, 4.0)
```

## Distanza tra punti

Scrivere una funzione `distanza` che prende due punti e ne ritorna la distanza.

Ogni punto è rappresentato da una tupla contenente due valori, rispettivamente la `x` e la `y` del punto all'interno del piano.

La distanza tra due punti si può calcolare utilizzando il teorema di pitagora.  
In modo particolare, dati i due punti `(x1, y1)` e `(x2, y2)` la loro distanza si può calcolare con la seguente formula:
`sqrt((x1 - x2)**2 + (y1 - y2)**2)`

Dove `sqrt` è la funzione per calcolare la radice quadrata che in python va importata scrivendo `from math import sqrt` all'inizio del file.

```py
from math import sqrt

def distanza(p1, p2):
    ...

# Esempi
print(distanza((1, 2), (2, 2))) # 1.0
print(distanza((1, 2), (2, 3))) # 1.4142135623730951
print(distanza((2, 3), (-10, 7))) # 12.649110640673518
print(distanza((1, 1), (1, 1))) # 0.0
```

## Punti più vicini

Scrivere una funzione `distanza_minore_punti` che prende una lista di punti nel piano e ritorna la distanza tra i due punti più vicini all'interno di della lista.

Come per l'esercizio sopra, ogni punto è rappresentato da una tupla contenente due valori, rispettivamente la `x` e la `y` del punto all'interno del piano.

Per implementare questa funzione sfruttare la funzione `distanza` scritta in precedenza.

_nota: potete assumere che tutti i punti all'interno della lista siano diversi. Cioè non può succedere che uno stesso punto appaia due volte all'interno della lista._

```py
from math import sqrt

def distanza_minore_punti(punti):
    ...

# Esempi
print(distanza_minore_punti([
    (1, 2),
    (-10, 5),
    (-5, 5),
    (1, -1),
])) # 3.0
print(distanza_minore_punti([
    (0, 0),
    (3, 4),
    (5, 10),
    (2, 7),
    (-1, 2),
])) # 2.23606797749979
```

## Segreto

Scrivere un programma interattivo che offre all'utente la possibilità di salvare dei segreti protetti da password e di recuperarli successivamente.  
Un segreto è semplicemente una stringa inserita dall'utente che idealmente vorrebbe mantenere segreta.

Il programma deve offrire due operazioni:
- `mostra`:
  chiede il nome e la password di un segreto e, nel caso siano corretti, mostra il contenuto del segreto.
- `aggiungi`:
  chiede un nome, una password e un segreto e li salva.  
  Attenzione che se un segreto con quel nome esiste già bisogna considerare questa operazione come un aggiornamento del segreto, bisogna quindi assicurarsi che la password sia la stessa inserita in precedenza prima di modificare il segreto.

### Esempi input/output
```
Cosa vuoi fare? (aggiungi/mostra): aggiungi
Nome del segreto: pin bancomat
Password: gattini123
Segreto: 54321
Segreto "pin bancomat" salvato!

Cosa vuoi fare? (aggiungi/mostra): aggiungi
Nome del segreto: data di nascita
Password: patatine123
Segreto: 25/12/1970
Segreto "data di nascita" salvato!

Cosa vuoi fare? (aggiungi/mostra): mostra
Nome del segreto: pin bancomat
Password: gattini123
Il segreto è 54321

Cosa vuoi fare? (aggiungi/mostra): mostra
Nome del segreto: nome gatto
Il segreto "nome gatto" non esiste!

Cosa vuoi fare? (aggiungi/mostra): mostra
Nome del segreto: data di nascita
Password: pizza123
La password è errata!

Cosa vuoi fare? (aggiungi/mostra): aggiungi
Nome del segreto: pin bancomat
Esiste già un segreto con questo nome, verrà modificato!
Password: mucche123
La password è errata!

Cosa vuoi fare? (aggiungi/mostra): aggiungi
Nome del segreto: pin bancomat
Esiste già un segreto con questo nome, verrà modificato!
Password: gattini123
Segreto: 98765
Segreto "pin bancomat" salvato!

Cosa vuoi fare? (aggiungi/mostra): esci
Ciao!
```

Ovviamente questo programma così da solo ha poco senso in quanto tutti i segreti verranno persi nel momento in cui l'utente chiude il programma.  
_Extra_: trovare un modo per salvare i segreti alla chiusura del programma e per recuperarli all'apertura. Per farlo sarà necessario leggere e scrivere file, vi invito a cercare da soli su internet/sulla documentazione come si fa.

