# Politique de sécurité

Agenteca installe du texte que des modèles vont exécuter, parfois avec des hooks et des serveurs MCP qui lancent des programmes. Les failles y sont prises au sérieux.

## Signaler une faille

**Ne publiez pas de faille dans un ticket public.**

Utilisez le signalement privé de GitHub : dans le dépôt concerné, onglet **Security**, puis **Report a vulnerability**.

Si ce signalement privé n'est pas disponible sur le dépôt, écrivez à <agenteca@proton.me>, sans détail public de la faille dans l'objet du message.

Indiquez le dépôt et la version, les étapes pour reproduire, et l'effet (ce qu'un attaquant obtient).

## Ce qui nous intéresse en priorité

- Un paquet qui fait écrire un fichier hors du projet, ou à travers un lien symbolique.
- Un paquet dont du code s'exécute pendant l'installation.
- Un contenu malveillant que le scan laisse passer alors qu'une règle devrait l'arrêter (texte invisible, commande téléchargée puis exécutée).
- Un moyen, pour un modèle pilotant le serveur MCP ou un plugin, d'installer sans que le plan soit montré, ou de contourner un scan bloquant.
- Un fichier modifié à la main écrasé ou supprimé sans accord.
- Sur le serveur : lecture d'un catalogue privé sans y être membre, élévation de rôle, fuite de jeton.

## Ce que le scan ne garantit pas

Le scan repère des pièges connus. Il ne prouve pas qu'un paquet est sûr : un texte parfaitement lisible peut demander à un agent une action nuisible. Un tel paquet n'est pas une faille d'Agenteca ; signalez-le au mainteneur du catalogue qui le liste.

## Versions suivies

Le projet est en 0.x : seule la dernière version publiée de chaque dépôt reçoit des correctifs.
