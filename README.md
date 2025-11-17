# autoRecon

Ces scripts fonctionnent pour l'instant depuis une machine Kali avec les outils installés dans le path.

Sinon il faut spécifier les chemins vers les outils au début de chaque script.


Automatise la reconnaissance a partir de tools bien connus.
Attention: Le but n'est pas de refaire nessus. Le but est simplement de gagner du temps sur ce que les auditeurs feraient de toute facon a la main.

Il faut donc que le tool reste rapide a executer.
Tres humblement les objectifs devraient s'en tenir a :
-Cartographier le reseau
-Identifier les low hanging fruits critiques
-Disposer d'outputs utilisables tels quels pour la suite du mandat
Ce qui est deja pas mal. Pour tout le reste il y a nessus

=autoNetRecon

Realise un maximum de recon basique sans authentification.


=autoADRecon

Realise un maximum de recon sur un AD avec les credentials de domaine fournis.
Permet de s'eviter le fastidieux saisie de credentials qui est differente pour chaque tool.



# TODO
- mettre chaque test dans une fonction qui puisse etre appelée indépendemment
- Meilleure gestion des options en ligne de commande
- Option de proxification des outils via un socks
- Scan du systeme pour retrouver les outils
- Utiliser la liste des domain computers obtenue via AD dans autoADrecon


In autoADrecon:
- netexec smb $SMBHOSTFILE -M ntlm_reflection
- #check for machine accounts rotation
https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/security-policy-settings/domain-member-disable-machine-account-password-changes

In autoNetRecon

- # check for vulnerabilities (where put these?)
- # Do the DC identification a second time during the scan
netexec smb ../carto_20251104-12-01/domainControllers.list.ips -M remove-mic
netexec smb ../carto_20251104-12-01/domainControllers.list.ips -M nopac
- responder-RunFinger
