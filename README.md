<h1>Introduction</h1>

AppDailySales est un script Python qui permettent de télécharger des fichiers de rapport quotidien des ventes à partir du site Web iTunes Connect.

<h1>Référentiel de code source a déménagé</h1>
Le référentiel de code source de ce script a déménagé à github . Il est maintenant disponible à l'adresse: https://github.com/hacker404/appdailysales

<h1>Comment utiliser</h1>
AppDailySales peuvent être utilisés en tant que programme autonome ou en tant que partie d'un autre script.

<h1>Utilisez comme programme autonome</h1>
Télécharger le appdailysales.py de script et exécutez la ligne de commande:

<h1>python appdailysales.py</h1>
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

<h1>Remarque:</h1> Le script retournera le code de sortie 0 en cas de succès, sinon le code de sortie 1 est renvoyé.

<h1>Utiliser comme partie d'un autre script</h1>
Depuis la version 1.3 de la AppDailySales script peut être utilisé dans le cadre d'un autre script. Il suffit de appdailysales d'importation, définissez les options de rapport, et appellent la fonction downloadFile. Voici un fichier de script pour vous aider à démarrer:

 Identifiant Apple » 
  des options . mot de passe =  'Votre 
  

     fichier téléchargé: ' , nom de fichier 
  , sauf : 
    retraçage . print_exc () 
        
si __name__ ==  '__main__ " : 
  principal ()
  
La fonction appdailysales.downloadFile retourne le nom du dernier fichier téléchargé. Veillez à inclure un bloc de try..except autour de l'appel à la gérer correctement les erreurs qui peuvent se produire pendant le téléchargement.

<h1>Téléchargez les rapports sur plusieurs jours</h1>
Depuis la version 1.6, il existe une option -d (--days aussi) qui est utilisé pour spécifier le nombre de jours à télécharger. La valeur par défaut est 1, qui va télécharger le rapport d'hier et maintient le script compatible avec les versions précédentes. Toute valeur peut être utilisée pour cette option. Cependant se il vous plaît noter que comme de maintenant Apple ne stocke les 7 derniers jours des rapports de vente quotidiens. En utilisant une valeur supérieure à 7 se traduira par un "rapport non disponible» erreur.

Pourquoi ne pas ajouter un contrôle dans le script pour empêcher des valeurs supérieures à 7? Je décidai de ne pas inclure le contrôle à tout hasard Apple décide de donner accès à des rapports de plus de 7 jours.

<h1>Rapport de fichier Nom de formatage</h1>
Version 2.1 introduit la nouvelle option (également --format) -f. Cette option vous permet de reformater le nom du fichier de rapport. Le format est spécifique comme par strftime (voir page de man), par exemple "% Y-% m-% d-daily.txt.gz« vous donnerait "2010-09-16-daily.txt.gz".

Par défaut, le fichier de rapport est comprimé. Lorsque vous utilisez l'option -f, assurez-vous d'inclure l'extension de nom de fichier approprié, par exemple, ".gz". Utilisez l'option -u pour avoir le script de décompresser le fichier pour vous. Le script va automatiquement enlever l'extension .gz si présent.

<h1>Quelle version de Python</h1>
Le script a été écrit pour et a été testé avec la version 2.5.x Python, 2.6.x, 2.7.x et . Il est peu probable que le script ne fonctionne avec Python 3.x sans quelques ajustements.

<h1>Mise au point du script</h1>
La version 2.4 introduit le nouveau drapeau de --debug. Cet indicateur affiche la sortie prolixe supplémentaire pour le débogage et le dépannage du script. Aussi, lorsque ce drapeau est activé et le script rencontre une erreur de grattage écran, un fichier nommé temp.html est créé et stocké dans le répertoire de sortie. Ce fichier contient le code HTML téléchargé dans la dernière requête Web.

<h1>Historique des modifications</h1>
<font>Version 2.9</font>

Crée automatiquement les répertoires ajoutés au format imbriqués (-f) des chaînes (p. -f% Y /% Y-% m /% Y% tous les jours- m-% d.txt). Fonctionne avec outputDirectory (-o). (Merci Mike Kasprzak)
Nouvelle option en ligne de commande "-n". Utilisé avec le format (-f), un fichier qui existe déjà ne sont pas téléchargées. (Merci Mike Kasprzak)
Ajout du support proxy. (Merci stakemura)
<font>Version 2.8</font>

