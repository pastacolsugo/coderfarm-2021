# Esercizi per casa

## File di configurazione
Scrivere un programma che legga un file di configurazione e lo converta in un dizionario di python (o nel formato che più ritenete sia adatto affinché sia poi fruibile in python).

L'idea di base del file di configurazione è che in ogni riga è possibile inserire una coppia chiave-valore che rappresenta una certa proprietà:
```
background=black

text-color=white
```
quello sopra è un esempio di un file di configurazione dove vengono definite due proprietà: `background` con valore `black` e `text-color` con valore `white`. (chiaramente questo è solo un esempio e ci potrebbe essere scritta qualsiasi cosa)  
Per questo esempio il vostro programma dovrebbe generare un dizionario simile a questo: `{"background": "black", "text-color": "white"}`

Da notare come tra le due proprietà ci sia una riga vuota. Essendo i file di configurazione modificati manualmente dagli utenti è necessario gestire questo genere di cose e ignorare cioè le righe vuote piuttosto che gli spazi inutili.

In questo caso ho scelto come separatore tra il nome e il valore il simbolo dell'uguale (`=`) ma potreste decidere di supportare anche altri simboli frequentemente utilizzati come per esempio i due punti (`:`)
```
background: black
text-color: white
```
Un altra cosa importante è la possibilità di inserire commenti all'interno del file di configurazione. Il vostro programma deve poter gestire correttamente (cioè ignorare) le righe commentate. Una riga è commentata se inizia con un carattere speciale come per esempio `#` oppure `;` o  `//`
```
# questo è un commento
; anche questo è un commento
# devono poter essere all'interno del file di configurazione
# ma essere ignorati dal vostro programma
background=black
```

Di seguito un esempio di file di configurazione complesso che unisce tutte le cose descritte sopra:
```
# ciao :)

; colore dello sfondo
background = black
; colore del testo
text-color: white
; dimensione del testo
  text-size= 30
```
al suo interno ci sono svariati commenti, righe vuote, spazi non necessari e proprietà separate da caratteri diversi.  
Il vostro programma finale dovrebbe comunque saperlo gestire correttamente e generare un dizionario simile a: `{"background": "black", "text-color": "white", "text-size": "30"}`

Vi consiglio prima di partire da una versione base che sappia gestire i casi più semplici e poi, una volta verificato il funzionamento, passate ad aggiungere cose più complesse tipo la gestione dei commenti o di caratteri diversi per l'assegnamento.

Se avete idee per migliorare il formato del file o di altre cose utili da aggiungere sono ovviamente ben accette.

Esempi di formati di configurazione esistenti, simili a quanto descritto sopra, possono essere file [INI](https://en.wikipedia.org/wiki/INI_file) e file [properties](https://en.wikipedia.org/wiki/.properties).  
