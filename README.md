# ItemDispatcher

[![Github Releases](https://img.shields.io/github/v/release/Selphira/ItemDispatcher?include_prereleases&color=blue)](https://github.com/Selphira/ItemDispatcher/releases/latest)
![Langues](https://img.shields.io/static/v1?label=Langues&message=Français&color=limegreen)
![Jeux supportés](https://img.shields.io/static/v1?label=Jeux%20supportés&message=EET&color=dodgerblue)
![GitHub Downloads (all assets, all releases)](https://img.shields.io/github/downloads/Selphira/ItemDispatcher/total)
![GitHub Downloads (all assets, latest release)](https://img.shields.io/github/downloads/Selphira/ItemDispatcher/latest/total)

## Présentation

ItemDispatcher est un mod pour Baldur's Gate 2 conçu pour permettre la distribution d'objets de manière flexible et personnalisée. Grâce à ce mod, vous pouvez spécifier des cibles, des types d'objets et des conditions précises pour la distribution, assurant un gameplay dynamique et adapté à vos besoins.

## Options de distribution
### Quantité d'objets distribués

Cette option détermine le nombre d'objets attribués à chaque cible sélectionnée. Elle est particulièrement utile pour distribuer des objets empilables, tels que des flèches.

- Si l'objet n'est pas empilable ou si la quantité dépasse la capacité d'une pile, plusieurs piles seront ajoutées à la cible.
- Si la cible est une créature, le nombre de piles ne peut excéder le nombre d'emplacements libres.
- Si l'objet doit être équipé par une créature, une seule pile sera générée.
- Toute quantité invalide est convertie automatiquement en une quantité de 1.

#### Exemples

| Exemple | Code |
| ------- | ---- |
| 1 objet | `-` ou `1` |
| 3 objets | `3` |
| Entre 2 et 6 objets | `2-6` |

### Objet à distribuer

L'objet à distribuer est la seule option obligatoire pour chaque distribution.  
Il est possible d'utiliser un objet aléatoire distribué lors de l'installation ou un trésor généré aléaoirement au moment de la création d'une créature par le jeu.

#### Types d'objets :

- **Objet précis** : Indiquez simplement le nom du fichier (ex. `sw1h01.itm`).
- **Objet aléatoire** : Utilisez une combinaison de filtres (voir section [combinaisons](#combinaisons)).
- **Trésor aléatoire** : Mentionnez le nom de la liste de trésors (ex. `sword.rnd`).

### Quantité de cibles

Par défaut, un seul objet est distribué par cible. Il est possible de spécifier le nombre de cibles sur lesquelles l'objet sera réparti, incluant des options comme : toutes les cibles, un nombre précis, un nombre aléatoire ou un pourcentage de cibles.

Si le nombre de cibles disponibles est inférieur à celui souhaité, l'objet ne sera distribué que sur les cibles disponibles.  

#### Exemples de quantités de cibles

| Exemple | Code |
| ------- | ---- |
| 1 cible aléatoire |  `-` ou `1` |
| Toutes les cibles | `*` |
| 2 cibles aléatoires | `2` |
| Entre 2 et 6 cibles aléatoires | `2-6` |
| 20% des cibles potentielles | `20%` |

### Cible de l'objet

La cible désigne l'endroit où l'objet sera distribué. Les types de cibles possibles incluent :

- **Créature**
- **Magasin** : Seuls les magasins acceptant le type d'objet seront pris en compte.
- **Conteneur**

Si aucune cible n'est spécifiée, elle sera choisie aléatoirement parmi l'ensemble des créatures disponibles.

Vous pouvez cibler spécifiquement en utilisant le nom de fichier ou sélectionner des cibles à partir de groupes ou de meta-groupes.

#### Exemples de cibles

| Description de la cible | Exemple | Code |
| ----------------------- | ------- | ---- |
| Une créature spécifique | Sur un squelette | `skelet01.cre` |
| Une créature aléatoire | Sur une créature aléatoire | `?.cre` |
| Une créature aléatoire d'une certaine race | Sur un nain | `dwarf.rce` |
| Une créature aléatoire d'une certaine classe | Sur un mage | `mage.cls` |
| Une créature aléatoire d'une certain kit | Sur un Kensai | `kensai.kit` |
| Une créature aléatoire d'une certain alignement | Sur une créature loyale mauvaise | `lawful_evil.alg` |
| Une créature aléatoire d'un certain type (humanoïde, animal, mort-vivant, etc.) | Sur un mort-vivant | `undead.gen` |
| Une créature aléatoire d'un certain genre | Sur une créature féminine | `female.gnd` |
| Une créature aléatoire de niveau 3 | Sur une créature de niveau 3	| `3.lvl` |
| Une créature aléatoire de niveau 3 et plus | Sur une créature de niveau 3 et plus | `3+.lvl` |
| Une créature aléatoire de niveau 3 et moins | Sur une créature de niveau 3 et moins | `3-.lvl` |
| Une créature aléatoire de niveau 3 à 6 | Sur une créature de niveau 3 à 6 | `3-6.lvl` |
| Un magasin spécifique | Dans le magasin de Ribald | `ribald3.sto` |
| Un magasin aléatoire | Dans un magasin aléatoire | `?.sto` |
| Un conteneur aléatoire | Dans un conteneur aléatoire | `?.cnt` |
| Un conteneur spécifique (nécessite que l'option "zone" soit défini) | Dans le conteneur n°2 de la carte | `2.cnt` |
| Un groupe | Sur une créature, un magasin ou un conteneur aléatoire appartenant au groupe | `mongroupe.grp` |
| Une zone | Sur une créature, un magasin ou un conteneur aléatoire du donjon d'Irenicus | `ar0602.are` |
 
Tout comme pour les objets, vous pouvez utiliser une [combinaison](#combinaisons) de filtres pour spécifier plusieurs critères de sélection.

### Source de l'objet

Si aucune source n'est spécifiée, l'objet est simplement ajouté au jeu. Pour éviter la duplication d'objets ou contrôler leur rareté, vous pouvez définir une source d'où l'objet sera prélevé.  
Si au moment de traiter la ligne, l'objet n’est pas présent à sa source, elle sera ignorée.

#### Exemples de sources

| Description de la source | Exemple | Code |
| ------------------------ | ------- | ---- |
| Une créature spécifique | Redistribuer depuis le squelette | `skelet01.cre` |
| Une créature aléatoire | Redistribuer depuis  une créature aléatoire qui le possède | `?.cre` |
| Toutes les créatures | Redistribuer depuis toutes les créatures qui le possèdent | `*.cre` |
| Un magasin spécifique | Redistribuer depuis le magasin de Ribald | `ribald3.sto` |
| Un magasin aléatoire | Redistribuer depuis un magasin aléatoire qui le possède | `?.sto` |
| Tous les magasins | Redistribuer depuis tous les magasins qui le possèdent | `*.sto` |

### Chapitre d'apparition

Cette option permet de spécifier à partir de quel chapitre l'objet peut apparaître, en fixant un chapitre précis ou une plage de chapitres (de 1 à 22, correspondant à la numérotation d'EET).  
L'apparition est régie par un script vérifiant le chapitre en cours.

#### Exemples de chapitre

| Exemple | Code |
| ------- | ---- |
| Disponible dans n'importe quel chapitre | `-` |
| Présent uniquement au chapitre 3 | `3` |
| Présent à partir du chapitre 3 | `3+` |
| Présent jusqu'au chapitre 3 inclus | `3-` |
| Présent du chapitre 3 au chapitre 5 inclus | `3-5` |

### Difficulté requise

Vous pouvez choisir de distribuer un objet selon le niveau de difficulté du jeu (valeurs de 1 à 5).

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
| N'importe quelle difficulté | `-` |
| Uniquement en difficulté de base | `3` |
| En difficile ou plus | `4+` |
| En normal ou moins | `2-` |
| Entre normal et difficile | `2-4` |

### Équipement de l'objet
    
Cette option, applicable uniquement si la cible est une créature, détermine si l'objet doit être équipé ou simplement ajouté à l'inventaire.

- **Sélection de la créature** : Si l'option est activée, seules les créatures pouvant porter l'objet seront sélectionnées.
- **Gestion des emplacements** : Si l'emplacement où l'objet doit être équipé est déjà occupé, le mod remplacera l'objet existant par celui à distribuer, à condition qu'il soit du même type. Cette vérification garantit que la créature sera apte à l'utiliser.
- **Remplacement** : Si l'objet ne peut pas être équipé dans le slot prévu (par exemple, une arme à deux mains ne pouvant pas être équipée par une créature portant déjà un bouclier), la distribution de l'objet ne sera pas réalisée sur cette créature.

| Exemple | Code |
| ------- | ---- |
| L'objet ne sera pas équipé | `-` ou `0` |
| L'objet sera équipé | `1` |
| L'objet sera équipé aléatoirement | `?` |

### Rendre l'objet volable

Cette option détermine si l'objet peut être volé par le joueur lorsqu'il est détenu par une créature.

| Exemple | Code |
| ------- | ---- |
| L'objet ne peut pas être volé | `-` ou `0` |
| L'objet peut être volé | `1` |
| L'objet peut aléatoirement être volé ou non | `?` |

### Rendre l'objet droppable

Cette option indique si l'objet peut être ramassé (looté) après que la créature ait été vaincue.

| Exemple | Code |
| ------- | ---- |
| L'objet ne peut pas être ramassé | `-` ou `0` |
| L'objet peut être ramassé | `1` |
| L'objet peut aléatoirement être ramassé ou non | `?` |

### Chance de prise en compte de la ligne

Cette option définit la probabilité, en pourcentage, que la ligne soit prise en compte pour la distribution de l'objet. Elle accepte une valeur de 1 à 100.

#### Exemple
Si la valeur est définie à 50, il y a 50 % de chances que l'objet soit distribué selon les critères de la ligne.

<a name="combinaisons"></a>
## Les combinaisons

L'une des fonctionnalités avancées du mod est la capacité de combiner des critères pour cibler des entités de manière plus précise. Pour cela, les critères peuvent être séparés par le symbole `&`, ce qui permet de cumuler plusieurs conditions (opération AND). Pour un filtrage OR, il est nécessaire d'utiliser des [groupes](#groupes).

Exemple : Si vous souhaitez distribuer un objet à des nains d'alignement mauvais dans une zone spécifique, vous pouvez créer un groupe `evils.grp` qui répertorie les alignements mauvais :

```
lawful_evil.alg
neutral_evil.alg
chaotic_evil.alg
```

La définition de la cible serait alors : `dwarf.rce&male.gnd&evils.grp&ar0602.are`  

- **dwarf.rce** : Les créatures de race naine
- **male.gnd** : De genre masculin
- **evils.grp** : D'alignement mauvais
- **ar0602.are** : Dans le donjon d'Irenicus

<a name="groupes"></a>
## Les groupes

Les groupes permettent de regrouper plusieurs entités sous une seule référence, facilitant ainsi la sélection des cibles. Un fichier `.grp` contient les entités à inclure, chacune sur une ligne distincte.

## Les meta-groupes

Les meta-groupes sont des ensembles dynamiques générés automatiquement à partir des données du jeu et s'adaptent aux ajouts d'autres mods. Ils fonctionnent comme des groupes classiques, avec une extension spécifique pour cibler le meta-groupe souhaité.

### Précisions sur l'utilisation

- **Extension et valeur ciblée** : L'extension indique le type de meta-groupe utilisé, tandis que le nom spécifie la valeur ciblée. Par exemple, pour cibler une créature de race humaine, le nom serait human et l'extension .rce (`human.rce`).
- **Fichiers .ids** : Le nom du groupe doit correspondre à une entrée dans le fichier `.ids` pertinent, en respectant la casse (utilisation de **minuscules**). Ces fichiers définissent les différentes valeurs possibles pour un type de donnée (race, classe, etc.).
- **Gestion des espaces** : Les espaces présents dans les noms d'entrée des fichiers `.ids` doivent être remplacés par des underscores (`_`). Par exemple, pour une valeur comme "High Elf", le nom de groupe serait `high_elf.rce`.

### Les meta-groupes basés sur un fichier .ids

| Type | Meta-groupe | Fichier .ids | Extension | Exemple |
| ---- | ----------- | ------------ | --------- | ------- |
| Créature | Race de la créature | race.ids | rce | `human.rce` |
| Créature | Classe de la créature | class.ids | cls | `mage.cls` |
| Créature | Kit de la créature | kit.ids | kit | `mage.kit` |
| Créature | Genre de la créature | gender.ids | gnd | `female.gnd` |
| Créature | Alignement de la créature | alignmen.ids | alg | `lawful_evil.alg` |
| Créature | Donnée générale de la créature | general.ids | gen | `undead.gen` |
| Créature | Donnée spécifique de la créature | specific.ids | spc | `magic.spc` |
| Objet | Catégorie de l'objet | itemcat.ids | cat | `amulet.cat` |

### Les meta-groupes basés sur d'autres données

| Type | Meta-groupe | Extension | Exemple |
| ---- | ----------- | --------- | ------- |
| Créature | Niveau de la créature | lvl | `2.lvl` |
| Objet | Niveau d'echantement de l'objet | ilv | `4+.ilv` |
| Objet | Objets maudits | mgr | `cursed.mgr` |
| Objet | Armes à deux mains | mgr | `two_handed.mgr` |
| Objet | Objets magiques | mgr | `magical.mgr` |
| Objet | Robes | arm | `robe.arm` |
| Objet | Armures de cuir | arm | `leather.arm` |
| Objet | Armures de mailles | arm | `chainmail.arm` |
| Objet | Armures de plates | arm | `platemail.arm` |
| Objet | Targes | arm | `buckler.arm` |
| Objet | Petits boucliers | arm | `small_shield.arm` |
| Objet | Boucliers moyens | arm | `medium_shield.arm` |
| Objet | Grands boucliers | arm | `large_shield.arm` |

#### Détails sur le niveau de la créature et le niveau d'enchantement de l'objet

Les meta-groupes relatifs au niveau de la créature et au niveau d'enchantement de l'objet prennent en charge des notations complexes pour un filtrage précis. Ces notations permettent de spécifier des seuils et des plages de valeurs.

| Exemple | Nom du groupe |
| ------- | ------------- |
| Les créatues/objets de niveau 3 | `3` |
| Les créatues/objets de niveau 3 et plus | `3+` |
| Les créatues/objets de niveau 3 et moins | `3-` |
| Les créatues/objets entre le niveau 3 et le niveau 5 inclus | `3-5` |

## Les trésors aléatoires

Vous pouvez référencer des listes de trésors aléatoires qui seront attribuées par le jeu. Utilisez cette fonctionnalité pour enrichir la diversité des objets obtenus par les créatures ou les conteneurs.

## Comment un autre mod peut venir se greffer à la répartition ?
## Quelques règles générales
