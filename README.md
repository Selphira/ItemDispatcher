# ItemDispatcher

[![Github Releases](https://img.shields.io/github/v/release/Selphira/ItemDispatcher?include_prereleases&color=blue)](https://github.com/Selphira/ItemDispatcher/releases/latest)
![Langues](https://img.shields.io/static/v1?label=Langues&message=Français&color=limegreen)
![Jeux supportés](https://img.shields.io/static/v1?label=Jeux%20supportés&message=EET&color=dodgerblue)
![GitHub Downloads (all assets, all releases)](https://img.shields.io/github/downloads/Selphira/ItemDispatcher/total)
![GitHub Downloads (all assets, latest release)](https://img.shields.io/github/downloads/Selphira/ItemDispatcher/latest/total)

## Présentation

ItemDispatcher est un mod pour Baldur's Gate 2 conçu pour permettre la distribution d'objets de manière flexible et personnalisée. Grâce à ce mod, vous pouvez spécifier des cibles, des types d'objets et des conditions précises pour la distribution, assurant un gameplay dynamique et adapté à vos besoins.

## Options de distribution

### Quantité d'objets à sélectionner

Cette option détermine combien d'objets différents seront choisis aléatoirement parmi les objets éligibles définis par le filtre.

- Cette option s'applique uniquement lorsque les objets à distribuer sont déterminés de manière aléatoire.
- Si cette option n'est pas spécifiée, un seul objet sera sélectionné par défaut.
- Les objets sélectionnés sont ensuite distribués selon les paramètres définis, tels que la **quantité par cible**, les **piles** et les **cibles**.

#### Exemples

| Exemple | Code |
| ------- | ---- |
| 1 objet aléatoire | `-` ou `1` |
| 3 objets aléatoires | `3` |
| Entre 2 et 5 objets aléatoires | `2-5` |
| Tous les objets éligibles | `*` |
| 1 objet différent par cible potentielle | `#` |

### Quantité de piles distribuées par cible

Cette option permet de définir combien de **piles** d’un objet seront distribuées à chaque cible sélectionnée.  

- Une pile représente un ensemble d’unités empilées, jusqu’à la capacité maximale d’empilement définie par l’objet.  
- Si la cible est une créature qui ne dispose pas d’assez d’emplacements libres dans son inventaire, le nombre de piles sera réduit en fonction de l’espace disponible.
- Dans le cas où la quantité est définie aléatoirement (par exemple, `2-6` pour une quantité comprise entre 2 et 6 piles), la valeur aléatoire sera recalculée pour chaque cible sélectionnée. Cela permet une distribution dynamique et variée des objets. 

**Détails supplémentaires**  

1. Les objets non empilables sont également pris en charge : chaque pile correspondra à un exemplaire unique de l’objet.  
2. En combinaison avec l’option **Quantité maximale par pile**, cette règle permet de distribuer efficacement des objets tout en contrôlant leur empilement et leur quantité globale.  

#### Exemples

| Exemple | Code |
| ------- | ---- |
| 1 objet par cible | `-` ou `1` |
| 3 objets par cible | `3` |
| Entre 2 et 6 objets par cible | `2-6` |

### Quantité maximale par pile

Cette option permet de définir combien d’unités d’un objet peuvent être présentes dans une seule pile lors de la distribution.

- Si aucune valeur n’est définie, la valeur d'empilement maximal spécifiée dans l’objet même sera utilisée.
- Si la **quantité maximale par pile** dépasse la limite d’empilement de l’objet, une seule pile contenant le maximum autorisé par l’objet sera créée.
- Pour créer plusieurs piles, il faudra définir cette intention via la **quantité d’objets distribués par cible**.
- Dans le cas où la quantité est définie aléatoirement (par exemple, `2-6` pour une quantité comprise entre 2 et 6 unités par pile), la valeur aléatoire sera recalculée pour chaque pile générée. Cela garantit une variation entre les piles distribuées.

#### Exemples

| Exemple | Code |
| ------- | ---- |
| L’empilement maximal autorisé par l’objet | `-` |
| Maximum de 10 unités par pile | `10` |
| Entre 5 et 15 unités maximum par pile | `5-15` |

### Objet à distribuer

L'objet à distribuer est la seule option obligatoire pour chaque distribution.  
Il est possible d'utiliser un objet aléatoire distribué lors de l'installation ou un trésor généré aléaoirement au moment de la création d'une créature par le jeu.

#### Types d'objets :

- **Objet précis** : Indiquez simplement le nom du fichier (ex. `sw1h01.itm`).
- **Objet aléatoire** : Utilisez une combinaison de filtres (voir section [combinaisons](#combinaisons)).
- **Trésor aléatoire** : Mentionnez le nom de la liste de trésors (ex. `sword.rnd`).

##### Différences entre la sélection d'un seul objet et de plusieurs objets aléatoires  

Les règles de distribution peuvent être configurées pour sélectionner un seul objet ou plusieurs objets aléatoirement. Chaque approche a ses propres avantages, inconvénients et cas d’usage spécifiques.

###### Sélection d’un seul objet  

**Description** :  
Une seule instance d’un objet, choisi selon les filtres définis, est distribuée.  

**Avantages** :  
- Simplicité : idéal pour des distributions ciblées et directes.  
- Prévisibilité : l’objet sélectionné est unique, ce qui facilite le suivi et l’équilibrage.  
- Efficace pour des objets rares ou uniques qui ne doivent pas apparaître en plusieurs exemplaires.  

**Inconvénients** :  
- Moins de variété dans les objets distribués.  
- Ne convient pas aux scénarios nécessitant plusieurs objets diversifiés.  

**Cas d’usage** :  
- Distribuer une arme spécifique à un boss ou à une créature importante.  
- Ajouter un trésor précis à un coffre clé.  
- Récompenser un joueur avec un objet particulier après une quête.

###### Sélection de plusieurs objets  

**Description** :  
Plusieurs objets sont sélectionnés aléatoirement parmi ceux définis par les filtres et répartis selon les paramètres de distribution.  

**Avantages** :  
- Variété accrue : parfait pour enrichir les inventaires des cibles.  
- Permet de simuler des trésors diversifiés ou des coffres bien remplis.  
- Convient aux scénarios où la diversité est essentielle (par exemple, un coffre contenant des armes, des potions et des gemmes).  

**Inconvénients** :  
- Moins prévisible : difficile à équilibrer si la distribution est entièrement aléatoire.  
- Peut compliquer le suivi des objets distribués, surtout avec des quantités importantes.  

**Cas d’usage** :  
- Répartir plusieurs objets aléatoires sur un groupe d’ennemis (par exemple, un mélange de potions et de flèches).  
- Créer des trésors variés dans des coffres ou des conteneurs.  
- Simuler un butin complexe dans des scénarios où la diversité est clé.  

###### Résumé  

| Critère                     | Sélection d’un seul objet                  | Sélection de plusieurs objets              |
| --------------------------- | ----------------------------------------- | ----------------------------------------- |
| **Simplicité**              | Facile à configurer et à suivre           | Plus complexe à équilibrer et à contrôler |
| **Variété**                 | Limitée                                   | Importante                                |
| **Cas d’usage typiques**    | Objets uniques ou rares                   | Trésors diversifiés ou inventaires riches |
| **Prévisibilité**           | Très prévisible                           | Moins prévisible                          |

Choisissez le type de règle en fonction de vos besoins : une sélection unique pour la précision, ou plusieurs objets pour la variété et la richesse des contenus distribués.

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

La cible désigne l'endroit où l'objet sera distribué. Elle peut être définie de plusieurs manières, selon le niveau de précision souhaité :

1. **Par le nom du fichier** : La méthode la plus simple consiste à spécifier directement le fichier correspondant à la cible (par exemple, `skelet01.cre` pour une créature spécifique ou `ribald3.sto` pour un magasin particulier).
2. **Par une sélection aléatoire ou complexe** : Si aucune cible précise n'est indiquée, des [groupes](groupes), des [meta-groupes](meta-groupes) ou des [combinaisons](#combinaisons) de critères peuvent être utilisés pour définir les cibles.

Les types de cibles possibles incluent :

- **Créature** : L'objet peut être ajouté à l'inventaire ou équipé sur une créature.
- **Magasin** : Seuls les magasins acceptant le type d'objet seront pris en compte.
- **Conteneur** : L'objet sera placé dans un conteneur spécifique ou aléatoire.

**Conditions de sélection pour les créatures**

Lorsqu'une créature est sélectionnée aléatoirement, les conditions suivantes s'appliquent :

- **Si l'objet est destiné à être équipé**, seules les **créatures humanoïdes** avec un emplacement d'équipement libre sont éligibles. Un emplacement est considéré comme libre si aucun objet non droppable n'y est déjà équipé.
- **Si l'objet est une arme ou un bouclier et doit être équipé**, seules les créatures possédant une compétence martiale suffisante pour manier l'objet seront retenues. Cela garantit que les créatures sélectionnées peuvent utiliser l'objet de manière optimale.
- Seules les créatures qui possèdent au moins un emplacement d'inventaire libre sont éligibles à la sélection.

Dans les cas où plusieurs mods ciblent la même créature ou que cette dernière est sélectionnée plusieurs fois pour un objet à équiper sur le même emplacement, une liste de trésors aléatoires sera automatiquement générée et assignée à la créature. L'objet final sera alors déterminé de manière aléatoire pendant la partie.

Si aucune cible n'est spécifiée, elle sera choisie aléatoirement parmi l'ensemble des créatures disponibles.  
Si aucune cible valide (créature, magasin ou conteneur) ne peut être trouvée, la règle de distribution sera ignorée.

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
| Une créature aléatoire possédant une force 12 et plus | Sur une créature possédant une force 12 et plus	| `12+.str` |
| Une créature aléatoire possédant une dextérité de 14 | Sur une créature possédant une dextérité de 14	| `14.dex` |
| Une créature aléatoire possédant une constitution de 16 et moins | Sur une créature possédant une constitution de 16 et moins	| `16-.con` |
| Une créature aléatoire possédant une intelligence entre 12 et 14 | Sur une créature possédant une intelligence entre 12 et 14	| `12-14.int` |
| Une créature aléatoire possédant une sagesse de 15 | Sur une créature possédant une sagesse de 15	| `15.wis` |
| Une créature aléatoire possédant un charsime de 15 | Sur une créature possédant un charsime de 15	| `15.cha` |
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
| Présent aux chapitres 2, 5 et 10 | `2\|5\|10` |

### Moment de la journée  

Cette option permet de définir à quel moment de la journée un objet peut apparaître. Les valeurs possibles correspondent à des périodes spécifiques :  

- **0** : Le jour  
- **1** : Le crépuscule  
- **2** : La nuit  
- **3** : Le matin    

#### Exemples  

| Exemple | Code |
| ------- | ---- |
| Présent à n'importe quel moment de la journée. | `-` |
| Présent uniquement pendant la journée. | `0` |
| Présent uniquement au crépuscule. | `1` |
| Présent uniquement pendant la nuit. | `2` |
| Présent uniquement le matin. | `3` |
| Présent le matin et la journée. | `0\|3` |
| Présent au crépuscule, la nuit et le matin. | `1\|2\|3` |

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
| En normal ou difficile | `2\|4` |

### Équipement de l'objet
    
Cette option, applicable uniquement si la cible est une créature, détermine si l'objet doit être équipé ou simplement ajouté à l'inventaire.

- **Sélection de la créature** : Si l'option est activée, seules les créatures pouvant porter l'objet seront sélectionnées.
- **Gestion des emplacements** : Si l'emplacement où l'objet doit être équipé est déjà occupé, le mod remplacera l'objet existant par celui à distribuer, à condition qu'il soit du même type. Cette vérification garantit que la créature sera apte à l'utiliser.
- **Remplacement** : Si l'objet ne peut pas être équipé dans le slot prévu (par exemple, une arme à deux mains ne pouvant pas être équipée par une créature portant déjà un bouclier), la distribution de l'objet ne sera pas réalisée sur cette créature.

Si la cible est une créature et que l'objet à équiper est une arme ou un bouclier, le mod prend en compte ses compétences martiales pour s'assurer qu'elle peut les utiliser de manière optimale. Une option globale permet de définir le nombre minimal d'étoiles de compétence requis pour qu'une créature puisse équiper l'objet. Par défaut, cette valeur est fixée à 1, mais peut être augmentée jusqu'à 5 pour renforcer la sélectivité. Cela réduit la probabilité qu'une créature reçoive une arme en distribution aléatoire mais reste utile en distribution directe pour éviter des incompatibilités.    
Si une créature ne possède aucune compétence martiale, l'objet sera tout de même équipé, sauf si elle fait partie de la liste de créatures spécifiquement définies comme ne pouvant pas recevoir d'arme.  
Une protection est en place pour éviter de remplacer des objets spéciaux déjà équipés par les créatures. Si l'objet actuel est non droppable ou s'il ne dispose pas de description, il ne sera pas remplacé, car ces objets sont souvent destinés à fournir des capacités spéciales à la créature. Cette règle fonctionne en tandem avec la liste des objets à ignorer.

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

Cette option détermine la probabilité que **l'un des objets sélectionnés aléatoirement** soit effectivement distribué. Elle accepte une valeur comprise entre 1 et 100, représentant un pourcentage.  

- **Valeur basse** : Une valeur faible (par exemple, 10) indique une faible probabilité que l'objet soit distribué.  
- **Valeur élevée** : Une valeur élevée (par exemple, 90) augmente la probabilité que l'objet soit inclus dans la distribution.  

Cela permet de contrôler la fréquence à laquelle un objet aléatoire sélectionné sera effectivement distribué, ajoutant ainsi de la variabilité et de la flexibilité à la distribution.  

#### Exemples  

| Exemple | Code |
| ------- | ---- |
| 100 % de chance (tous les objets seront distribués) | `100` |
| 50 % de chance pour chaque objet sélectionné | `50` |
| 10 % de chance pour chaque objet sélectionné | `10` |

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

Il est aussi possible d'utiliser des négations pour exclure certaines cibles.  
Si vous décidez de sélectionner les nains d'alignement non mauvais dans une zone spécifique.    
L'exemple deviendra : `dwarf.rce&male.gnd&!evils.grp&ar0602.are`  

<a name="groupes"></a>
## Les groupes

Les groupes permettent de regrouper plusieurs entités sous une seule référence, facilitant ainsi la sélection des cibles. Un fichier `.grp` contient les entités à inclure, chacune sur une ligne distincte.

<a name="meta-groupes"></a>
## Les meta-groupes

Les meta-groupes sont des ensembles dynamiques générés automatiquement à partir des données du jeu et s'adaptent aux ajouts d'autres mods. Ils fonctionnent comme des groupes classiques, avec une extension spécifique pour cibler le meta-groupe souhaité.

### Précisions sur l'utilisation

- **Extension et valeur ciblée** : L'extension indique le type de meta-groupe utilisé, tandis que le nom spécifie la valeur ciblée. Par exemple, pour cibler une créature de race humaine, le nom serait human et l'extension .rce (`human.rce`).
- **Fichiers .ids** : Le nom du groupe doit correspondre à une entrée dans le fichier `.ids` pertinent, en respectant la casse (utilisation de **minuscules**). Ces fichiers définissent les différentes valeurs possibles pour un type de donnée (race, classe, etc.).
- **Gestion des espaces** : Les espaces présents dans les noms d'entrée des fichiers `.ids` doivent être remplacés par des underscores (`_`). Par exemple, pour une valeur comme "High Elf", le nom de groupe serait `high_elf.rce`.

### Les meta-groupes basés sur un fichier .ids

| Type | Meta-groupe | Fichier .ids | Extension | Exemple |
| ---- | ----------- | ------------ | --------- | ------- |
| Créature | Race de la créature | [race.ids](<https://gibberlings3.github.io/iesdp/files/ids/bgee/race.htm>) | rce | `human.rce` |
| Créature | Classe de la créature | [class.ids](<https://gibberlings3.github.io/iesdp/files/ids/bgee/class.htm>) | cls | `mage.cls` |
| Créature | Kit de la créature | [kit.ids](<https://gibberlings3.github.io/iesdp/files/ids/bgee/kit.htm>) | kit | `mage.kit` |
| Créature | Genre de la créature | [gender.ids](<https://gibberlings3.github.io/iesdp/files/ids/bgee/gender.htm>) | gnd | `female.gnd` |
| Créature | Alignement de la créature | [alignmen.ids](<https://gibberlings3.github.io/iesdp/files/ids/bgee/alignmen.htm>) | alg | `lawful_evil.alg` |
| Créature | Donnée générale de la créature | [general.ids](<https://gibberlings3.github.io/iesdp/files/ids/bgee/general.htm>) | gen | `undead.gen` |
| Créature | Donnée spécifique de la créature | [specific.ids](<https://gibberlings3.github.io/iesdp/files/ids/bgee/specific.htm>) | spc | `magic.spc` |
| Créature | Compétence martiale de la créature | [wprof.ids](<https://gibberlings3.github.io/iesdp/files/ids/bgee/wprof.htm>) | prf | `proficiency2weapon.spc` |
| Objet | Catégorie de l'objet | [itemcat.ids](<https://gibberlings3.github.io/iesdp/files/ids/bgee/itemcat.htm>) | cat | `amulet.cat` |
| Magasin | Catégorie de l'objet acceptée | [itemcat.ids](<https://gibberlings3.github.io/iesdp/files/ids/bgee/itemcat.htm>) | prc | `boot.prc` |

### Les meta-groupes basés sur d'autres données

| Type | Meta-groupe | Extension | Exemple |
| ---- | ----------- | --------- | ------- |
| Créature | Niveau de la créature | lvl | `2.lvl` |
| Créature | Force de la créature | str | `15.str` |
| Créature | Dextérité de la créature | dex | `14-.dex` |
| Créature | Constitution de la créature | con | `17+.con` |
| Créature | Intelligence de la créature | int | `14-16.int` |
| Créature | Sagesse de la créature | wis | `12.wis` |
| Créature | Charisme de la créature | cha | `12.cha` |
| Créature | Les créatures de la zone | are | `ar0602.are` |
| Objet | Niveau d'echantement de l'objet | ilv | `4+.ilv` |
| Objet | Objets maudits | igr | `cursed.igr` |
| Objet | Armes à deux mains | igr | `two_handed.igr` |
| Objet | Objets magiques | igr | `magical.igr` |
| Objet | Objets qui peuvent s'empiler | igr | `stackable.igr` |
| Objet | Robes | arm | `robe.arm` |
| Objet | Armures de cuir | arm | `leather.arm` |
| Objet | Armures de mailles | arm | `chainmail.arm` |
| Objet | Armures de plates | arm | `platemail.arm` |
| Objet | Targes | arm | `buckler.arm` |
| Objet | Petits boucliers | arm | `small_shield.arm` |
| Objet | Boucliers moyens | arm | `medium_shield.arm` |
| Objet | Grands boucliers | arm | `large_shield.arm` |
| Objet | Parchemins de sort de l'école de l'Abjuration | scl | `abjuration.scl` |
| Objet | Parchemins de sort de l'école de la Conjuration | scl | `conjuration.scl` |
| Objet | Parchemins de sort de l'école de la Divination | scl | `divination.scl` |
| Objet | Parchemins de sort de l'école de l'Enchantement | scl | `enchantment.scl` |
| Objet | Parchemins de sort de l'école de l'Illusion | scl | `illusion.scl` |
| Objet | Parchemins de sort de l'école de l'Évocation | scl | `evocation.scl` |
| Objet | Parchemins de sort de l'école de la Nécromancie | scl | `necromancy.scl` |
| Objet | Parchemins de sort de l'école de l'Altération | scl | `alteration.scl` |
| Objet | Parchemins de sort de l'école généraliste | scl | `generalist.scl` |
| Objet | Parchemins de sort par niveau de sort | scl | `4-6.scl` |
| Objet | Objet qui s'équipe à l'emplacement du casque | slt | `helmet.slt` |
| Objet | Objet qui s'équipe à l'emplacement de l'armure | slt | `armor.slt` |
| Objet | Objet qui s'équipe à l'emplacement du bouclier | slt | `shield.slt` |
| Objet | Objet qui s'équipe à l'emplacement des gants | slt | `gloves.slt` |
| Objet | Objet qui s'équipe à l'emplacement de l'amulette | slt | `amulet.slt` |
| Objet | Objet qui s'équipe à l'emplacement de la ceinture | slt | `belt.slt` |
| Objet | Objet qui s'équipe à l'emplacement des bottes | slt | `boots.slt` |
| Objet | Objet qui s'équipe à l'emplacement de l'arme | slt | `weapon.slt` |
| Objet | Objet qui s'équipe à l'emplacement de la cape | slt | `cloak.slt` |
| Objet | Objet qui s'équipe à l'emplacement des munitions | slt | `quiver.slt` |
| Objet | Objet qui s'équipe à l'emplacement des anneaux | slt | `left_ring.slt` |
| Objet | Objet qui s'équipe à l'emplacement des objets rapides | slt | `quick_item.slt` |
| Magasin | Les magasins | stt | `store.stt` |
| Magasin | Les tavernes | stt | `tavern.stt` |
| Magasin | Les auberges | stt | `inn.stt` |
| Magasin | Les temples | stt | `temple.stt` |
| Magasin | Les conteneurs | stt | `container.stt` |

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

Il est très simple pour un autre mod de s'intégrer au système de répartition d'ItemDispatcher. Pour cela, il suffit de créer un dossier nommé `dispatching` et d'y inclure des fichiers pertinents tels que `items.2da`, des groupes ou des listes de trésors aléatoires.

### Structure d'arborescence

```
dispatching
|_ items.2da
|_ groups
   |_ boss.2da
   |_ all_elf.2da
   |_ ...
|_ treasures
   |_ gems.2da
   |_ bigswords.2da
   |_ ...
```

### Fonctionnement

Lors de l'installation, ItemDispatcher scanne tous les mods présents dans le répertoire du jeu, vérifie l'existence du dossier `dispatching` et traite les fichiers qui s'y trouvent. Cela permet à un mod de s'intégrer harmonieusement au système de distribution d'objets sans nécessiter de modifications complexes.

### Exemple pratique

Si un mod ajoute de nouveaux boss et que l'auteur souhaite les inclure dans la liste des boss existants, il suffit de créer le fichier `groups/boss.2da` et d'y lister les nouvelles cibles. Cela garantit que ses boss seront pris en compte (en plus des boss du jeu de base et ceux ajoutés par d'autres mods) lorsqu'une règle de distribution utilisera ce groupe.

## Quelques règles générales

Un fichier de log est généré pour consigner tous les changements effectués par le mod. Ce fichier peut être utilisé à des fins de vérification ou pour consulter les détails sur la localisation des objets ajoutés.
