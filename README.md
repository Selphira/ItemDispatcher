# ItemDispatcher

[![Github Releases](https://img.shields.io/github/v/release/Selphira/ItemDispatcher?include_prereleases&color=blue)](https://github.com/Selphira/ItemDispatcher/releases/latest)
![Langues](https://img.shields.io/static/v1?label=Langues&message=Français&color=limegreen)
![Jeux supportés](https://img.shields.io/static/v1?label=Jeux%20supportés&message=EET&color=dodgerblue)
![GitHub Downloads (all assets, all releases)](https://img.shields.io/github/downloads/Selphira/ItemDispatcher/total)
![GitHub Downloads (all assets, latest release)](https://img.shields.io/github/downloads/Selphira/ItemDispatcher/latest/total)

## Présentation
## Les options
### La quantité d'objets à donner à la cible

C'est la quantité d'objet qui sera donnée à chacune des cibles sélectionnées.  
L'option est surtout utile pour les cas où vous voulez distribuer des objets empilables, comme par exemple les flèches.  

Si l'objet n'est pas empilable ou si la quantité dépasse le nombre par pile, plusieurs objets piles seront alors ajoutées à la cible.  
Si la cible est une créature, et le nombre de piles ne pourra dépasser le nombre d'emplacements libres de la créature.  
Si l'objet est destiné à être équipé par une créature, une seule pile sera générée.

Toute quantité invalide sera automatiquement convertie en une quantité de 1.

#### Exemples de quantités d'objets

| Exemple | Code |
| ------- | ---- |
| 1 objet | - |
| 1 objet | 1 |
| 3 objets | 3 |
| Entre 2 et 6 objets | 2-6 |

### L'objet

Le nom du fichier de l'objet à distribuer, c'est la seule option qui sera obligatoire. Ex: sw1h01.itm, cursed.rnd

L'objet pourra aussi faire référence à un trésor aléatoire qui sera affecté au moment de la création de la créature par le jeu. 
Attention, si l'objet fait partie d'un trésor aléatoire et qu'il doit être équipé, il faudra que l'ensemble des objets de la liste des trésors appartiennent au même emplacement d'équipement (le mod effectuera la vérification).

3 types d'objets sont possibles
- Un objet bien précis  
  Le plus simple, il suffit d'indiquer le nom du fichier. Ex: sw1h01.itm
- Un objet aléatoire  
  Si vous désirez qu'un objet soit distribué aléatoirement lors de l'installation, vous pourrez utiliser une [combinaison](#combinaisons) de fitres.
- Un trésor aléatoire  
  Contrairement à l'objet aléatoire, ce type d'objet sera déterminé aléatoirement par le jeu.  
  Il suffit d'indiquer le nom d'une liste de trésors aléatoire. Ex: sword.rnd

### La quantité de cibles

Par défaut, un seule cible par ligne aura l'objet réparti sur elle.
Pour étendre les possibilités, on peut donc définir la quantité de cibles sur lesquels répartir l'objet. 4 possibilités sont offertes, toutes les cibles, un nombre de cible bien précis, un nombre aléatoire de cibles, un pourcentage de cibles.
Les cibles sont déterminées aléatoirement en fonction des filtres renseignés. Si le nombre de cibles potentielles est plus petit que la quantité désirée, l'objet ne sera distribué qu'au nombre de cibles potentielles. Il ne sera pas distribué en plusieurs exemplaires sur une même cible.

Cette notion de quantité est valable pour toutes les cibles où une part d'aléatoire est présente.  

#### Exemples de quantités de cibles

| Exemple | Code |
| ------- | ---- |
| 1 cible aléatoire | - |
| 1 cible aléatoire | 1 |
| Toutes les cibles | * |
| 2 cibles aléatoires | 2 |
| Entre 2 et 6 cibles aléatoires | 2-6 |
| 20% des cibles potentielles | 20% |

### La cible de l'objet

C'est l'endroit où l'on défini où sera réparti l'objet. 3 types de cibles sont possible
- Une créature
- Un magasin  
  Seul les magasins acceptant le type d'objet à distribuer seront pris en compte
- Un conteneur

Il est possible de déterminer une cible en fonction du nom de son fichier pour sélectionner une cible bien précise, ou à partir d'un groupe ou meta-groupe.

#### Exemples de cibles

| Description de la cible | Exemple | Code |
| ----------------------- | ------- | ---- |
| Une créature spécifique | Sur un squelette | skelet01.cre |
| Une créature aléatoire | Sur une créature aléatoire | ?.cre |
| Une créature aléatoire d'une certaine race | Sur une créature aléatoire de race naine | dwarf.rce |
| Une créature aléatoire d'une certaine classe | Sur une créature aléatoire de classe mage | mage.cls |
| Une créature aléatoire d'une certain kit | Sur une créature aléatoire possédant le kit de Kensai | kensai.kit |
| Une créature aléatoire d'une certain alignement | Sur une créature loyale mauvaise aléatoire | lawful_evil.alg |
| Une créature aléatoire d'un certain type (humanoïde, animal, mort-vivant, etc.) | Sur une créature aléatoire de type mort-vivant | undead.gen |
| Une créature aléatoire d'un certain genre | Sur une créature aléatoire du genre féminin | female.gnd |
| Une créature aléatoire de niveau 3 | Sur une créature aléatoire de niveau 3 | 3.lvl |
| Une créature aléatoire de niveau 3 et plus | Sur une créature aléatoire de niveau 3 et plus | 3+.lvl |
| Une créature aléatoire de niveau 3 et moins | Sur une créature aléatoire de niveau 3 et moins | 3-.lvl |
| Une créature aléatoire de niveau 3 à 6 | Sur une créature aléatoire de niveau 3 à 6 | 3-6.lvl |
| Un magasin spécifique | Dans le magasin de Ribald | ribald3.sto |
| Un magasin aléatoire | Dans un magasin aléatoire | ?.sto |
| Un conteneur aléatoire | Dans un conteneur aléatoire | ?.cnt |
| Un conteneur spécifique (nécessite que l'option "zone" soit défini) | Dans le conteneur numéro 2 de la carte où il se trouve | 2.cnt |
| Un groupe | Sur une créature, un magasin ou un conteneur aléatoire appartenant au groupe | mongroupe.grp |
| Une zone | Sur une créature, un magasin ou un conteneur aléatoire du donjon d'Irenicus | ar0602.are |
 
Tout comme l'objet, vous pourrez utiliser une [combinaison](#combinaisons) de fitres.

### La source de l'objet

Si aucune source n'est spécifiée, le mod se contentera d'ajouter une nouvelle instance de l'objet dans le jeu. Toutefois, ce comportement peut ne pas toujours être souhaité : on peut, par exemple, vouloir limiter l'objet à un seul exemplaire, ou éviter sa prolifération excessive dans le monde. Par ailleurs, certains mods centralisent tous leurs objets dans un magasin unique pour simplifier leur gestion, maximiser la compatibilité ou répondre à d’autres besoins d'organisation. 

Dans ces contextes, la définition d'une source permet de contrôler l’apparition de l’objet. Si une source est spécifiée, l'objet ne sera pas simplement ajouté : il sera retiré de cette source, ce qui garantit qu'il ne sera pas dupliqué.  
Si, au moment de l'ajout, l'objet n’est plus présent à sa source d'origine, le mod ignorera la ligne.

#### Exemples de sources

| Description de la source | Exemple | Code |
| ------------------------ | ------- | ---- |
| Une créature spécifique | Redistribuer l'objet du squelette | skelet01.cre |
| Une créature aléatoire | Redistribuer l'objet d'une créature aléatoire qui le possède | ?.cre |
| Toutes les créatures | Redistribuer l'objet de toutes les créatures qui le possèdent | *.cre |
| Un magasin spécifique | Redistribuer l'objet du magasin de Ribald | ribald3.sto |
| Un magasin aléatoire | Redistribuer l'objet d'un magasin aléatoire qui le possède | ?.sto |
| Tous les magasins | Redistribuer l'objet de tous les magasins qui le possèdent | *.sto |

### Le chapitre

Cette option permet de définir à quel chapitre l'objet pourra apparaitre. Cela pourra aller d'un chapitre fixe, un chapitre minimum et/ou un chapitre maximum.  
Du fait de sa nature, ce genre de répartition passera obligatoirement par un script, qui vérifiera le chapitre en cours pour savoir si l'objet sera présent ou non sur la cible.
Les chapitres iront du 1 au 22, qui correspond à la numérotation des chapitres de EET.

#### Exemples de chapitre

| Exemple | Code |
| ------- | ---- |
| Un objet présent à n'importe quel chapitre | - |
| Un objet présent qu'au chapitre 3 | 3 |
| Un objet présent à partir du chapitre 3 | 3+ |
| Un objet présent jusqu'au chapitre 3 inclus | 3- |
| Un objet présent du chapitre 3 au chapitre 5 inclus | 3-5 |

### La difficulté

Cette option permet de distribuer un objet, uniquement si le joueur est dans une difficulté précise. Vous voulez récompenser les joueurs qui se cassent la tête à vaincre vos monstres en difficulté maximale ? Vous voulez donner un coup de pouce à ceux qui préfèrent se focaliser sur l'histoire en jouant en difficulté minimale ? C'est possible !  
Les valeurs possibles vont de 1 à 5 et correspondent, par défaut, aux niveaux de difficultés suivants :

| Valeur | Difficulté |
| --- | ---- |
| 1 | Facile |
| 2 | Normal |
| 3 | Règle de base |
| 4 | Difficile |
| 5 | Très difficile |

#### Exemples de la difficulté

| Exemple | Code |
| ------- | ---- |
| Dans n'importe quelle difficulté | - |
| Uniquement en difficulté de base | 3 |
| En difficile ou plus | 4+ |
| En normal ou moins | 2- |
| Entre la difficulté normale et difficile | 2-4 |

### Equiper l'objet

Cette option n'est valable que si la cible est une créature, elle indique si l'objet doit être équipé ou simplement ajouté dans son inventaire.    
Attention, si cette option est activée, seules les créatures pouvant porter l'objet seront sélectionnées.  
Aussi, si le slot de la créature est déjà occupé par un objet, le mod s'assurera de remplacer l'objet par un autre de même type.    

| Exemple | Code |
| ------- | ---- |
| Ne sera pas équipé | - |
| Ne sera pas équipé | 0 |
| Sera équipé | 1 |
| L'objet sera aléatoirement équipé ou non | ? |

### Rendre l'objet volable

Cette option indique si l'objet peut être volé ou non si la cible est une créature. Rien de spécial à ajouter ici.

| Exemple | Code |
| ------- | ---- |
| Ne peut pas être volé | - |
| Ne peut pas être volé | 0 |
| Peut être volé | 1 |
| L'objet peut aléatoirement être volé ou non | ? |

### Rendre l'objet droppable

Cette option indique si l'objet peut être looté ou non si la cible est une créature. Rien de spécial à ajouter ici.

| Exemple | Code |
| ------- | ---- |
| Ne peut pas être volé | - |
| Ne peut pas être volé | 0 |
| Peut être volé | 1 |
| L'objet peut aléatoirement être volé ou non | ? |

### La chance de prendre en compte la ligne

Une option qui indique la chance que la ligne soit prise en compte, rien de plus, rien de moins. Elle accepte une valeur allant de 1 à 100.

<a name="combinaisons"></a>
## Les combinaisons

C'est ici qu'on peut commencer à vraiment s'amuser, il est possible de combiner la plupart des notations de cible. Pour se faire, il suffit de les séparer avec le caractère "&". Vous pourrez les noter dans n'importe quel ordre.

Chaque partie se cumule, et les cibles potentielles doivent se trouver dans chacune des parties. C'est une opération AND. L'opération OR est possible par l'utilisation des [groupes](#groupes).  

Que diriez-vous de pouvoir répartir votre objet sur des nains d'alignement mauvais d'une zone précise ?  
Comme il n'est pas possible par défaut de pouvoir filtrer sur n'importe quel type d'alignement mauvais, nous allons créer un groupe `evils.grp` qui listera l'ensemble des créatures d'alignements mauvais. Le fichier contiendra le texte suivant

```
lawful_evil.alg
neutral_evil.alg
chaotic_evil.alg
```

La définition de la cible se traduira par ce bout de code `dwarf.rce&male.gnd&evils.grp&ar0602.are`  

Si nous décomposons, nous obtenons
- dwarf.rce : Les créatures de race naine
- male.gnd : De genre masculin
- evils.grp : D'alignement mauvais
- ar0602.are : Dans le donjon d'Irenicus

<a name="groupes"></a>
## Les groupes
## Les meta-groupes

Les meta-groupes sont des groupes automatiquement générés à partir des données du jeu. De fait, ils s'adaptent automatiquement aux ajouts des mods.  
Ils s'utilisent comme des groupes classiques, mis à part que l'extension change afin de cibler le meta-groupe désiré.  
L'extension défini le meta-groupe à utiliser, tandis que le nom défini la valeur ciblée.  
Le nom est celui présent dans le fichier .ids correspondant, en minuscule. Les espaces sont remplacés par des _.

### Les meta-groupes basés sur un fichier .ids

| Type | Meta-groupe | Fichier .ids | Extension | Exemple |
| ---- | ----------- | ------------ | --------- | ------- |
| Créature | La race de la créature | race.ids | rce | human.rce |
| Créature | La classe de la créature | class.ids | cls | mage.cls |
| Créature | Le kit de la créature | kit.ids | kit | mage.kit |
| Créature | Le genre de la créature | gender.ids | gnd | female.gnd |
| Créature | L'alignement de la créature | alignmen.ids | alg | lawful_evil.alg |
| Créature | La donnée générale de la créature | general.ids | gen | undead.gen |
| Créature | La donnée spécifique de la créature | specific.ids | spc | magic.spc |
| Objet | La catégorie de l'objet | itemcat.ids | cat | amulet.cat |

### Les meta-groupes basés sur d'autres données

| Type | Meta-groupe | Extension | Exemple |
| ---- | ----------- | --------- | ------- |
| Créature | Le niveau de la créature | lvl | 2.lvl |
| Objet | Le niveau d'echantement de l'objet | ilv | 4+.ilv |
| Objet | Les objets maudits | mgr | cursed.mgr |
| Objet | Les armes à 2 mains | mgr | two_handed.mgr |
| Objet | Les objets magiques | mgr | magical.mgr |
| Objet | Les robes | arm | robe.arm |
| Objet | Les armures de cuir | arm | leather.arm |
| Objet | Les armures de mailles | arm | chainmail.arm |
| Objet | Les armures de plates | arm | platemail.arm |
| Objet | Les targes | arm | buckler.arm |
| Objet | Les petits boucliers | arm | small_shield.arm |
| Objet | Les boucliers moyens | arm | medium_shield.arm |
| Objet | Les grands boucliers | arm | large_shield.arm |

Le nom du groupe correspondant au niveau de la créature et au niveau d'enchantement de l'objet supportent une notation complexe permettant d'affiner le filtrage.

| Exemple | Nom du groupe |
| ------- | ------------- |
| Les créatues/objets de niveau 3 | 3 |
| Les créatues/objets de niveau 3 et plus | 3+ |
| Les créatues/objets de niveau 3 et moins | 3- |
| Les créatues/objets entre le niveau 3 et le niveau 5 inclus | 3-5 |

## Les trésors aléatoires
## Comment un autre mod peut venir se greffer à la répartition ?
## Quelques règles générales