Mise à jour du script pour soutenir les derniers changements de l'ITC.
Déplacez référentiel de code source à github. ( https://github.com/hacker404/appdailysales )
<font>Version 2.7</font>

Modifié le script pour faire plusieurs tentatives de chargement de la page par défaut du fournisseur avant de signaler une erreur.
Changé la façon dont la disposition de contenu est vérifié pour éviter les tentatives de décompression HTML.
<font>Version 2.6</font>

Mise à jour du script pour soutenir la nouvelle URL du site Web de vente et tendances. (Merci ferenc.vehmann)
Activé soutien RFC2965 cookie. (Merci troegenator)
<font>Version 2.5</font>

Mise à jour pour afficher les messages de notification, le cas échéant, d'Apple affiche sur le chiffre d'affaires et les tendances tableau de bord. Vous devez utiliser l'option -v ou --verbose pour voir le message de notification.
<font>Version 2.4</font>

Mise à jour pour supporter les dernières modifications iTC de site Web.
-v Jour (verbose) pour afficher les messages de l'utilisateur plus conviviale.
Ajouté drapeau --debug. Fournit plus une sortie verbeuse pour le débogage et le dépannage.
Mise à jour à gratter la page des fournisseurs et effectuer le réglage de fournisseur par défaut.
Mise à jour à gratter pour la liste des dates disponibles du rapport.
Mise à jour à télécharger les rapports ne sont disponibles. Un message est affiché quand un rapport demandé ne sont pas disponibles.
<font>Version 2.3</font>

Mise à jour de gratter l'écran pour la vente et les tendances URL.
<font>Version 2.2</font>

Remplacé le "par" déclaration, qui causait des problèmes sur différentes plates-formes et avec version différente de python, avec le code plus compatible.
<font>Version 2.1</font>

Ajoute nouvelle option -f (également --format) pour reformater le nom du fichier de rapport. (Merci Daniel Dickison.)
Mise à jour pour afficher un message invalide connexion des titres de compétences si le processus de connexion échoue. (Merci Daniel Dickison.)
L'option -v (verbose aussi) va sauver le dernier html récupéré dans le fichier temp.html. Ceci est utile lorsque troubler un problème avec grattage écran du site web. Le temp.html est automatiquement supprimé lorsque le script télécharge avec succès le rapport. (Merci Daniel Dickison.)
Le -P (également --passwordStdin) affiche désormais le message «Mot de passe»
<font>Version 2.0.2</font>

Suppression de paramètre non valide utilisé pour concentrer une erreur et tester de nouveaux rapports d'erreur.
<font>Version 2.0.1</font>

Améliorer les rapports d'erreur
<font>Version 2.0</font>

Mise à jour de support 9 Septembre, 2010 iTunes Connect changements.
Soutien BeautifulSoup chuté. Je ne ai pas le temps d'appuyer deux approches de grattage écran séparés.
<font>Version 1.10</font>

Correction de bugs causés par les récents changements iTunes Connect.
<font>Version 1.9</font>

Patch appliquée qui ajoute un nouveau de lire le mot de passe de l'entrée standard (merci Martin Billemont).
<font>Version 1.8.1</font>

Code modifié pour fonctionner avec les dernières modifications iTunes Connect (merci Andrew de los Reyes).
<font>Version 1.8</font>

Maintenant utilise os.path.join pour éviter les problèmes avec un slash ou le manque de lorsque vous spécifiez le répertoire de sortie (merci Keith Simmons).
<font>Version 1.7</font>

Code qui a reçu les dates disponibles du rapport de l'HTML retiré. Cette cassé la compatibilité ascendante lors de l'utilisation BeautifulSoup et était trompeuse quand Apple a retardé les rapports "d'hier".
Ajouté à -D (--date également) option qui permet le téléchargement d'une date spécifique. Remarque: la date doit être jj / mm / aaaa.
<font>Version 1.6</font>

Modifié à utiliser BeautifulSoup est disponible (grâce Rogue Amoeba Software, LLC)
Logique de décompression modifié pour fonctionner uniquement en mémoire, ce qui rend plus rapide et moins sujette aux erreurs (grâce Rogue Amoeba Software, LLC)
Ajouté jours pour télécharger l'option (-d ou compter les jours), peut être utilisé pour télécharger tous les rapports disponibles
<font>Version 1.5</font>

Script mis à jour pour fonctionner avec les dernières modifications du site web
Suppression de sortie de trackback lorsque l'utilisation est affiché
<font>Version 1.4</font>

Modifié à utiliser itts.apple.com comme le point de départ; élimine 2 appels HTTP (grâce à Leon Ho pour fournir le changement)
Ajout d'une vérification d'erreur pour le fichier de téléchargement; de rapport non disponible 'impressions de message si elle est détectée
<font>Version 1.3</font>

Script à exécuter en tant que programme autonome ou comme partie d'un autre script modifié
<font>Version 1.2</font>

Options de ligne de commande ajoutée (fichier de script d'édition ne sont plus nécessaires)
Possibilité de décompresser le fichier de téléchargement Ajouté
<font>Version 1.1</font>

Première version
<h1>Collaborateurs</h1>
Des remerciements spéciaux vont aux personnes suivantes pour leur contribution à ce projet:

Leon Ho
Rogue Amoeba Software, LLC
Keith Simmons
Andrew de los Reyes
Maarten Billemont
Daniel Dickison
Mike Kasprzak
stakemura
<h1>Certains Final Words</h1>
Je créé ce script avec le développeur iPhone à l'esprit. Être un développeur iPhone moi, je ne veux pas me souvenir pour télécharger le rapport quotidien des ventes de l'activité de hier, donc je l'ai écrit ce script. Je dois une tâche cron planifiée sur un serveur qui va télécharger le rapport de chaque jour pour moi, donc je ne dois pas. Est pas grande automatisation.
