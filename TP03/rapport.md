                             contexte de l'exercice
Nous annonçons que le site bosch-cyber a été compromis, et que l'attaquant aurait exfiltré des outils secrets très dangereux !
Heureusement l'administration a mis le site sous maintenance, découvrez maintenant ce que l'attaquant a exfiltré !



                               I - PREPARATION 
   	

l'objectifs de ce projet est de determiner l'ensenble des outils que l'attaquant aurait exfiltré du site web

                               II-  INTRODUCTION 

le site bosch-cyber ayant été victime d'une compromission suite a cela elle cherche donc a savoir les outils qui ont été exfiltrer par l'attaque 
cyber-bosch a donc fait appel anous service pour faire une analyse et donner les outils derober par l'attaquant 

participants : les acteurs de ce projet sont : le site bosch-cybee en tant que client  et  TCHOUYA AUDREY comme executueur del'analyse 
du site , 
                                III-  METHODOLOGIE  

en vue de detreminer les outils et informations exfiltre nous allons faire une analyse preliminaire qui se deroule en plusieurs etape notamant :
Collecter toutes les informations disponibles sur la compromission ( log d'acces , log d'ereeur ; historique des commande ,historique bash)
Analyser les données nécessaires pour déterminer la méthode d'attaque utilisée pour nuire au site.
Vérifiez et déterminez quels fichiers ont été compromis et exfiltré (en analysant les ip , les url, les fichier malveilant ).

pour avoir l'historique exacte d'exfiltration il faut alayser les log systéme pour se faire nous allons commencer par les:

-afficher les logs systémes
-donner une analyse de ces logs

1) analyse des log d'accés 

 tail access.log

x-special/nautilus-clipboard
copy
file:///tmp/VMwareDnD/ftJJz3/img1.png 

- L'enregistrement 1 indique qu'une requête GET a été effectuée pour récupérer la ressource "nav.php" sur la branche "master" du répertoire "bosch/bosch.com/commits" par un
 utilisateur ayant l'adresse IP 216.244.66.248 . Le code de réponse HTTP 200 indique que la requête a réussi et renvoyé 28034 octets de données.
 L'agent utilisateur utilisé était "DotBot/1.2" de Moz.com.

- L'enregistrement 2 indique qu'une requête GET a été effectuée pour récupérer la ressource "encryption.php" sur la branche "master" du répertoire
"bosch/bosch.com/src" par un utilisateur ayant l'adresse IP 185.191.171.4 . Le code de réponse HTTP 200 indique que la requête a réussi et renvoyé 12591 octets de données.
l'agent utilisateur utilisé était "SemrushBot/7~bl" de Semrush.com.

- L'enregistrement 3 indique qu'une requête GET a été effectuée pour récupérer la ressource "Comment.php" sur la branche "master" du répertoire "bosch/note.bosch.com/blame" 
par un utilisateur ayant l'adresse IP 185.191 .171.8. Le code de réponse HTTP 200 indique que la requête a réussi et renvoyé 15864 octets de données. L'agent 
utilisateur utilisé était "SemrushBot/7~bl" de Semrush.com.

- L'enregistrement 4 indique qu'une requête GET a été effectuée pour récupérer la ressource "Filter.php" sur le commit "0aafe1b942e6eddb284df562df17745fa982f570" du répertoire
"bosch/note.bosch.com/blame" par un utilisateur ayant l'adresse IP 216.244 .66.248. Le code de réponse HTTP 200 indique que la requête a réussi et renvoyé 49693 octets de données.
l'agent utilisateur utilisé était "DotBot/1.2" de Moz.com.

- L'enregistrement 5 indique qu'une requête GET a été effectuée pour récupérer la ressource "myinfo.php" par un utilisateur ayant l'adresse IP 92.184.117.239.
le code de réponse HTTP 200 indique que la requête a réussi et renvoyé 3634 octets de données.l'agent utilisateur utilisé était "Chrome/108.0.0.0" d'Opera.

- L'enregistrement 6 indique qu'une requête GET a été effectuée pour la ressource "echo.php" par un utilisateur ayant l'adresse IP 5.188.210

2) analyse des log d'erreur

