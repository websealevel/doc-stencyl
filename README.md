# Stencyl, s'initier au développement d'un jeu vidéo

- [Stencyl, s'initier au développement d'un jeu vidéo](#stencyl-sinitier-au-développement-dun-jeu-vidéo)
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
  - [Animation](#animation)
  - [Évènements](#évènements)
  - [Évènements personnalisés](#évènements-personnalisés)
  - [Changer de scène](#changer-de-scène)
    - [Les blocs du *Design mode*](#les-blocs-du-design-mode)
  - [Les positions](#les-positions)
  - [Conseils](#conseils)
  - [Traductions anglais-français, termes](#traductions-anglais-français-termes)
  - [Liens](#liens)
  - [Ressources](#ressources-1)


Une documentation sur Stencyl et ses concepts et ses concepts. [Stencyl](https://fr.wikipedia.org/wiki/Stencyl) est un outil de développement de jeu vidéo **propriétaire** qui permet de créer **des jeux vidéo en 2D**, à destination d'ordinateurs, de téléphones et du web. Son utilisation globale est gratuite et certaines options sont proposées en supplément payant.

>Hollow Knight a été initialement développé sur Stencyl, puis finalement sur Unity.

Bon outil pour des petits jeux 2D, pour s'initier au développement et au design de jeux vidéo. Le fait qu'il soit notamment développé en Java (et sûrement host par la JVM - à confirmer) fait qu'il est naturellement portable vers tous les OS et tous les devices (desktop et mobile). 

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
- `Behaviors`: ici on ajoute des comportements prédéfinis (`Logic/Behaviors`) à notre classe d'acteurs et on les configure (constantes du comportement comme la vitesse, hauteur d'un saut, la touche à presser, etc.). Par exemple, `jump force` détermine la hauteur maximale du saut

>Le moteur fonctionne par composition. On injecte des comportements dans nos objets comme des composants (Pattern Strategy).

## Les scènes

Une scène (scene) est un niveau du jeu. Elles sont peuplées d'acteurs et de tiles. On peut également attacher des comportements à des scènes.

Créer une nouvelle scène. **Attention**, pour les paramètres `Tile Width` et `Tile Height` **il faut bien faire attention à ce que les valeurs correspondent aux tailles de vos Tiles** (dans vos ressources). Sinon, le moteur va y découper des *tiles* qui ne correspondent pas à vos tiles préparées.

Quand la scène est créée, un éditeur de scène est lancé. On va préparer la scène en plaçant des tuiles et des acteurs. On y ajustera également la gravité.

Une fois la scène prête à être testée, lancer le jeu (`Ctr+Enter`).

## Animation

Une `Animation` représente un état dans lequel un acteur peut se trouver (*walking*, *running*, *jumping*, etc.). Il est donc conseillé de nommer les animations en accord avec les états qu'elles représentent. Pour créer une animation, il faut combiner des images (*frames*).


## Évènements

Les évènements (events) sont définis dans le Design Mode. Un évènement contient de la logique de jeu. *Les comportements (behaviors) sont composés d'évènements*. En fait, un comportement est un conteneur d'évènements. On utilise généralement des comportements car on peut les attacher ensuite à n'importe quelle scène ou Actor Type. Créer directement un évènement sur un `Actor Type` ou une scène ne permet pas de dupliquer le comportement avec d'autres acteurs. C'est utile si on veut désigner *du comportement unique à une classe*.

Les différents types d'évènements:

- Basic:
  - `When creating`: à la création de l'objet (acteur, scene)
  - `When drawing`: au moment du rendu graphique sur la sortie. Se repète sans cesse dans la game loop.
  - `When updating`: au moment de la mise à jour de l'état du jeu. Se repète sans cesse dans la game loop. C'est *la mise à jour qui fait avancer l'état du jeu*.

## Évènements personnalisés

En Design Mode, dans l'onglet Events d'un Actor Type, Scene on peut définir un *évènement custom* avec une chaine de carcactères dans certains blocs `trigger event` (onglet `Behaviors`). On peut ainsi déclencer des évènements personnalisés sur un Actor Type ou une scène dans des conditions particulières. Puis on peut y répondre en ajoutant un évènement puis `Advanced/Custom Events`.

## Changer de scène

Les block utiles sont dans `Scene/Game flow` dans le *Design Mode*. Voir ici un [article de la documentation sur le changement de scène](https://www.stencyl.com/help/view/changing-scenes/) (de niveaux).

### Les blocs du *Design mode*

-  `set x-speed to [value] for [Self]`: ajuste la vitesse horizontale (>0 vers la droite) pour Self, la classe sur laquelle on déclare l'évènement (Actor Type ou Scene).


## Les positions

Stencyl mesure la position d'un acteur depuis le coin haut gauche du sprite. Conformément aux standards du traitement d'image, la position (0,0) est le coin haut à gauche (scène, sprite de l'acteur). *L'axe x est orienté vers la droite et l'axe y vers le bas*.


## Conseils

- Pour se familiariser avec l'outil, [faire le Crash Course 1](https://www.stencyl.com/help/start/) et le [Crash Course 2](https://www.stencyl.com/help/start/)
- Améliorer vous-même le Crash Course 1 : 
  - on n’a pas d'*inertie* en l'air (si on arrête de presser touche left ou right on s'arrête net, perte de l'élan dans une direction)
  - on ne peut pas sauter *quand* on est sur un clown
  - le clown ne se déplace pas
- ne pas oublier d'enregistrer son jeu régulièrement

## Traductions anglais-français, termes

- *idle*: inactif, sur place
- *stomp*: piétiner
- *tile*: tuile
- *frame*: image d'une animation. Un jeu tournant à 60 [frames/seconde](https://fr.wikipedia.org/wiki/Images_par_seconde) (60 FPS) affiche 60 images en 1 seconde, chaque image est donc affichée durant 1/60 ~ 16.6ms sur la sortie d'affichage.
- *Game loop*: La *game-loop* est le mécanisme de base qui permet de faire évoluer le jeu dans le temps. C'est une séquence de code qui tourne en boucle tant que le jeu est lancé et se termine soit suite à une action de la personne qui joue, soit par un game-over. Durant la game-loop, trois processus sont généralement en cours d'exécution: 
  - récupérer et traiter les inputs de la personne qui joue (*input*)
  - mettre à jour l'état du jeu (déplacement du joueur, passage du temps, mise à jour du monde, etc.) (*update*)
  - *rendre* le jeu (représentation graphique, peindre le nouvel état sur l'écran pour représenter l'état du jeu actuel) (*render*)
À la fin de la *loop*, les ressources allouées (mémoire RAM, GPU et CPU) doivent être *proprement rendues* et le contrôle rendu à l'OS.

## Liens

- [Programmation de jeux vidéo (wiki)](https://fr.wikipedia.org/wiki/Programmation_de_jeux_vid%C3%A9o), aperçu général
- [Game Loop (Programming Pattern)](https://gameprogrammingpatterns.com/game-loop.html), un article sur le pattern de game loop et les écueils à éviter
- [Game Loop en Javascript](https://developer.mozilla.org/en-US/docs/Games/Anatomy), un article sur la gameloop en Javascript dans l'environnemetn du navigateur (jeux HTML5)
- [Stencyl (site officiel)](https://www.stencyl.com/)
- [Stencyl documentation](https://www.stencyl.com/help/)
- [Working with behaviors (Design Mode)](https://www.stencyl.com/help/view/working-with-behaviors/), créer des comportements et maitriser le `Design Mode`
- [Events](https://www.stencyl.com/help/view/events-reference/)
- [(Behavior) attributes](https://www.stencyl.com/help/view/attributes/), les variables d'état d'un comportement, et donc par extension, d'un acteur ou d'une scène qui implémente ce comportement
- [Game attributes](https://www.stencyl.com/help/view/game-attributes/), les variables d'environnement (global au jeu)
- [Attributes Types](https://www.stencyl.com/help/view/attribute-types-reference/), les différents types d'attributs définis par Stencyl, utilisables et configurables comme propriétés de comportements. Et leurs représentations graphiques


## Ressources

- [Game Developers Conference (GDC)](https://gdconf.com/), LA conférence annuelle de la communauté du développement du jeux vidéos. Des tonnes et des tonnes de conférences gratuites, de qualité (également dans la captation) à regarder.
- [Magic: the Gathering: Twenty Years, Twenty Lessons Learned](https://youtu.be/QHHg99hwQGY), très belle conférence sur le game design sur le long terme et le renouvellement du gameplay et d'une licence
- [Diablo: A Classic Game Postmortem](https://youtu.be/VscdPA6sUkc), conférence superbe, drôle et enrichissante sur le développement de Diablo dans les années 90 par le créateur original lui même
- [Game programming patterns (en)](https://www.pdfdrive.com/game-programming-patterns-e158623095.html), une référence dans le domaine, un livre de [Robert Nystrom](https://twitter.com/munificentbob). Ce livre couvre l'architecture et le design dans le domaine du développement JV.
- [Artificial Intelligence for games, 2n edition (en)](https://www.pdfdrive.com/artificial-intelligence-for-games-e25411627.html), un très beau livre très complet qui référence énormément de patterns, stratégies, techniques et algorithmes pour tous vos besoins en termes d'IA. Viens avec une bibliographie très complète pour approfondir un sujet qui a su retenir notre attention.
- [The Art of Game Design, 2nd edition (en)](https://www.pdfdrive.com/the-art-of-game-design-a-book-of-lenses-2nd-edition-e157699641.html)
- [Level Up! The guide to great video game design (en)](https://www.pdfdrive.com/level-up-the-guide-to-great-video-game-design-e157921744.html)
- [Procedural generation in game design (en)](https://www.pdfdrive.com/procedural-generation-in-game-design-e184787611.html)
- [GameDev Ressources](https://github.com/Kavex/GameDev-Resources), un dépôt recensant une tonne de ressources pour le développement de jeux vidéo (asset, code, design, outils, etc.)
- [Magic tools](https://github.com/ellisonleao/magictools), un autre dépôt recensant une tonne de ressources pour le développement de jeux vidéo (asset, code, design, outils, etc.)
- [Keys to Economic Systems](https://gdkeys.com/keys-to-economic-systems/?utm_source=pocket_mylist), un excellent article sur la modélisation de systèmes économiques dans un jeu vidéo.