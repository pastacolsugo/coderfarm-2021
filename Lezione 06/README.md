# Lezione 6
### [Esercizi per la prossima settimana](ESERCIZI.md)
<br>

# 

In questa lezione non abbiamo affrontato nessun argomento nuovo.  
Abbiamo ripassato le cose fatte nelle lezioni scorse, visto e fatto degli esercizi.

Di seguito un esercizio svolto a lezione per allenarsi con tuple e dizionari:

```py
# data una lista (registro) dove ogni elemento
# è una tupla contenente nome e voto
# ritornare un dizionario che associa a ogni nome
# la lista di tutti i suoi voti
def organizza_voti(registro):
    ...

print(organizza_voti([
    ("samuele", 10),
    ("andrea", 4),
    ("samuele", 6),
    ("david", 8),
    ("gabriele", 7),
    ("david", 5),
])) # {"samuele": [10, 6], "andrea": [4], "david": [8, 5], "gabriele": [7]}
```

<details> 
  <summary><b>Soluzione (clicca per mostrare)</b></summary>

```py
# data una lista (registro) dove ogni elemento
# è una tupla contenente nome e voto
# ritornare un dizionario che associa a ogni nome
# la lista di tutti i suoi voti
def organizza_voti(registro):
    output = {}
    for nome,voto in registro:
        if nome in output:
            output[nome].append(voto)
        else:
            output[nome] = [voto]
    return output

print(organizza_voti([
    ("samuele", 10),
    ("andrea", 4),
    ("samuele", 6),
    ("david", 8),
    ("gabriele", 7),
    ("david", 5),
])) # {"samuele": [10, 6], "andrea": [4], "david": [8, 5], "gabriele": [7]}
```

</details>
<br>