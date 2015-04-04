Création de son premier dépôt
=============================

Nous allons voir 2 possibilités pour créer un dépôt. La première nous créerons un dépot depuis notre PC, et la seconde en clonant un dépôt Github.

Création d'un dépôt
-------------------

Se placer dans le dossier du projet ou en créer un.
Puis on tape la commande suivante:

.. code-block:: bash

	git init

Le dépôt est créé, un fichier ``.git`` est créé dans ce dossier.
Il faudra ensuite créer des fichiers sources et les faire connaitre à Git. 
La commande "commit" sera utilisé, nous verrons cela un peu plus loin.

Il faut créer un fichier ``README.md`` qui sera un fichier d'information sur le projet.



Cloner un dépôt
---------------

Lorsque nous clonons un dépot, nous récupérons l'historique et le code source d'un projet.
Nous pouvons nous rendre sur des serveurs contenant des dépôt comme `Github <https://github.com>`_
En se rendant sur le site et en se connectant sur un projet, nous pouvons récupérer un lien que nous pourrons utiliser pour cloner ce projet.
Par exemple, nous récupérons le projet domopi sur notre PC:

.. code-block:: bash

	git clone https://github.com/aurelazy/Domopi.git

Git va créer un dossier caché ``.git`` dans le dossier téléchargé, celui-ci comprend l'historique des modifications, et la configuration de Git pour ce projet


Création d'un dépôt servant de serveur
--------------------------------------

Pour un serveur de dépôt, il n'y a besoin que du dossier .git, car les fichiers seront modifiés sur les clients distant et non sur le serveur !
Donc pour la création il suffit de taper:

.. code-block:: bash

	git init --bare

c'est l'option ``--bare`` qui permet de ne créer que le dossier ``.git``.
Pour récupérer le dépot depuis un poste client, il suffit d'utiliser SSH:

.. code-block:: bash

	git clone ssh://utilisateur@serveur/chemin/git




Lier notre dépôt à GitHub
-------------------------

Pour envoyer ensuite notre projet sur Github, rien de plus simple. 
Après création d'un compte, puis d'un dépôt sur GitHub, on lance la commande:

.. code-block:: bash

	git remote add origin https://github.com/<username>/<mon-projet>.git
	git push -u origin master
	


