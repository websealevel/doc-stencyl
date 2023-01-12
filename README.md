# doc-stencyl

- [doc-stencyl](#doc-stencyl)
  - [Détails techniques](#détails-techniques)
  - [Concepts de base](#concepts-de-base)
    - [Ressources](#ressources)
      - [Acteurs (`Actor`)](#acteurs-actor)
      - [L'éditeur de template d'acteurs (`Actor Type Editor`)](#léditeur-de-template-dacteurs-actor-type-editor)
      - [Autres ressources et éditeurs](#autres-ressources-et-éditeurs)
    - [Logique (comportements et code)](#logique-comportements-et-code)
  - [Groupes et collisions (groups)](#groupes-et-collisions-groups)
  - [Personnaliser un template d'acteur](#personnaliser-un-template-dacteur)
  - [Les scènes](#les-scènes)
  - [Conseils](#conseils)
  - [Traductions anglais-francais](#traductions-anglais-francais)
  - [Ressources](#ressources-1)


Une documentation sur Stencyl et ses concepts et ses concepts. [Stencyl](https://fr.wikipedia.org/wiki/Stencyl) est un outil de développement de jeu vidéo **propriétaire** qui permet de créer **des jeux vidéo en 2D**, à destination d'ordinateurs, de téléphones et du web. Son utilisation globale est gratuite et certaines options sont proposées en supplément payant.

>Hollow Knight a été initialement développé sur Stencyl, puis finalement sur Unity.

Bon outil pour des petits jeux 2D, pour s'initier au développement et au design de jeux vidéos. Le fait qu'il soit notamment développé en Java (et sûrement host par la JVM - à confirmer) fait qu'il est naturellement portable vers tous les OS et tous les devices (desktop et mobile). 

## Détails techniques

- propriétaire, existe depuis 2011
- développé en Java, [ActionScript](https://fr.wikipedia.org/wiki/ActionScript) (implémentation du standard ECMAScript par Macromedia, propriété d'Adobe) et [Haxe](https://fr.wikipedia.org/wiki/Haxe)
- host par la [JVM](https://fr.wikipedia.org/wiki/Machine_virtuelle_Java) et donc multiplateformes et multidevices
- *visual coding*
- possibilité de coder via l'extension de classes (en Haxe)

## Concepts de base

L'outil est divisé en différentes sections: les ressources (assets et templates), la logique (comportements et code)

### Ressources

Le logiciel s'ouvre sur le `Dashboard`, qui nous permet d'accéder à toutes les ressources de notre jeu.

#### Acteurs (`Actor`)

Tout ce qui peut bouger ou être interactif (tout ce qui a un comportement) est un `Actor` (personnage jouable, ennemi, éléments d'interfaces, objets, etc.). Un `Actor Type` est un template d'Actor (une classe), un Actor en est une instance (un objet).

#### L'éditeur de template d'acteurs (`Actor Type Editor`)

Si on double-click sur un Actor Type, on ouvre l'`Actor Type Editor`. Cet éditeur permet de personnaliser l'apparence, le comportement et les propriétés physiques (moteur physique) de l'Actor Type.

>`Ctr+o` permet d'ouvrir un menu pour accéder à n'importe quelle ressource.

#### Autres ressources et éditeurs

- Tilesets
- Sounds
- Scenes
- Fonts
- Backgrounds

### Logique (comportements et code)

Les comportements (`Behavior`) contrôlent toute la logique du jeu et les interactions entre le programme et la personne qui joue. On peut accéder au `Design Mode`, un [éditeur de comportement](https://www.stencyl.com/help/view/working-with-behaviors/).

>Si l'on préfère coder, on peut soit ouvrir un éditeur de code prévu à cet effet (ou intégrer son éditeur de code favori), soit utiliser des blocks de code où l'on peut insérer du code.

## Groupes et collisions (groups)

Les [groupes](https://www.stencyl.com/help/view/collisions-and-groups/) permettent de gérer les collisions entre acteurs. Ils sont utilisés pour déterminer quelles classes d'Actor (Actor Type) rentrent en collision avec qui.

Pour éditer des groupes, ouvrir le menu `Settings/Groups`. Ici on peut créer et éditer des groupes et indiquer avec quelles classes d'acteur ils rentrent en collision.

## Personnaliser un template d'acteur

Dans l'éditeur de template d'acteur (Actory Type Editor):

- `Properties`: nom du patron, groupe auquel il appartient
- `Physics`: rotation autorisée, soumis à la gravité, friction, propriétés élastiques et visqueuses (rebond, amortissement), etc.
- `Behaviors`: ici on ajoute des comportements prédéfinis (`Logic/Behaviors`) à notre classe d'acteurs et on les configure (constantes du comportement comme la vitesse, hauteur d'un saut, la touche à presser, etc.)

>Le moteur fonctionne par composition. On injecte des comportements dans nos objets comme des composants (Pattern Strategy).

## Les scènes

Une scène (scene) sont des niveaux du jeu. Elles sont peuplées d'acteurs et de tiles. On peut également attacher des comportements à des scènes.

Créer une nouvelle scène. **Attention**, pour les paramètres `Tile Width` et `Tile Height` **il faut bien faire attention à ce que les valeurs correspondent aux tailles de vos Tiles** (dans vos ressources). Sinon, le moteur va y découper des *tiles* qui ne correspondent pas à vos tiles préparées.

Quand la scène est créee, un éditeur de scène est lancé. On va préparer la scène en plaçant des tuiles et des acteurs. On y ajustera également la gravité.

Une fois la scène prête à être testée, lancer le jeu (`Ctr+Enter`).

## Conseils

- Pour se familiariser avec l'outil, [faire le Crash Course 1](https://www.stencyl.com/help/start/)
- Améliorer vous-même le crash course 1
- ne pas oublier d'enregistrer son jeu régulièrement

## Traductions anglais-francais

- *idle*: inactif, sur place
- *stomp*: piétiner
- *tile*: tuile

## Ressources

- [Stencyl (site officiel)](https://www.stencyl.com/)
- [Stencyl documentation](https://www.stencyl.com/help/)
- [Working with behaviors (Design Mode)](https://www.stencyl.com/help/view/working-with-behaviors/)