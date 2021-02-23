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
6. Nommer et documenter ce groupe
7. Y ajouter les personnes autorisées: **Membres": Afficher tout et gérer les membres.
  * **Attention**: Si c'est un groupe 365, et qu'un propriétaire doit aussi en disposer des droits, il faut en plus de le mettre propriétaire, il faut le mettre membre.
8. Exécuter le script ci-après.

### Customisation du script joint
C'est tellement imprévu par Microsoft, qu'il faut modifier les droits avec un script qui semble faire 1 boucle sur plusieurs groupes (Si qq'1 sait lire du PS, je suis preneur d'explications, car trouvé la recette mais sans le décodage).
* [Gérer les personnes qui peuvent créer des groupes Microsoft 365 | Microsoft Docs](https://docs.microsoft.com/fr-fr/microsoft-365/solutions/manage-creation-of-groups?view=o365-worldwide)
1. Copier ce scipt: https://github.com/CloudReady-ch/QuickLearn/blob/master/Microsoft/Teams/Groups-Creators.ps1
2. Modifier pour remplacer "it-groups-creators" avec le nom effectivement utilisé pour autoriser la création d'une équipe.
3. Exécuter le script dans un fenêtre "Powershell ISE" (Nécessite de s'identifier avec un compte Microsoft 365 autorisé pendant l'exécution)

## Normaliser les noms de Groupes (équipes)
Cela peut être un poil pénible, si tu crées une équipe, tu as envie de prendre un nom sympa et compréhensible, mais pour qui? Dans Teams c'est le nom des projets et des équipes, pour l'IT, cela va générer des groupes dans la base et on aimerait des noms de groupes qui facilitent leur tri et identification. Pour cela, on fait des conventions de nommage.
* https://github.com/CloudReady-ch/ISEIG-LAB/blob/9c2f529ac2e4b390c6e885940c57a75f881fab4a/AZURE/BestPratiq_Naming.md

On peut aussi imposer des règles de nommages, dans 365.
* TK

Mais faudrait-il le faire? Ou laisser la liberté de nommer les équipes, selon leur sens? 
* Limiter les droits de création à une partie de l'équipe, 
* et les réunir pour prendre un moment pour un briefing sur la façon de nommer les groupes, 
* et des bases de la communication explicite et univoque.

## Autoriser les invités
* Ouvrir la console admin Teams: https://admin.teams.microsoft.com/company-wide-settings/guest-configuration
  * Paramètres échelle organisation - Accès invité: Par défaut c'est activé, à la base.
  * On peut bloquer quelques options pour les appels, les vidéos, la messagerie.
* Autres infos
  * https://docs.microsoft.com/fr-fr/microsoftteams/guest-access
  * Vérifier aussi dans Azure: https://docs.microsoft.com/fr-fr/microsoft-365/solutions/collaborate-as-team?view=o365-worldwide
    * External collaboration settings (Azure Active Directory)

## Limiter les domaines externes
Par défaut c'est tout ouvert, mais on peut gérer une liste "blanche" de domaines autorisés, ou une liste "noire" des domaines interdits.
* Attention: Dès qu'un domaine est "autorisé", alors cela devient une liste blanche et tous les autres domaines sont bloqués, explicités ou pas. Il faut alors autoriser les domaines un par un.
* Cf. console admin: https://admin.teams.microsoft.com/company-wide-settings/external-communications
  * https://docs.microsoft.com/fr-fr/microsoftteams/manage-external-access#let-your-teams-users-chat-and-communicate-with-users-in-another-organization
