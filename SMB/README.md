# Configurazione Protocollo Samba


## :gear: Fase 1 - Preparazione del S.O.
> Per aggiornare i programmi presenti nel sistema operativo eseguire i seguenti comandi: <br>
 ***apt-get update*** <br>
 ***apt-get upgrade*** <br>

> Inoltre, è necessario controllare se Samba è presente sul sistema operativo: <br>
 ***whereis samba*** <br>
 Il comando restituirà due output differenti. <br>
 Se Samba **è presente** verrà restituita la directory dove è installato; <br>
 Se Samba **non è presente** sarà restituito un messaggio indicante la mancata presenza del programma. <br>
 
 
## :gear: Fase 2 - Installazione di Samba e configurazione

> Se Samba non è presente, installarlo: <br>
***apt-get install samba*** <br>

> Creazione di un utente per Samba: <br>
***useradd -b /bin/bash -d /home/username/sambaFolder -m username*** <br>
***passwd username*** <br>
Così facendo per accedere alla cartella di Samba da quasiasi sistema si drovrà mettere username e password diverse da quelle "principali". <br>
_Nota: nel caso in cui la password sarà inferiore verrà visualizzato un messaggio indicante la mancata sicurezza di quest'ultima_ <br>

> Configurazione del file di Samba: <br>
***nano /etc/samba/smb.conf*** <br>
Configurare il file come quello presente [qui](/SMB/Files/smb.conf) <br>
_Nota: di quel file sono state modificate solamente le ultime righe alle quali è stata aggiunta la sezione [sambashare] e le righe di testo presenti in essa_

-sudo nano 7etc/samba/smb.conf 
	[sambashare]
		comment = Samba on Ubuntu
		path = /home/username/sambashare
		read only = no
		browsable = yes
		(FILE DI ESEMPIO)
		
> Creare un'eccezione nel firewall per Samba: <br>
***ufw allow samba*** <br>

> Riavviare Samba: <br>
***servive smdb restart*** <br>

-Aggiungere l'user a samba con smbpasswd -a username --> passwd --> passwd
- Provare la connessione :D
- se ci sono problemi provare a controllare il file di configurazione
