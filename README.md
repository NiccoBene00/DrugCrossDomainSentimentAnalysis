# Cross domain sentiment analysis on drugs reviews - AI 23/24 UNIFI
## Studente: Niccolò Benedetto MAT. 7024656
## Docente: Paolo Frasconi

> [!IMPORTANT]
> Contenuto della repository:
>  - **Cross_Domain_SentimentAnlysis.ipynb**, Jupyter Notebook del codice del progetto implementato con [Google Colab](https://colab.google/).
>  - **CD_SentimentAnalysis.pdf**, file pdf generato con software [LaTeX](https://www.latex-project.org/) inerente alla documentazione del progetto.


**Project Assignment**:

In questo esercizio si utilizzano implementazioni disponibili dell’algoritmo Perceptron (p.es. [scikit-learn](https://scikit-learn.org/stable/) 
in Python o [Weka](https://ml.cms.waikato.ac.nz/weka/) in Java) al problema dell’analisi del sentimento su recensioni di farmaci, come descritto
in [Gräßer et al. 2018](https://dl.acm.org/doi/10.1145/3194658.3194677), cercando di riprodurre risultati analoghi a quelli riportati nella tabella 3 dell’articolo (caso cross-domain).  I risultati numerici potranno differire dato che gli autori utilizzano un classificatore diverso. Il dataset è disponibile sul [repository di UCI](https://archive.ics.uci.edu/ml/datasets/Drug+Review+Dataset+%28Drugs.com%29). È accettabile utilizzare un sottoinsieme dei dati e/o semplificare gli attributi lessicali (p.es. evitando i trigrammi) se le risorse di calcolo disponibili fossero insufficienti.


> [!NOTE]
> **Informazioni utili**
> 
> L'implementazione del codice necessario alla realizzazione del progetto segue le seguenti fasi
>  1. preparazione dei dati del dataset:
>     pre-processing del testo delle reviews attraverso la libreria [NLTK](https://www.nltk.org/#natural-language-toolkit) e valutazione della polarità 
>     mediante il tool [VADER](https://pypi.org/project/vaderSentiment/). La valutazione di polarità fornirà un quantificatore (numero reale) che viene sfruttato per definire
>     una nuova colonna del database, che rappresenta un nuovo valore di rating, il quale verrà utilizzato come etichetta del modello. In particolare sei il quantificatore rientra nel range [-1;0.3] allora il     >     valore di rating è 0 (sentimento negativo), se cade in (-0.3;0.3) allora rating corrisponde a 1 (sentimento neutro), mentre se
>     rientra nell'intervallo [0.3;1] rating equivale a 2 (sentimento positivo).
> 
>     **Osservazione:** il range scelto per definire il nuovo valore di rating è da ritenersi congruo con il significato dei valori di compound generati dal tool VADER. Scelte di intervalli diversi
>     potranno, a seguito dell'addestramento del modello, produrre risultati diversi.
> 
>     **Citazioni**
>     
>     [1] @Hutto, C.J. & Gilbert, E.E. (2014). VADER: A Parsimonious Rule-based Model for Sentiment Analysis of Social Media Text. Eighth International Conference on Weblogs and Social Media (ICWSM-14). Ann 
>         Arbor, MI, June 2014.
>  3. realizzazione del modello:
>  5. addestramento e test del modello 
>  6. produzione dei risultati
