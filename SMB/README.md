comandi:
-Verificare che il so sia aggiornato (update & upgrade)
-Controllare se è presente samba
	- se si top
	- se no installa con apt-get install samba
-creare utente per samba (useradd -b /bin/bash -d /home/username/sambaFolder -m username)
-aggiungere password all'user con passwd username --> pass --> pass (mostra messaggio se < 8 caratteri)
-sudo nano 7etc/samba/smb.conf 
	[sambashare]
		comment = Samba on Ubuntu
		path = /home/username/sambashare
		read only = no
		browsable = yes
		(FILE DI ESEMPIO)
- service smdb restart --> Restartaimo
- sudo ufw allow samba --> Mettiamo i permessi per samba nel firewall

-Aggiungere l'user a samba con smbpasswd -a username --> passwd --> passwd
- Provare la connessione :D
- se ci sono problemi provare a controllare il file di configurazione