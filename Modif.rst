Modification de notre code et sauvegarde
========================================

Dans ce chapitre, nous allons voir les différentes commandes utiles à la modification de nos fichiers de code ainsi que la sauvegarde de ceux-ci, ``commit``.

Voir le status de notre *code*
-------------------------------


Pour voir les fichiers modifiés:

.. code-block:: bash

	git status

Méthode de travail:

	#. Modifier le code
	#. Tester le programme pour vérifier s'il fonctionne
	#. Faire un commit pour "enregistrer" les changements et les faire connaitre à Git;
	#. Recommencer à partir de l'étape 1

Si l'on change un code dans un fichier, ex:``status``, et que l'on refait un:

.. code-block:: bash

	git status
	
nous voyons que le retour n'est pas le même, nous avons, entre autre, la ligne suivante:

.. code-block:: bash

	modifié:          status
	aucune modification n'a été ajoutée à la validation (utilisez "git add" ou "git commit -a")

Pour voir les changements fait dans le fichier:

.. code-block:: bash

	git diff

Les lignes ajoutées sont précédées d'un ``+``, les lignes supprimées d'un ``-``.
Si plusieurs fichiers avaient été modifiés, nous aurions vu la totalité des fichiers, par contre si nous ne voulions voir les modifications que d'un seul fichier, nous pouvions faire:

.. code-block:: bash

	git diff status # Où status est le nom du fichier


Sauvegarder notre *code*
------------------------

Lorsque nous modifions un fichier de notre code, il faut dire à *Git* de prendre les nouveaux changements dans celui-ci.
Cette sauvegarde s'appelle un *commit*.

Lors de la commande:

.. code-block:: bash

	git status

nous avons vu que le fichier modifié était en rouge, ce qui veut dire que lors du commit il ne sera pas pris en compte.
Il faudra lui préciser le nom lors du commit, il y a 3 possibilités:

	#. ``git add fichier1 fichier2`` # pour ajouter les fichier au commit puis 
	   ``git commit``
	#. ``git commit -a`` # pour tout commiter
	#. ``git commit fichier1 fichier2``

Lorsque la commande *commit* est lancé, un éditeur de texte s'ouvre. Cela permet d'insérer un texte pour décrire le changement.
Ce texte doit être court, par défaut, chaque commit ne devrait faire l'objet que d'un seul changement dans le code.
Pour changer l'éditeur par défaut de git il suffit de faire:

.. code-block:: bash

	git config --global core.editor "vim"

Le *commit* enregistre les changements dans sont historique local, si nous voulons que ces changements soient pris en compte par pour tout le monde, il faudra envoyer ces changements sur le serveur.

Annuler un commit
-----------------

Il peut arriver que nous ayons besoin d'annuler un commit que nous avons fait.
Pour cela, nous avons la possibilité de vérifier tous les commits fait sur un projet:

.. code-block:: bash

	git log

Avec cette commande, on peut voir tous les commits que nous avons effectué sur ce projet.

Pour voir également les changements faits, on peut lancer la commande avec l'option ``-p``:

.. code-block:: bash

	git log -p

On peut également avoir les changements effectué lors d'un commit mais plus court, en lançant la commande suivante:

.. code-block:: bash

	git log --stat

Nous allons voir maintenant les commandes pour annuler un commit ou un message de commit.

Si nous devons changer le message du dernier commit, il suffit de faire:

.. code-block:: bash

	git commit --amend

On reviens sur l'éditeur de texte.
On ne peut pas modifier un message déjà envoyé.
Pour annuler un commit de manière soft, voici plusieurs commandes possibles:

.. code-block:: bash

	git reset HEAD

On peut également utiliser plusieurs notations:

	* HEAD: dernier commit
	* HEAD^: avant dernier commit
	* HEAD^^: avant-avant dernier commit
	* HEAD~2: pareil
	* d6d98923868578a7f38dea79833b56d0326fcba1: le numéro de commit.

Le commit sera retiré, par contre, les fichiers restent modifiés.
Pour annuler un commit de manière hard, qui annulera le dernier commit ainsi que les changements du fichier.

.. code-block:: bash

	git reset --hard HEAD^

Pour annuler les changements sur un fichier avant un commit il suffit d'envoyer:

.. code-block:: bash

	git checkout

Ceci va également restaurer le fichier.


Annuler/Supprimer un fichier avant un commit
---------------------------------------------

Supposons que vous veniez d’ajouter un fichier à Git avec git add et que vous vous apprêtiez à le *commiter*. Cependant, vous vous rendez compte que ce fichier est une mauvaise idée et vous voudriez annuler votre ``git add``.
Il est possible de retirer un fichier qui avait été ajouté pour être *commité* en procédant comme suit :

.. code-block:: bash


	git reset HEAD -- fichier_a_supprimer
