# Cross domain sentiment analysis on drugs reviews - AI 23/24 UNIFI
## Studente: Niccolò Benedetto MAT. 7024656
## Docente: Paolo Frasconi

> [!IMPORTANT]
> Contenuto della repository:
>  - **Cross_Domain_SentimentAnlysis.ipynb**, Jupyter Notebook con il codice del progetto implementato con [Google Colab](https://colab.google/).
>  - **CD_SentimentAnalysis.pdf**, file pdf generato con software [LaTeX](https://www.latex-project.org/) inerente alla documentazione del progetto.


**Project Assignment**:

*In questo progetto si utilizzano implementazioni disponibili dell’algoritmo Perceptron (p.es. [scikit-learn](https://scikit-learn.org/stable/) 
in Python o [Weka](https://ml.cms.waikato.ac.nz/weka/) in Java) al problema dell’analisi del sentimento su recensioni di farmaci, come descritto
in [Gräßer et al. 2018](https://dl.acm.org/doi/10.1145/3194658.3194677), cercando di riprodurre risultati analoghi a quelli riportati nella tabella 3 dell’articolo (caso cross-domain).  I risultati numerici potranno differire dato che gli autori utilizzano un classificatore diverso. Il dataset è disponibile sul [repository di UCI](https://archive.ics.uci.edu/ml/datasets/Drug+Review+Dataset+%28Drugs.com%29). È accettabile utilizzare un sottoinsieme dei dati e/o semplificare gli attributi lessicali (p.es. evitando i trigrammi) se le risorse di calcolo disponibili fossero insufficienti.*


> [!NOTE]
> **Informazioni utili**
> 
> L'implementazione del codice necessario alla realizzazione del progetto segue le seguenti fasi
>  1. preparazione dei dati del dataset:
>     pre-processing del testo (rimozione caratteri alfanumerici, conversione in minuscolo, tokenizzazione, rimozione delle stop-words) delle reviews attraverso la libreria
>     [NLTK](https://www.nltk.org/#natural-language-toolkit) e valutazione della polarità 
>     mediante il tool [VADER](https://pypi.org/project/vaderSentiment/). Questa valutazione fornirà un quantificatore (numero reale) che viene sfruttato per 
>     definire una nuova colonna del dataset, che rappresenta un nuovo valore di rating, il quale verrà utilizzato come etichetta del modello. In particolare se il 
>     quantificatore rientra nel range [-1;-0.3], allora il valore di rating è 0 (sentimento negativo), se cade in (-0.3;0.3), allora rating corrisponde a 1 
>     (sentimento neutro), mentre se rientra nell'intervallo [0.3;1], rating equivale a 2 (sentimento positivo).
> 
>     **Osservazione:** il range scelto per definire il nuovo valore di rating è da ritenersi congruo con il significato dei valori di compound generati dal tool 
>     VADER (vedi [about the scoring of VADER analysis](https://github.com/cjhutto/vaderSentiment)). Scelte di intervalli diversi
>     potranno, a seguito dell'addestramento del modello, produrre risultati diversi.
> 
>     [1] @Hutto, C.J. & Gilbert, E.E. (2014). VADER: A Parsimonious Rule-based Model for Sentiment Analysis of Social Media Text. Eighth International Conference on 
>         Weblogs and Social Media (ICWSM-14). Ann Arbor, MI, June 2014.
>  3. realizzazione del modello:
>     il modello prevede come dati di train i vari testi delle reviews, dunque associa come etichetta il rispettivo valore di rating (rating_model) calcolato durante la
>     fase di preparazione dei dati.
>
>     **Osservazione:** il modello viene addestrato anche su i testi delle reviews grezzi (i.e. senza alcun tipo di pre-processing dei dati testuali). L'analisi del confronto dei
>     risultati (ottenuti per reviews "grezze" e reviews "pulite") fornirà qualche informazione sull'utilità di utilizzo della libreria NLTK.
>  4. addestramento e test del modello:
>     l'estrazione delle lexical-features dai dati di train viene eseguita attraverso il ricorso alla classe TfidVectorized del modulo scikit-learn. Si ottiene dunque
>     una nuova rappresentazione in forma matriciale dove le righe corrispondono ai testi e le colonne corrispondono a valori proporzionali alle features,
>     che tengono conto ella frequenza delle parole nel documento e della frequenza inversa nel corpus di addestramento (vedi [about TfidVectorizer](https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfVectorizer.html#) per maggiori info). Si addestra quindi il modello mediante l'algoritmo predittivo
>     Perceptron a cui vengono passate come input le lexical-features estratte e le rispettive etichette. L'analisi cross-domain ci impone poi di utilizzare iterativamente Perceptron
>     per l'addestramento e il test del modello sui testi delle reviews appartenenti a porzioni del dataset complessivo, ottenute considerando tutte le possibili combinazioni conseguibili
>     incrociando coppie di domini (si veda la documentazione del progetto per maggiori chiarimenti).
>
>     **Osservazione:** durante la fase di estrazione delle lexical-features si è deciso di far considerare all'istanza della classe TfidVectorizer le parole dei testi delle reviews
>     come unità di analisi per il vettorizzatore; in particolare questo valuta gli unigrammi (singole parole) e i bi-grammi (coppie di parole adiacenti), differentemente da lavoro
>     descritto in [Gräßer et al. 2018](https://dl.acm.org/doi/10.1145/3194658.3194677), in cui si considerano anche i trigrammi.
>  6. produzione dei risultati: Perceptron genera un quantificatore, definito accuratezza della predizione, ottenute per una valutazione di confronto tra l'array delle etichette reali dei dati
>     di test e l'array delle predizioni effettuate. L'accuratezza è dunque calcolata attraverso il rapporto tra le predizioni corrette rispetto al totale delle predizioni generate. Il
>     quantificatore associato sarà un numero compreso tra 0 (nessuna predizione corretta) e 1 (tutte le predizioni effettuate sono corrette).
