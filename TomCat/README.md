# Installazione di TomCat

## Note Iniziali
Si ritiene **necessario** eseguire tutti i comandi sottostanti da **sudo!** <br>
Utilizzare SSH se si pensa che possa rendere il tutto più comodo. <br>


## :gear: Fase 1 - Preparazione del S.O. & Installazione di Java

Per aggiornare i programmi presenti nel sistema operativo eseguire i seguenti comandi: <br>
>         apt-get update
>         apt-get upgrade

Digitare il seguente comando:
>        java -version
Nel caso in cui java non fosse presente sarà visualizzato il seguente messaggio: <br>
> ![JavaNotFound](...) <br>
In questo caso basterà digitare ciò che ci viene suggerito. <br>

> Altrimenti sarà visualizzato un messaggio simile al seguente: <br>
![JavaFound](...) <br>
In quest'altro caso, invece, si può procedere alla prossima fase.

### CheckPoint
Se il seguente comando mostra che Java è presente sul sistema, è stato installato tutto correttamente!
>       java -version


## :gear: Fase 2 - Installazione di Tomcat

**Facoltativo** Il primo passaggio di affrontare prima della installazione di TomCat è quello di creare un utente apposito per la gestione di Apache TomCat: <br>
>         useradd -b /bin/bash -d /opt/tomcat -m username
_Nota: la directory può anche essere diversa da quella sopra idicata. In questo caso bisognerà scaricare, estrarre ed eseguire TomCat da lì._

Spostarsi nella directory nella quale si vuole scaricare e, in seguito, installare TomCat tramite il seguente comando:
>         cd directory

Una volta fatto ciò bisogna scaricare il programma:
1) Se si utilizza ubuntu tramite GUI basterà andare sul sequente [sito](https://tomcat.apache.org/download-90.cgi) e scaricare il file che finisce per .tar.gz

2) Se si vuole fare, invece, tramite linea di comando basterà usare il seguente comando:
>         wget https://downloads.apache.org/tomcat/tomcat-9/v9.0.41/bin/apache-tomcat-9.0.41.tar.gz

Estrarre il programma appena scaricato:
>         tar -xzvf fileName
_Note: se non riesci a estrarre il programma significa che il file scaricato non è quello desiderato. Di conseguenza è consigliato provare a riscaricarlo controllando che il comando sia stato scritto correttamente._

### CheckPoint
Se eseguendo i seguenti comandi notiamo che è presente la cartella decompressa, significa che abbiamo eseguito tutte le procedure correttamente:
>         cd /opt/tomcat/
>         ls

## :gear: Fase 3 - Avviare il programma:

Per avviare il programma basterà eseguire il seguente comando:
>         . /op/tomcat/bin/startup.sh

Una volta fatto ciò TomCat sarà "Up and running"!

### CheckPoint 
Per controllare se tomcat è stato installato correttamente basta andare su google e digitare localhost:8080. Se viene caricata la schermata di default significa che funziona tutto correttamente. <br>
![TomCat](...) <br>
