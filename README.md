appdailysales
=============
script Python pour télécharger iTunes Connect rapports de vente quotidiens.

Introduction
AppDailySales est un script Python qui permettent de télécharger des fichiers de rapport quotidien des ventes à partir du site Web iTunes Connect.

Référentiel de code source a déménagé
Le référentiel de code source de ce script a déménagé à github . Il est maintenant disponible à l'adresse: https://github.com/kirbyt/appdailysales

Comment utiliser
AppDailySales peuvent être utilisés en tant que programme autonome ou en tant que partie d'un autre script.

Utilisez comme programme autonome
Télécharger le appdailysales.py de script et exécutez la ligne de commande:

python appdailysales.py
utilisation : appdailysales . py [ Options ] 
options  et arguments : 
- h      :  imprimer  ce message d'aide et  de sortie  ( aussi - aide ) 
- un uid : votre ID de pomme ( également - AppleID ) 
- p pwd : votre mot de passe ( également - mot de passe ) 
- P      : lire le mot de passe de l'entrée standard ( également - passwordStdin ) 
- o dir : répertoire où le fichier de téléchargement est stocké ,  par défaut  est le répertoire de travail courant ( également - outputDirectory ) 
- v      : sortie verbeuse ,  par défaut  est off ( également - verbose ) 
- u      : fichier de téléchargement décompression ,  par défaut  est de ( aussi - décompression ) 
- d num : nombre de jours à télécharger ,  par défaut  est  1  ( aussi - jours ) 
- mm D / jj / aaaa : la date du rapport de télécharger ,  - option d est ignoré lorsque  - D est utilisé ( également - la date ) 
- f le format : format de nom de fichier de sortie ( voir strftime ; aussi - Format ) 
- n       : utilisé avec  - f , saute le téléchargement de fichiers de rapport que déjà exister ( également - noOverWriteFiles ) 
- proxy : URL du proxy 
- debug : sortie de débogage ,  par défaut  est off
Vous pouvez également modifier les variables d'option situés vers le haut du fichier de script si vous préférez ne pas utiliser les options de ligne de commande. Cependant, cette approche est déconseillée avec la version 1.2 et supérieure du fichier de script.

Remarque: Le script retournera le code de sortie 0 en cas de succès, sinon le code de sortie 1 est renvoyé.

Utiliser comme partie d'un autre script
Depuis la version 1.3 de la AppDailySales script peut être utilisé dans le cadre d'un autre script. Il suffit de appdailysales d'importation, définissez les options de rapport, et appellent la fonction downloadFile. Voici un fichier de script pour vous aider à démarrer:









 Identifiant Apple » 
  des options . mot de passe =  'Votre 
 
 
 
  

     fichier téléchargé: ' , nom de fichier 
  , sauf : 
    retraçage . print_exc () 
        
si __name__ ==  '__main__ " : 
  principal ()
La fonction appdailysales.downloadFile retourne le nom du dernier fichier téléchargé. Veillez à inclure un bloc de try..except autour de l'appel à la gérer correctement les erreurs qui peuvent se produire pendant le téléchargement.

Téléchargez les rapports sur plusieurs jours
Depuis la version 1.6, il existe une option -d (--days aussi) qui est utilisé pour spécifier le nombre de jours à télécharger. La valeur par défaut est 1, qui va télécharger le rapport d'hier et maintient le script compatible avec les versions précédentes. Toute valeur peut être utilisée pour cette option. Cependant se il vous plaît noter que comme de maintenant Apple ne stocke les 7 derniers jours des rapports de vente quotidiens. En utilisant une valeur supérieure à 7 se traduira par un "rapport non disponible» erreur.

Pourquoi ne pas ajouter un contrôle dans le script pour empêcher des valeurs supérieures à 7? Je décidai de ne pas inclure le contrôle à tout hasard Apple décide de donner accès à des rapports de plus de 7 jours.

Rapport de fichier Nom de formatage
Version 2.1 introduit la nouvelle option (également --format) -f. Cette option vous permet de reformater le nom du fichier de rapport. Le format est spécifique comme par strftime (voir page de man), par exemple "% Y-% m-% d-daily.txt.gz« vous donnerait "2010-09-16-daily.txt.gz".

Par défaut, le fichier de rapport est comprimé. Lorsque vous utilisez l'option -f, assurez-vous d'inclure l'extension de nom de fichier approprié, par exemple, ".gz". Utilisez l'option -u pour avoir le script de décompresser le fichier pour vous. Le script va automatiquement enlever l'extension .gz si présent.

Quelle version de Python
Le script a été écrit pour et a été testé avec la version 2.5.x Python, 2.6.x, 2.7.x et . Il est peu probable que le script ne fonctionne avec Python 3.x sans quelques ajustements.

Mise au point du script
La version 2.4 introduit le nouveau drapeau de --debug. Cet indicateur affiche la sortie prolixe supplémentaire pour le débogage et le dépannage du script. Aussi, lorsque ce drapeau est activé et le script rencontre une erreur de grattage écran, un fichier nommé temp.html est créé et stocké dans le répertoire de sortie. Ce fichier contient le code HTML téléchargé dans la dernière requête Web.

Historique des modifications
Version 2.9

Crée automatiquement les répertoires ajoutés au format imbriqués (-f) des chaînes (p. -f% Y /% Y-% m /% Y% tous les jours- m-% d.txt). Fonctionne avec outputDirectory (-o). (Merci Mike Kasprzak)
Nouvelle option en ligne de commande "-n". Utilisé avec le format (-f), un fichier qui existe déjà ne sont pas téléchargées. (Merci Mike Kasprzak)
Ajout du support proxy. (Merci stakemura)
Version 2.8

