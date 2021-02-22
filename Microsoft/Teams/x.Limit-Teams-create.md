# Customiser Teams 
## Comment réduire les droits de création des équipes, pas à tout le monde par défaut
Chez Microsoft, ce n'était visiblement pas prévu, donc ce n'est pas dans un simple "settings". Même dans le module "fait pour" l'éducation, avec l'application d'une "policy" pour les écoles avec mineurs (secondaire), par défaut, les élèves peuvent créer des équipes et canaux invisibles à volonté...
* C'est beau la liberté... Mais est-ce le bon endroit pour ? Moi perso, cela pourrait m'aller. Sauf que cela va créer des groupes avec des noms "libres" (Minecraft, totor...) et générer un "cheni" pas possible pour les admins, en plus de questionner la responsbilité de l'établissement ou l'état responsable du "tenant" avec ces groupes "libres" et hors contrôle (*Mais bon, il suffit de réutiliser les mêmes règles de décharges que les fournisseurs, sauf que whatsapp, c'est interdit aux moins de 16 ans sans autorisation parentale*)
* Il y a bien une stratégie proposée par Microsoft: https://docs.microsoft.com/fr-ch/MicrosoftTeams/easy-policy-setup-edu?tabs=students%2Cstudent-settings
  * Mais même en prenant l'option "Primary or Secondary", les étudiants peuvent librement créer des groupes et canaux, y compris privés.
  * https://docs.microsoft.com/fr-ch/MicrosoftTeams/easy-policy-setup-edu?tabs=students%2Cstudent-settings#policy-areas
* Compte-tenu de nos habitudes, on a envie de mieux contrôler cela: Il faut faire la customisation suivante:

### Création d'un groupe autorisé
Première étape, créer un groupe de sécurité, avec ou sans email (bonne idée de pouvoir leur envoyer un message)
1. http://admin.microsoft.com (avec les droits pour créer des groupes)
2. **Groupes:** https://admin.microsoft.com/Adminportal/Home?source=applauncher#/groups
3. **Groupes actifs**
4. **Ajouter un groupe**
5. **Choisir un type de groupe**: Sécurité ("à extension messagerie" en option, cela veut dire un email pour faire liste de distribution) ou 365
* Si tu fais un groupe Office 365, ces derniers ne peuvent pas être imbriqués (et j'ai pas testé si cela fonctionne pour mettre des droits, cela devrait)
  * Si tu fais un groupe 365, tu peux affecter des propriétaires qui gèrent ce groupe
  * Si tu choisis 365, tu pourras aussi lui créér une équipe Teams associée.
* Si tu veux affecter le droit à plusieurs groupes de sécurité alors tu pourras les inclure dans le groupe autorisé.
  * **NESTING LIMITATION**
  * **Attention**: Avec Microsoft Azure/365, tu dois faire des groupes sécurité avec alias emails si tu veux l'imbriquer dans un groupe de même.
  * Oui chez Microsoft, non seulement tu ne peux pas imbriquer des groupes 365, mais pas des groupes avec alias dans un groupe sans, et(ou) inversement...
6. 

### Customisation du script joint
C'est tellement imprévu par Microsoft, qu'il faut modifier les droits avec un script qui semble faire 1 boucle sur plusieurs groupes (Si qq'1 sait lire du PS, je suis preneur d'explications, car trouvé la recette mais sans le décodage).
* Gérer les personnes qui peuvent créer des groupes Microsoft 365 | Microsoft Docs

## Normaliser les noms de Groupes (équipes)
Cela peut être un poil pénible, si tu crées une équipe, tu as envie de prendre un nom sympa et compréhensible, mais pour qui? Dans Teams c'est le nom des projets et des équipes, pour l'IT, cela va générer des groupes dans la base et on aimerait des noms de groupes qui facilitent leur tri et identification. Pour cela, on fait des conventions de nommage.
* https://github.com/CloudReady-ch/ISEIG-LAB/blob/9c2f529ac2e4b390c6e885940c57a75f881fab4a/AZURE/BestPratiq_Naming.md

On peut aussi imposer des règles de nommages, dans 365.
* TK

Mais faudrait-il le faire? Ou laisser la liberté de nommer les équipes, selon leur sens?
