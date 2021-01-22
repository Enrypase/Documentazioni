# Configurazione Protocollo Samba


## :gear: Fase 1 - Preparazione del S.O.
Per aggiornare i programmi presenti nel sistema operativo eseguire i seguenti comandi: <br>
>     apt-get update
>     apt-get upgrade

Inoltre, è necessario controllare se Samba è presente sul sistema operativo: <br>
>     whereis samba
Il comando restituirà due output differenti. <br>
Se Samba **è presente** verrà restituita la directory dove è installato; <br>
Se Samba **non è presente** sarà restituito un messaggio indicante la mancata presenza del programma. <br>
 
 
## :gear: Fase 2 - Installazione di Samba e configurazione

Se Samba non è presente, installarlo:
>     apt-get install samba
### CheckPoint:
Per controllare se l'installazione di Samba è andato a buon fine basta digitare: <br>
>     systemctl status samba
Se il programma risulta essere installato, di conseguenza, significa l'installazione essere andata a buon fine <br>

reazione di un utente per Samba: <br>
>     useradd -b /bin/bash -d /home/username/sambaFolder -m username
>     passwd username
Così facendo per accedere alla cartella di Samba da quasiasi sistema si drovrà mettere username e password diverse da quelle "principali". <br>
_Nota: nel caso in cui la password sarà inferiore verrà visualizzato un messaggio indicante la mancata sicurezza di quest'ultima_ <br>
### CheckPoint:
L'effettiva esecuzione delle operazioni si presume se non vengono visualizzati messaggi di errore e, verificata, una volta che si tenterà la connessione. <br>

Configurazione del file di Samba: <br>
>     nano /etc/samba/smb.conf
Configurare il file come quello presente [qui](/SMB/Files/smb.conf) <br>
_Nota: di quel file sono state modificate solamente le ultime righe alle quali è stata aggiunta la sezione [sambashare] e le righe di testo presenti in essa_
### CheckPoint:
L'effettiva esecuzione delle operazioni si presume se non vengono visualizzati messaggi di errore e, verificata, una volta che si tenterà la connessione. <br>		

Creare un'eccezione nel firewall per Samba: <br>
>     ufw allow samba

Riavviare Samba: <br>
>     servive smdb restart

Per completare il tutto, aggiungere un username a Samba:
>     smbpasswd -a username
_Nota: nel caso in cui si volesse rimuovere un esername da samba è necessario utilizzare ***pdbedit -x -u username***_


## :gear: Fase 3 - Connessione alla cartella condivisa
> Se si utilizza **windows** basta andare nell'esplora risorse e inserire il seguente percorso: ***\\\ip-address\sharedFolder***
![ConnessioneWindows](/SMB/Immagini/ConnessioneWindows)

> Se si utilizza un sistema **Ubuntu** oppure ***macOS***, invece, digitare il seguente percorso: ***smb://ip-address/sharedFolder***
![ConnessioneUbuntu](/SMB/Immagini/ConnessioneUbuntu)
