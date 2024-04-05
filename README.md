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
> Informazioni utili
> 
> L'implementazione del codice necessario alla realizzazione del progetto segue le seguenti fasi:
>  1. preparazione del dataset
>  2. realizzazione del modello
>  3. addestramento e test del modello 
>  4. produzione dei risultati