Mise à jour du script pour soutenir les derniers changements de l'ITC.
Déplacez référentiel de code source à github. ( https://github.com/hacker404t/appdailysales )
Version 2.7

Modifié le script pour faire plusieurs tentatives de chargement de la page par défaut du fournisseur avant de signaler une erreur.
Changé la façon dont la disposition de contenu est vérifié pour éviter les tentatives de décompression HTML.
Version 2.6

Mise à jour du script pour soutenir la nouvelle URL du site Web de vente et tendances. (Merci ferenc.vehmann)
Activé soutien RFC2965 cookie. (Merci troegenator)
Version 2.5

Mise à jour pour afficher les messages de notification, le cas échéant, d'Apple affiche sur le chiffre d'affaires et les tendances tableau de bord. Vous devez utiliser l'option -v ou --verbose pour voir le message de notification.
Version 2.4

Mise à jour pour supporter les dernières modifications iTC de site Web.
-v Jour (verbose) pour afficher les messages de l'utilisateur plus conviviale.
Ajouté drapeau --debug. Fournit plus une sortie verbeuse pour le débogage et le dépannage.
Mise à jour à gratter la page des fournisseurs et effectuer le réglage de fournisseur par défaut.
Mise à jour à gratter pour la liste des dates disponibles du rapport.
Mise à jour à télécharger les rapports ne sont disponibles. Un message est affiché quand un rapport demandé ne sont pas disponibles.
Version 2.3

Mise à jour de gratter l'écran pour la vente et les tendances URL.
Version 2.2

Remplacé le "par" déclaration, qui causait des problèmes sur différentes plates-formes et avec version différente de python, avec le code plus compatible.
Version 2.1

Ajoute nouvelle option -f (également --format) pour reformater le nom du fichier de rapport. (Merci Daniel Dickison.)
Mise à jour pour afficher un message invalide connexion des titres de compétences si le processus de connexion échoue. (Merci Daniel Dickison.)
L'option -v (verbose aussi) va sauver le dernier html récupéré dans le fichier temp.html. Ceci est utile lorsque troubler un problème avec grattage écran du site web. Le temp.html est automatiquement supprimé lorsque le script télécharge avec succès le rapport. (Merci Daniel Dickison.)
Le -P (également --passwordStdin) affiche désormais le message «Mot de passe»
Version 2.0.2

Suppression de paramètre non valide utilisé pour concentrer une erreur et tester de nouveaux rapports d'erreur.
Version 2.0.1

Améliorer les rapports d'erreur
Version 2.0

Mise à jour de support 9 Septembre, 2010 iTunes Connect changements.
Soutien BeautifulSoup chuté. Je ne ai pas le temps d'appuyer deux approches de grattage écran séparés.
Version 1.10

Correction de bugs causés par les récents changements iTunes Connect.
Version 1.9

Patch appliquée qui ajoute un nouveau de lire le mot de passe de l'entrée standard (merci Martin Billemont).
Version 1.8.1

Code modifié pour fonctionner avec les dernières modifications iTunes Connect (merci Andrew de los Reyes).
Version 1.8

Maintenant utilise os.path.join pour éviter les problèmes avec un slash ou le manque de lorsque vous spécifiez le répertoire de sortie (merci Keith Simmons).
Version 1.7

Code qui a reçu les dates disponibles du rapport de l'HTML retiré. Cette cassé la compatibilité ascendante lors de l'utilisation BeautifulSoup et était trompeuse quand Apple a retardé les rapports "d'hier".
Ajouté à -D (--date également) option qui permet le téléchargement d'une date spécifique. Remarque: la date doit être jj / mm / aaaa.
Version 1.6

Modifié à utiliser BeautifulSoup est disponible (grâce Rogue Amoeba Software, LLC)
Logique de décompression modifié pour fonctionner uniquement en mémoire, ce qui rend plus rapide et moins sujette aux erreurs (grâce Rogue Amoeba Software, LLC)
Ajouté jours pour télécharger l'option (-d ou compter les jours), peut être utilisé pour télécharger tous les rapports disponibles
Version 1.5

Script mis à jour pour fonctionner avec les dernières modifications du site web
Suppression de sortie de trackback lorsque l'utilisation est affiché
Version 1.4

Modifié à utiliser itts.apple.com comme le point de départ; élimine 2 appels HTTP (grâce à Leon Ho pour fournir le changement)
Ajout d'une vérification d'erreur pour le fichier de téléchargement; de rapport non disponible 'impressions de message si elle est détectée
Version 1.3

Script à exécuter en tant que programme autonome ou comme partie d'un autre script modifié
Version 1.2

Options de ligne de commande ajoutée (fichier de script d'édition ne sont plus nécessaires)
Possibilité de décompresser le fichier de téléchargement Ajouté
Version 1.1

Première version
Collaborateurs
Des remerciements spéciaux vont aux personnes suivantes pour leur contribution à ce projet:

Leon Ho
Rogue Amoeba Software, LLC
Keith Simmons
Andrew de los Reyes
Maarten Billemont
Daniel Dickison
Mike Kasprzak
stakemura
Certains Final Words
Je créé ce script avec le développeur iPhone à l'esprit. Être un développeur iPhone moi, je ne veux pas me souvenir pour télécharger le rapport quotidien des ventes de l'activité de hier, donc je l'ai écrit ce script. Je dois une tâche cron planifiée sur un serveur qui va télécharger le rapport de chaque jour pour moi, donc je ne dois pas. Est pas grande automatisation.
