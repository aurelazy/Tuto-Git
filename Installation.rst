Installation
==============

Pour installer git sur une Debian, il suffit de taper la commande:

.. code-block:: bash

   apt-get install git-core gitk


A quoi correspond ces 2 paquets:
	* git-core: c'est git
	* gitk: une interface graphique qui aide à visualiser les logs. Facultatif.

Pour activer la couleur, à ne faire qu'une seule fois:

.. code-block:: bash

   git config --global color.diff auto 
   git config --global color.status auto 
   git config --global color.branch auto

Pour configurer le nom:

.. code-block:: bash

	git config --global user.name "aurelazy"

Pour configurer le mail:

.. code-block:: bash

	git config --global user.email mon@ema.il

On peut vérifier toutes ces infos en éditant le fichier ``~/.gitconfig``.

On peut créer des alias pour les commandes, dans le fichier ``.gitconfig``:

.. code-block:: yaml

	[alias]
		ci = commit
		co = checkout
		st = status
		br = branch

Donc au lieu d'écrire:

.. code-block:: bash

	git commit

On peut écrire:

.. code-block:: bash

	git ci
