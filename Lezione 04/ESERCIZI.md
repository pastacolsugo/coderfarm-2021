# Esercizi per casa

Nella [pagina principale](../README.md) ho aggiunto i siti che vi ho mostrato a lezione che contengono esercizi in Python.  
Non li ho mai utilizzati estensivamente per cui non ve ne posso assicurare la qualità. Se non riuscite a risolvere qualche esercizio non vi preoccupate e magari provate a cambiare, non è detto che siano presentati per forza in ordine di difficoltà.  

Gli esercizi seguenti funzioneranno come [descritto a lezione](README.md), cioè vi è richiesto solamente di implementare la funzione descritta e non di richiedere valori in input all'utente.

## Media pesata

Scrivete una funzione `media_pesata` che prende come argomento una lista contenente dei voti e il loro rispettivo peso e ne ritorni la [media pesata](https://www.youmath.it/domande-a-risposte/view/6298-media-ponderata.html).

Ogni elemento all'interno della lista è a sua volta una lista contenente due elementi: il primo elemento è il voto e il secondo è il peso del voto.

_nota: nonostante forse non lo abbiamo mai visto, all'interno delle liste è possibile mettere qualsiasi cosa, quindi anche altre liste._

```py
def media_pesata(voti):
    ...

# esempi
print(media_pesata([[8, 1.0], [9, 0.5], [5, 0.5], [6, 0.75], [3, 0.25]])) # 6.75
print(media_pesata([[10, 0.5], [6, 1.0], [7, 0.25], [2, 0.75], [5, 1.0]])) # 6.5
```
Nel primo esempio stiamo passando alla funzione 5 voti:  
- `8` con il peso di `1.0`
- `9` con il peso di `0.5`
- `5` con il peso di `0.5`
- `6` con il peso di `0.75`
- `3` con il peso di `0.25`

la cui media pesata è:  
`(8 * 1.0 + 9 * 0.5 + 5 * 0.5 + 6 * 0.75 + 3 * 0.25) / (1.0 + 0.5 + 0.5 + 0.75 + 0.25) = 6.75`