x-special/nautilus-clipboard
copy
file:///tmp/VMwareDnD/lVNZoR/img 2.png

- "pas d'amont en direct lors de la connexion à l'amont" indique qu'un serveur amont n'est pas accessible directement.
- "no live amont lors de la connexion à l'amont" signifie que le serveur amont est hors ligne ou ne répond pas.
"recv() a échoué (104 : réinitialisation de la connexion par l'homologue) lors de la lecture de l'en-tête de réponse en amont" indique une erreur de
 communication entre le serveur Nginx et le serveur amont.
- Ces erreurs peuvent être causées par des problèmes de configuration ou des erreurs de réseau. Il est recommandé de vérifier les paramètres de
configuration du serveur web et de s'assurer que le serveur amont est accessible et répond correctement


3) listing des exfiltration critique 

- la ressource "nav.php" sur la branche "master" du répertoire "bosch/bosch.com/commits" par un utilisateur ayant l'adresse IP 216.244.66.248.  L'agent utilisateur utilisé était "DotBot/1.2" de Moz.com.

- la ressource "encryption.php" sur la branche "master" du répertoire "bosch/bosch.com/src" par un utilisateur ayant l'adresse IP 185.191.171.4.   L'agent utilisateur utilisé était "SemrushBot/7~bl" de Semrush.com.

- la ressource "Comment.php" sur la branche "master" du répertoire "bosch/note.bosch.com/blame" par un utilisateur ayant l'adresse IP 185.191.171.8.  L'agent utilisateur utilisé était "SemrushBot/7~bl" de Semrush.com.

-la ressource "Filter.php" sur le commit "0aafe1b942e6eddb284df562df17745fa982f570" du répertoire "bosch/note.bosch.com/blame" par un utilisateur ayant l'adresse IP 216.244.66.248. L'agent utilisateur utilisé était "DotBot/1.2" de Moz.com.

                      IV - RESULTAT

a ) methode d'intrusion

l'attaquant a effectuer un ensemble de reque d'abord a l'exterieur puis , une fois a l'interieur du systéme il a effectuer un certains nombre de
 commande

x-special/nautilus-clipboard
copy
file:///tmp/VMwareDnD/Gi79R7/img 3.png

il a afficher des contenu , a crée une tache planifier dans opt/leak et a installer un fichier zip

b) resultat d'analyse 

L'analyse des log nous affiche un enregistrement de requêtes vers le serveur web le 4 septembre 2022. Les requêtes sont un mélange de requêtes GET vers 
différents fichiers et pages sur le serveur, avec différents codes de réponse et agents utilisateurs. Deux agents utilisateurs suspect sont  identifiés
dans le journal sont "DotBot/1.2" et "SemrushBot/7~bl"
 
-  IP 216.244.66.248.  L'agent utilisateur  "DotBot/1.2" de Moz.com.

-  IP 185.191.171.4.   L'agent utilisateur "SemrushBot/7~bl" de Semrush.com.

-  IP 185.191.171.8.  L'agent utilisateur  "SemrushBot/7~bl" de Semrush.com.

- IP 216.244.66.248. L'agent utilisateur "DotBot/1.2" de Moz.com.

c) conclusion 

Il est important de noté que l'attaquant n'a pas seulement  effectuer des requetes , efiliter des données trés importantes , celui ci a egalement cree une 
tache planifié et installé un  zip.

 
 
                            V- RECONMANDATIONS 

-  verifiez zt mettre a jour les configurations  

- Vérifiez-vous que votre code est correctement testé et sans erreurs. Vérifiez également que tous les fichiers nécessaires sont présents sur le serveur.

- utilisez HTTPS pour sécuriser les connexions. Cela peut aider à empêcher les attaquants d'intercepter les données en transit.

- Limitez l'accès à votre site web en utilisant des pare-feux et des listes de contrôle d'accès pour éviter les connexions non autorisées.

- utiliser un outil de surveillance de site web pour détecter rapidement toute


              VI- CONCLUSION GENERALE 

l' analyse nous a permit de determiner par l'attaquant  les  outils exfiltrés "nav.php" , "encription.php" ," comment.php"
 
