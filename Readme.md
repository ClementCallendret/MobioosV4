Readme:

Ce projet se base sur la démo de Broadleaf Commerce : https://github.com/BroadleafCommerce/DemoSite

------------------------------------------------------------------------------------------------------
Prérequis :
-Windows
-Visual Studio Code

Extension vs code :
    Nécessaire : 
    -Mobioos Forge (extension id : Mobioos.mobioos-forge)
    -Extension Pack for Java (extension id : vscjava.vscode-java-pack)

    Optionnelle : 
    -Dependency Analytics (extension id : redhat.fabric8-analytics)
------------------------------------------------------------------------------------------------------
Initialisation :
    -LIRE LA DOC MOBIOOS : https://documentation.mobioos.ai/?id=what-is-mobioos-forge 

    -cloner le github dans votre répertoire favoris
    -supprimer le fichier .git, car Mobioos tentera de créer une branche par variant créé sur ce repo.
    -ouvrir le projet dans Vscode
    -2 possibilités :
        -avoir les variants créé sur github -> Initialiser un répertoire github public 
        (Pourquoi un répertoire public ? Dans nos tests mobioos n'a pas réussi a push la branche sur un rep privé. Et une fois le projet Mobioos initialiser, changer le github de public à privé ne résoud pas le pb).
        -avoir les variants en local -> ne rien faire
    -Cliquer dans la barre verticale à gauche sur le M de Mobioos Forge Explorer
    -Faire "Open Project" et cliquer sur le dossier de ce projet
    -Un onglet nommé "BroadleafCommerce" apparait

------------------------------------------------------------------------------------------------------
Utilisation :
    -Voir diagramme du projet -> Dans l'onglet Mobioos Forge Explorer, clique droit sur "BroadleafCommerce" -> MF : Design the feature model. Un nouvel onglet s'ouvre avec le diagramme.
    
    -Voir le mappage des fichiers -> aller à BroadleafCommerce -> DemoSite -> site -> src\main et cliquer sur des fichiers. 
     pas de couleur = pas mappé (car essentiel ou pas d'importance côté utilisateur mais potentiellement inutilisé dans certains variants)
     une couleur = mappé, mettre la souris dessus et le nom de la feature correspondante à ce code apparaît.

    -Créer un variant -> 
        -Dans l'onglet Mobioos Forge Explorer, aller tout en bas à "Customization Scenarios", cliquer sur le "+" tout à droite du titre
        -Entrer le nom de votre configuration et appuyer sur Entrer (Il faut un nom qui ne soit pas déjà pris. Pour voir la liste des configurations déjà créer, dérouler l'onglet "Customization Scenarios")
        -Un nouvel onglet apparait. Des cases sont déjà cochées, en jaune, c'est les éléments minimums nécessaires au bon fonctionnement du site. Vous pouvez rajouter des options en cliquant dessus.
        (Certaines options dépendent d'autres, comme "Login" et "Customer Account Informations", donc si vous en voulez une, l'autre ce cochera automatiquement.)
        -Cliquer sur "Save"
        


        -Cliquer sur "Generate" : 2 possibilités en fonction de ce que vous avez choisi ci-dessus:
            -Si vous voulez votre variant sur une branche Github, verifier que votre branche actuel et Commit. Ecrire le nom de la branche qui va être créée et attendre que le variant soit push. (Ne pas se fier à la notification qui dit que c'est en cours de push, aller voir directement sur votre navigateur si c'est bon).
            Aller sur la branche voulu (rafraichir les infos de github pour faire apparaitre la branche sur Vscode)

            -Si vous voulez votre variant en local, appuyer sur Echap quand le nom de la branche est demandée. Cliquer sur la pop up à droite qui propose d'ouvrir le projet créé. Le variant est par défaut stocké à Users\VotreUsername\mobioos-forge-customizations

        -Maintenant le variant créé, ouvrer un terminal et entrer :
         "cd DemoSite ; mvn clean install ; cd site ; mvn spring-boot:run ; mvn spring-boot:run ; mvn spring-boot:run"
        Ou aller dans le répertoire "DemoSite", lancer la compilation avec mvn clean install (Il est possible qu'elle échoue, relancer là le cas échéant. Si après plusieurs tentatives elle continue d'échouer, tenter de passer à la suite, parfois ça se lance quand même).

        Aller dans le dossier "site" et lancer dans un terminal mvn spring-boot:run (Si vous arrêter le programme avec un Ctrl + C le port reste ouvert, donc quand vous aller essayer de le relancer une erreur apparaitra, ce n'est pas grave, relancer la commande une nouvelle fois, 3 fois max).
        
        -Attendre que le lancement soit fini (20 à 50s)
        -Connexion au site client:
        http://localhost:8080
        https://localhost:8443

        -Pour se connecter ailleurs voir les ports sur https://github.com/BroadleafCommerce/DemoSite#active-ports