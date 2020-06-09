# Vous ne connaissez pas encore JS : Débuter - 2e édition
# Chapitre 1 : Qu'est-ce que JavaScript ?

Tout comme moi, vous ne connaissez pas encore JavaScript, du moins pas complètement. Comme aucun de nous d'ailleurs. Nous pouvons toutefois tous faire plus ample connaissance avec JavaScript.

Dans ce premier chapitre du premier livre de la série *Vous ne connaissez pas encore JS* (You Don't Know JS Yet dans sa version originale, abrégée YDKJSY), nous allons prendre le temps de constituer de solides bases pour bien préparer la suite. Nous allons donc commencer par explorer toute une variété d'importants détails de contextualisation et d'effacer quelques mythes et idées reçues à propos de ce qu'est réellement le langage (et ce qu'il n'est pas).

Il s'agit d'un précieux aperçu que tous les développeurs JS devrait connaître portant sur l'identité et la façon dont Javascript est organisé et maintenu. Si vous voulez faire plus amples connaissance avec JS, voici la première étape de votre voyage.

## A propos du livre

J'insiste sur le mot voyage car *connaître JS* n'est pas une destination, c'est une direction. Quel que soit le temps passé sur le langage, vous allez toujours trouver quelque chose à apprendre et à comprendre un peu mieux. Donc ce livre n'est pas une lecture à faire rapidement en quête d'un accomplissement quelquonque. C'est plutôt dans la patience et la persistence que vous ferez des premiers pas de qualité.

A la suite de ce chapitre de contextualisation, le reste du livre dresse un panomara de haut-vol sur ce que vous trouverez en creusant et en étudiant le JS au sein de la série *YDKJSY*.

Le chapitre 4 identifie notamment trois piliers principaux autour duquel le JS est organisé: portée/fermetures, prototypes/objets et types/coercition. JS est un langage vaste et complexe avec beaucoup de fonctionnalités et de potentiel. Mais tout le JS est fondé sur ces trois piliers fondateurs.

Gardez à l'esprit que même si ce livre est intitulé "Débuter", il n'est pas destiné à être un livre d'introduction. Son travail principal est de vous préparer à étudier JS en profondeur tout au long de la série. Il est écrit en supposant que vous êtes familié avec JS avec déjà plusieurs mois d'experience. Soyez donc certain d'avoir déjà passé beaucoup de temps à écrire du JS pour vous avoir construit une expérience afin d'en tirer le plus possible.

D'ailleurs, même si vous avez déjà écrit beaucoup de JS, ce livre ne devrait pas être survolé. Prenez votre temps pour parcourir l'ensemble de son contenu : **un bon début dépend toujours d'un solide premier pas.**

<!-- @todo find a better title here -->
## Qu'y a-t-il avec ce nom ?

Le nom JavaScript est probablement le plus mal compris des noms de langages de programmation. Est-il lié à Java ? Est-ce uniquement la version scriptée de Java ? Est-ce uniquement pour écrire des scripts et non de réels programmes ?

En fait le nom JavaScript est l'artefact d'une combine marketing. Quand Brendan Eich a conçu le langage, il l'a appelé Mocha. En interne chez Netscape, la marque LiveScript était utilisée. Mais quand il a fallu le nommer publiquement, "JavaScript" remporta les suffrages.

Pourquoi ? Car le langage a été originellement conçu pour attirer une audience principalement composée de développeurs Java et parce que le mot "script" était populaire à cette époque pour faire référence à des programmes légers. Ces "scripts ultra légers seraient les premier à s'insérer dans les pages de cette nouvelle chose appelée web !

En d'autre termes, JavaScript était un stratagème marketing pour essayer de positionner ce langage comme une bonne alternative à l'écriture du plus lourd et plus connu Java. C'est pour cette raison qu'il aurait tout aussi bien pu s'appeler "WebJava".

Il y a quelques similitudes superficielles entre le code JavaScript et le code Java. Ces ressemblances ne proviennent pas forcément d'un développement partagé mais plutôt d'une volonté des deux langages de viser les développeurs ayant des attentes assummées de syntaxe par rapport au C (et par extension au C++).

<!-- @todo Need a better translation here -->
<!-- There are some superficial resemblances between JavaScript's code and Java code. Those similarities don't particularly come from shared development, but from both languages targeting developers with assumed syntax expectations from C (and to an extent, C++). -->

Par exemple, on utilise le `{` pour commencer un bloc de code et `}` pour le terminer, comme en C/C++ et Java. On utilise aussi le `;` pour ponctuer la fin d'une déclaration.

D'une certaine manière, les relations légales sont plus profondes que la syntaxe. Oracle (via Sun), l'entreprise qui possède et maintient toujours Java est aussi propriétaire de la marque "JavaScript" (via Netscape). Cette marque n'est presque jamais appliquée et semble ne pouvoir jamais l'être.

Pour ces raisons, certains ont suggéré qu'on utilise le terme JS au lieu de JavaScript. C'est un raccourci très commun et même un bon candidat pour vendre officiellement le langage. D'ailleurs, ces livres utilisent presque exclusivement le terme JS pour y faire référence.

Plus éloigné de la marque détenue par Oracle, le nom officiel du langage spécifié par TC39 et formalisé par les standards ECMA est **ECMAScript**. Et d'ailleurs, depuis 2016, le nom officiel du langage a été suffixé par son année de révision. Au moment d'écrire ces lignes, il s'agit de la version ECMAScript 2019, autrement abrégée ES2019.

En d'autres termes, le JavaScript/JS éxécuté par votre navigateur ou dans Node.js est *une* implémentation du standard ES2019

| NOTE: |
| :--- |
| N'utilisez pas des termes comme "JS6" ou "ES8" pour faire référence au langage. Certains le font mais ces appellations contribuent à perpétuer la confusion. Vous devriez vous en tenir à "ES20xx" ou juste "JS" |

En tout cas, que vous l'appeliez JavaScript, JS, ECMAScript, ou ES2019, ce n'est définitivement pas une variante du langage Java !

> "Java is to JavaScript as ham is to hamster." --Jeremy Keith, 2009

## Spécifications du langage

J'ai mentionné TC39, le comité de direction technique qui gère JS. Leur premier rôle est la gestion de la spécification officielle du langage. Il se réunit régulièrement pour valider les changements convenus qu'ils soumettent ensuite à ECMA, l'organisation qui gère les standards.

La syntaxe JS et son comportement sont définis dans la spécification ES.

ES2019 est la dixième spécification/révision majeure depuis l'origine de JS en 1995, donc dans l'adresse URL officielle des spécifications hébergée par ECMA, vous trouverez "10.0".

https://www.ecma-international.org/ecma-262/10.0/

Le comité TC39 est composé d'environ 50 à 100 personnes provenant d'un large éventail d'entreprises investies dans le web comme les fabricants de navigateurs (Mozilla, Google, Apple) et les fabricants d'appareils (Samsung, etc). Tous les membres sont volontaires bien que la plupart soient des employés de ces entreprises et donc pouvant recevoir des compensations pour leur travail au sein du comité.

TC39 se réunit généralement tous les mois pendant trois jours pour faire la revue du travail réalisé par ses membres depuis la dernière rencontre, pour discuter des problèmes et voter les propositions. Les lieux de réunions tournent entre les entreprises membre prêtent à accueillir l'événement.

Toutes les propositions au TC39 passent pas un processus scinder en cinq étapes. Comme nous sommes des développeurs, la première étape est le 0, de 0 à 4 donc. Vous pouvez trouver davatange d'informations ici : https://tc39.es/process-document/

L'étape 0 signifie que quelqu'un au TC39 pense qu'une idée en vaut la peine et a l'intention de la défendre. Cela signifie que beaucoup d'idées qui sont proposées par des non membres du TC39 via des réseaux informels comme les réseaux sociaux ou les billets de blog sont plutôt des "pré-étape 0". Pour être officiellement considérée à l'étape 0; une proposition doit être soutenue par un membre du TC39.

Une fois qu'une proposition atteint l'étape 4, elle est éligible pour être incluse à la prochaine révision annuelle du langage. Cela peut prendre de quelques mois à quelques années pour qu'une proposition passe toutes les étapes.

Toutes les propositions sont gérées publiquement, sur le dépôt Github du TC39 : https://github.com/tc39/proposals

Toute personne, du TC39 ou non, est encouragée à participer à ces discussions publiques et aux différentes étapes de travail sur ces propositions. Cependant, seul les membres du TC39 peuvent assister aux réunions et voter les propositions et changements. Donc, de ce fait, la voix d'un membre du TC39 aura un impact important sur la direction que suivra JS.

Contrairement à des mythes établis et malheureusement perpétués, il n'y a *pas* de multiples versions de JavaScript dans la nature. Il n'y a qu'**un JS**, le standard officiel maintenu par TC39 et ECMA.

Au début des années 2000, quand Microsoft a maintenu une fourche et une version rétro-ingénieurisé (et pas totalement compatible) de JS appelée "JScript", il y a avait légitimement "plusieurs version" de JS. Mais ces jours sont loin. Cela n'est donc plus d'actualité et imprécis d'affirmer cela aujourd'hui.

Tous les principaux fabricants de navigateurs et d'appareils se sont engagés pour garder leur implémentation de JS conforme à cette spécification centrale. Bien sûr, les moteurs développent des fonctionnalités à des moments différents. Mais il ne devrait jamais être possible que le moteur v8 (Chrome) implémente une fonctionnalité spécifiée de sorte à ce qu'elle soit différente ou incompatible à celle du moteur SpiderMonkey (Mozilla).

Cela signifie que vous pouvez apprendre **un JS** et compter sur ce même JS de partout.

### Le web dirige tout ce qui touche au JS

Alors que la liste des environnements qui execute JS s'étend constamment (des navigateurs aux serveurs (Node.js), en passant par les robots, les ampoules, etc.), celui qui gouverne JS est le web. En d'autres termes, la façon dont JS est implémenté pour les navigateurs web est, en tout pragmatisme, la seule réalité qui compte.

Pour sa majeure partie, le JS définit dans la spécification et le JS éxécuté dans les moteurs JS des navigateurs sont les mêmes. Mais il existe quelques différences qui nécessite d'être considérées.

<!-- @todo review translation here -->
Parfois, la spécification JS dictera un comportement nouveau ou mis à jour et pourtant cela ne correpondra pas exactement à la façon dont cela fonctionne dans les moteurs JS des navigateurs web. Une telle différence est historique : les moteurs JS ont eu plus de 20ans de comportement observable autour de petits bouts de fonctionnalités sur lesquels les contenus webs en sont venu à compter dessus. De ce fait, parfois les moteurs JS refuseront de se conformer à un changement dicté par la spécification car cela pourrait casser du contenu web.

<!-- Sometimes the JS specification will dictate some new or refined behavior, and yet that won't exactly match with how it works in browser-based JS engines. Such a mismatch is historical: JS engines have had 20+ years of observable behaviors around corner cases of features that have come to be relied on by web content. As such, sometimes the JS engines will refuse to conform to a specification-dictated change because it would break that web content. -->

Dans ces cas, TC39 fera souvent marche arrière et choisira simplement de rendre la spécification conforme à la réalité du web. Par exemple, TC39 a planifié d'ajouter la méthode `contains(..)` aux *Arrays* mais il se trouve que ce nom rentrait en conflit avec un vieux *framework* JS encore utilisé par quelques sites. Ils ont donc changé le nom pour un `includes(..)` rassembleur. La même chose est arrivée pour la crise comique/tragique de la communauté JS surnommée "smooshgate", quand la méthode `flatten(..)` prévue au départ a été finalement renommée `flat(..)`.

De temps en temps, TC39 décide que la spécification doit être ferme sur certains points même s"il est assez peu probable que les moteurs JS des navigateurs web se conformeront un jour.

La solution ? Appendix B, "Les fonctionnalités ECMAScript additionnelles pour les navigateurs web".[^specApB]. La spécification JS inclut cet appendix pour détailler toute différence connue entre la spécification officielle et la réalité du JS sur le web. En d'autres termes, il y a des exceptions qui sont autorisées *seulement* pour le JS du web. Les autres environnements JS doivent suivre la loi à la lettre.

<!-- @todo double check here -->
Les sections B.1 et B.2 couvrent les *additions* au JS (syntaxes et APIs) que le JS du web inclut, encore une fois, pour des raisons historiques mais dont TC39 ne projette pas formellement de les inclure dans le coeur de JS. Des exemples : inclure le `0`- pour les octaux libéraux préfixés, le global `escape(..)` / `unescape(..)` utilitaires, String "helpers" comme `anchor(..)` et `blink()` et la méthode RegExp  `compile(..)`.

<!-- Section B.1 and B.2 cover *additions* to JS (syntax and APIs) that web JS includes, again for historical reasons, but which TC39 does not plan to formally specify in the core of JS. Examples include `0`-prefixed octal literals, the global `escape(..)` / `unescape(..)` utilities, String "helpers" like `anchor(..)` and `blink()`, and the RegExp `compile(..)` method. -->

La section B.3 inclut quelques conflits où le code peut séxécuter à la fois dans les moteurs des navigateurs web et dans les moteurs non-web mais où le comportmeent *pourrait* être différent, résultant en différents résultats. La plupart des changements listés implique des situations qui sont labellisées comme des erreurs précoces quand le code s'éxecute en *mode strict*.

L'appendix B *gotchas* ne sont pas souvent rencontrées mais c'est toujours une bonne idée d'éviter ces constructions pour être sûr dans le futur. Partout où il est possible, adhérez à la spécification JS et ne comptez pas sur des comportement applicables uniquement dans certains environnements JS.

### Pas tout le (web) JS

Est-ce que ce code est un programme JS ?

```js
alert("Hello, JS!");
```

Cela dépend de la façon dont vous voyez les choses. La fonction `alert(..)` présentée ici n'est pas incluse dans la spécification JS malgré le fait que ce soit le cas dans tous les environnements JS web. Toutefois, vous ne la trouverez pas dans l'Appendix B, qu'en penser ?

Différents environnements JS (comme les moteurs JS des navigateurs, Node.js, etc.) ajoutent des API à la portée globale de vos programmes JS qui vous donne des fonctionnalités spécifiques à l'environnement, comme pouvoir afficher une fenêtre pop-up d'alerte dans le navigateur de l'utilisateur.

En fait, une grande variété d'API assimilées JS comme `fetch(..)`, `getCurrentLocation(..)`, et `getUserMedia(..)` sont toutes des API web qui ressemblent à JS. Dans Node.js, on a accès à des centaines de méthodes d'API provenant de modules intégrés, comme `fs.write(..)`.

Un autre exemple commun est la méthode `console.log(..)` (et toutes les autres méthodes  `console.*`). Celles-ci ne sont pas spécifiées dans JS mais de part leur utilité universelle sont définies par presque tous les environnements JS, suivant un consensus à peu près convenu.

Donc `alert(..)` et `console.log(..)` ne sont pas définies par JS. Mais elles *ressemblent* à JS. Ce sont des fonctions et des méthodes d'objets qui suivent les règles syntaxiques du JS. Les comportements derrière sont controlés par l'environnement exécutant le moteur JS, mais à la surface elles respectent JS pour pouvoir jouer sur son terrain de jeu.

La plupart des différences entre navigateurs dont les gens se plaignent en disant "le JS est incohérent !" sont en fait dues aux différences dans le comportement de ces environnements, pas dans la façon dont le JS en soi fonctionne.

Donc un appel `alert(..)` *est* du JS mais `alert` en soi n'en est pas réellement, il s'agit juste d'un invité, ce n'est pas une partie de la spécification JS officielle.

### Ce n'est pas toujours du JS

Au premier coup d'oeil, l'utilisation de la console/REPL (Read-Evaluate-Print-Loop) dans les outils de développement de votre navigateur (ou dans Node) ont l'air de plutôt être un environnement JS simple. Mais ce n'est pas vraiment le cas.

Les outils de développement sont... des outils pour les développeurs. Leur premier rôle est de rendre la vie des développeurs plus simple. Ils priorisent l'expérience développeur (DX). Ce n'est *pas* leur but de précisément et strictement refléter toutes les nuances du comportement JS de la spécification. De ce fait, il y a beaucoup d'excentricités qui pourrait agir comme un *"gotchas"* si vous considérez la console comme un environnement JS *pur*.

Soit dit en passant, c'est une bonne chose! Je suis ravi que les outils de développement rendent la vie des développeurs plus simple ! Je suis content qu'on ait de belles fonctionnalités comme l'auto-complete des variables/propriétés. Je pointe juste du doigt le fait que nous ne pouvons et nous ne devrions pas attendre que de tels outils  adhérent *toujours* strictement à la façon dont les programmes JS sont gérés car ce n'est pas leur rôle.

Comme le comportement de tels outils varie d'un navigateur à un autre et qu'ils changent (parfois fréquemment), je ne vais pas ici aborder chaque détail, ceci rendrait ce livre vite obsolète.

<!-- @todo double check here -->
Je vais plutôt juste faire allusion à quelques exemples concernant certains cas de différentes consoles d'environnements JS pour appuyer mon propos sur le fait de ne pas supposer qu'il s'agit de JS natif en les utilisant :

* Si oui ou non la déclaration de `var` ou `function` au plus haut niveau de la portée globale de la console crée de réelle variables globales (reflétant ainsi la propriété `window` et vice-versa).
* Ce qui arrive en utilisant de multiples déclarations `let` et `const` au plus haut niveau de la portée globale.
* Que `"use strict";` sur une entrée de ligne (en allant à la ligne après) active le mode strict pour le reste le session de cette console, de la même façon que sur la première ligne d'un fichier .js, ainsi que la façon dont vous pouvez utiliser `"use strict";` au delà de cette première ligne et toutefois conserver ce mode strict activer pour la session
* Comment le lien par défaut du `this` en dehors du mode strict fonctionne pour les appels de cfonctions et la façon dont l'usage de l'objet global va contenir les variables globales attendues.
* Comment *l'hoisting* (voir livre 2,  *Portée et fermetures*) fonctionne au sein des différentes lignes de code.
* Et beaucoup d'autres...

<!-- * Whether a `var` or `function` declaration in the top-level "global scope" of the console actually creates a real global variable (and mirrored `window` property, and vice versa!).

* What happens with multiple `let` and `const` declarations in the top-level "global scope."

* Whether `"use strict";` on one line-entry (pressing `<enter>` after) enables strict mode for the rest of that console session, the way it would on the first line of a .js file, as well as whether you can use `"use strict";` beyond the "first line" and still get strict mode turned on for that session.

* How non-strict mode `this` default-binding works for function calls, and whether the "global object" used will contain expected global variables.

* How hoisting (see Book 2, *Scope & Closures*) works across multiple line entries.

* ...several others -->

La console n'essaye pas de prétendre être un compilateur JS qui gère votre code exactement de la même façon que le moteur JS gèrerait un fichier .js. Elle essaye de faire en sorte que ce soit plus facile et plus rapide d'entrer quelques ligne de code et d'en voir un résultat rapide. Il s'agit donc d'usages complètement différents et de ce fait, ce n'est pas raisonnable de s'attendre à un outil qui gère les deux de la même façon.

Ne pensez pas que le comportement que vous constatez dans la console des outils de développement est une *exacte* représentation de la sémantique JS. Pour cela, lisez la spécification. Voyez plutôt à la console comme un environnement "JS-friendly" qui est utile en soi.

## Différents visages

Le terme "paradigme" dans le contexte d'un langage de programmation fait référérence à une large (presque universelle) approche de structuration du code. Au sein d'un paradigme, il y a toute une myriade de variations de style et de formes qui distinguent les programmes, incluant un nombre incalculable de librairies, de *frameworks* qui laissent leur signature singulière sur un code donné.

Mais quel que soit le style individuel d'un programme, les grands axes de la vue d'ensemble autour d'un paradigme sont pour tout programme presque toujours évidents au premier coup d'oeil.

Des catégories de code typique au niveau d'un paradigme incluent le procédural, l'objet orienté (OO/classes) et fonctionnel (FP) :

* Le style procédural organise le code de haut en bas, dans une progression linéaire au sein d'opérations prédétérminées, souvent collectées ensemble au sein d'unités liées appelées procédures.
* Le style orienté objet organise le code en collectant la logique et les données ensemble dans des unités appelées classes.
* Le style fonctionnel organise le code en fonctions (du traitement pur par opposition aux procédures) et à leurs utilisations comme valeurs.

Ces paradigmes ne sont ni bon ni mauvais. Ce sont des orientations qui guident et qui forgent la façon dont les développeurs abordent les problèmes et leurs solutions, comment ils structurent et maintiennent leur code.

Certains langages sont fortement liés à l'un de ces paradigmes : C est procédural, Java/C++ sont presque entièrement orientés objet et Haskell est fonctionnel de bout en bout.

Mais beaucoup de langages supportent différents modèles de code qui peuvent provenir, et même être un mix, de différents paradigmes. Ces bien nommés "langages multi-paradigmes" offre une flexibilité ultime. Dans certains cas, un programme peut même avoir deux ou plusieurs expressions de ces paradigmes se cotoyant.

JavaScript est sans aucun doute un langage multi-paradigme. Vous pouvez écrire du procédural, du orienté objet et du fonctionnel et vous pouvez choisir tel ou tel paradigme à chaque ligne de code plutôt que de forcer le choix vers du tout ou rien.

<!-- @todo Find a better title -->
## Vers l'avant et vers l'arrière

L'un des principes fondamentaux qui guide JavaScript est la préservation de la *rétro-compatibilité*. Beaucoup de gens sont perdus vis-à-vis des implications de ce terme et le confondent souvent avec le terme lié mais différent de *compatibilité ascendante*.

Remettons les pendules à l'heure.

La rétrocompatibilité signifie qu'une fois quelque chose accepté comme du JS valide, il n'y aura pas de futurs changements du langage qui rendront ce code invalide. Le code écrit en 1995 (aussi primitif et limité soit-il) doit toujours fonctionner aujourd'hui. Comme le proclament souvent les membres du TC39 : "On ne casse pas le web !".

L'idée est que les développeurs JS peuvent écrire du code en toute confiance en sachant que celui-ci ne cessera pas de fonctionner de façon inprédictible à cause de la mise à jour d'un navigateur. Cela rend la décision de choisir le JS pour un programme plus sage et un investissement plus sur, pour des années dans le futur.

Cette "garantie" n'est pas un détail. Maintenir la rétro-compatbilité sur maintenant bientôt 25 ans crée un énorme poids et tout un tas de challenges uniques. Il vous serait difficile de trouver beaucoup d'autres exemples d'un tel travail de rétrocompatibilité dans le domaine de la programmation .

Le cout de coller à un tel principe ne devrait pas être vulgairement mis de côté. Cela crée nécessairement une bar très haute pour inclure, changer ou étendre le langage. Chaque décision devient effectivement permanente, les bonnes comme les mauvaises. Une fois que c'est du JS, cela ne peut pas être retiré car cela pourrait casser des programmes, même si on aimerait vraiment, vraiment, les retirer !

Il y a quelques exceptions à cette règle. JS a eu quelques changements non rétrocompatibles, mais le TC39 est extrêmement prudent à ce sujet. Il étudie le code existant sur le web (via la récolte des données des navigateurs) pour estimer l'impact de tels changements et les navigateurs décident à la fin et votent si ils sont prêts à ou non à recevoir les foudres des utilisateurs pour de très petits changements comparés aux bénéfices d'améliorer ou réparer certains aspects du langage pour bien d'autres sites (et utilisateurs).

Ce genre de changements sont rares et concernent presque tous des petits cas spécifiques qui ne peuvent évidemment pas casser beaucoup de sites.

Il faut maintenant comparer la rétro-compatibilité à son homologue : la compatibilité ascendante. Celle-ci signifie qu'inclure une nouvelle addition à un langage dans un programme ne causerait pas un plantage de ce programme s'il était éxecuté par un vieux moteur JS. JS n'intègre pas ce type de compatibilité bien que beaucoup le souhaiterait et croient incorrectement que c'est le cas.

Par opposition, HTML et CSS ne sont pas rétro-compatible mais compatible ascendemment. Si vous ressortez de l'HTML ou du CSS écrit en 1995, c'est totalement possible que celui-ci ne fonctionne pas (ou fonctionne) aujourd'hui. Mais si vous utilisez une fonctionnalité datant de 2019 dans un navigateur de 2010, la page ne sera pas cassée mais le CSS/HTML non compatible ne sera pas traité quand le reste du HTML/CSS serait traité en conséquence.

Cela semble désirable d'inclure une compatibilité ascendente dans la conception d'un langage de programmation, mais c'est généralement peu pratique de le faire. La structuration (HTML) ou la stylisation (CSS) sont déclaratifs par nature donc c'est beaucoup plus facile de sauter des déclarations non reconnues avec un impact minimal sur les autres déclarations reconnues.

Mais le chaos et le non-déterminisme surviendrait si le moteur de langage de programmation sautait sélectivement des déclarations (ou même des expressions !) qu'il ne comprendrait pas comme c'est impossible d'assurer qu'une partie suivante du programme n'aurait pas besoin de la partie sauter pour fonctionner.

Bien que JS ne le soit pas et ne puisse pas être compatible ascendamment, il est primordial de reconnaitre la rétro-compatibilité JS, incluant les bénéfices durables pour le web et les contraintes et difficultés pour le JS que cela engendre.

### Jumping the Gaps

Comme JS n'est pas compatible ascendemment, cela signifie qu'il y a toujours un potentiel écart entre le code que vous écrivez qui est du JS valide et les moteurs les plus vieux que votre site ou votre application a besoin de supporter. Si vous éxecuté un programme qui utilise une fonctionnalité ES2019 dans un moteur de 2016, vous allez très certainement voir votre programme crasher.

Si la fonctionnalité est une nouvelle syntaxe, le programme échouera généralement complètement à la compilation et ne s'éxécutera pas, lançant une erreur de syntaxe. Si la fonctionnalité est une API (comme l'ES6 `Object.is(..)`), le programme pourrait se lancer pour lancer une exception pendant l'execution et stopper une fois en face de l'API inconnu.

Est-ce que cela signifie que les développeurs JS devraient toujours laguer derrière le rythme du progrès utilisant du code compatible avec les environnement de moteur JS les plus vieux dont ils ont besoin de supporter ? Non !

Mais cela signifie que les développeusr JS ont besoin de porter une attention particulière pour gérer cet écart.

Pour des nouvelles et incompatibles syntaxes, la solution est la transpilation. La transpilation est un terme inventé par la communauté pour décrire un outil qui convertie le code source du programme d'une forme vers une autre (mais toujours du code source textuel). Typiquement, les problèmes de compatibilité ascendante liés à la syntaxe sont résolus en utilisant un transpilateur (le plus commun est Babel (https://babeljs.io)) pour convertir d'une version plus récente de la syntaxe JS vers un équivalent dans une ancienne syntaxe.

Par exemple, un développeur pourrait écrire extrait de code comme :

```js
if (something) {
    let x = 3;
    console.log(x);
}
else {
    let x = 4;
    console.log(x);
}
```

Le code pourrait ressembler à ça dans l'arborescence du code source pour cette application. Mais au moment de la mise en production pour déployer sur un site public, le transpileur Babel devrait convertir ce code en quelque chose qui ressemble à ça :

```js
var x$0, x$1;
if (something) {
    x$0 = 3;
    console.log(x$0);
}
else {
    x$1 = 4;
    console.log(x$1);
}
```

L'extrait d'origine repose sur `let` pour créer une variable `x` dans un bloc de portée circonscrit aux propositions du `if` et du `else` sans interférer l'un sur l'autre. Un programme équivalent (avec un minimum de réécriture) que Babel peut produire est de juste choisir de nommer deux différentes variables avec des noms uniques produisant le même résultat sans interférence.

| NOTE: |
| :--- |
| Le mot-clé `let`a été ajouté dans ES6 (en 2015). L'exemple de transpilation qui précède serait uniquement nécessaire si une application avait besoin de se lancer dans un environnent JS pre-ES6. L'exemple est juste pour la simplicité d'illustration. Quand ES6 était nouveau, le besoin pour une telle transpilation était courant, mais en 2020, c'est beaucoup moins commun d'avoir besoin de supporter des environnements pre-ES6. La "cible" utilisée pour la transpilation est donc une fenêtre coulissante qui se déplace vers l'avant au gré des décisions prises par les sites/applications de stopper le support de tel ou tel vieux navigateur/moteur. |

Vous vous demandez pourquoi se lancer dans les problèmes d'un outil pour convertir d'une nouvelle syntaxe vers une ancienne ? Ne pourrions-nous pas juste écrire deux variables et ne pas utiliser le mot-clé `let`? La raison est qu'il est fortement recommandé aux développeurs d'utiliser la dernière version de JS pour que leur code soit propre et communique son propos plus efficacement.

Les développeurs devraient se focaliser sur l'écriture de formes propre et nouvelles et laisser les outils s'occuper de produire des versions assurant la compatibilité ascendante pour qu'il soit adapté au déploiement et à l'éxecution dans les plus vieux environnements JS

### Combler l'écart

Si le problème de la compatibilité ascendante  n'est pas lié à la nouvelle syntaxe mais plutôt à une méthode d'API manquante qui a été rajouté récemment, la solution la plus commune est de fournir une définition pour cette méthode qui remplace et se comporte comme si un plus vieil environnement l'avait déjà nativement défini. Ce modèle s'appelle un polyfill (alias "shim).

Prenons l'exemple de ce code :

```js
// getSomeRecords() returns us a promise for some
// data it will fetch
var pr = getSomeRecords();

// show the UI spinner while we get the data
startSpinner();

pr
.then(renderRecords)   // render if successful
.catch(showError)      // show an error if not
.finally(hideSpinner)  // always hide the spinner
```

Ce code utilise une fonctionnalité ES2019, la méthode `finally(..)` sur le prototype de promesse. Si ce code était utilisé dans un environnement pre-ES2019, la méthode `finally(..)` n'existerait pas et une erreur serait jetée. 

Un polyfill pour `finally(..)` dans un environnement pre-ES2019 pourrait ressembler à ça :

```js
if (!Promise.prototype.finally) {
    Promise.prototype.finally = function f(fn){
        return this.then(
            function t(v){
                return Promise.resolve( fn() )
                    .then(function t(){
                        return v;
                    });
            },
            function c(e){
                return Promise.resolve( fn() )
                    .then(function t(){
                        throw e;
                    });
            }
        );
    };
}
```

| ATTENTION: |
| :--- |
| C'est seulement une simple illustration d'un polyfill basic (pas complétement conforme à la spécification) pour `finally(..)`. N'utilisez pas ce polyfill dans votre code, utilisez toujours un polyfill solide et officiel dès que possible comme la collection de polyfills/shims dans ES-Shim. |

La déclaration `if` protège la définition du polyfill en le prévenant de s'éxecuter dans tout environnement ou le moteur JS a déjà défini cette méthode. Dans de plus vieux environnements, le polyfill est défini mais dans des environnements plus récents la déclaration du `if` est sautée silencieusement.

Les transpileurs comme Babel détecte les polyfills dont votre code a besoin et les fournit automatiquement pour vous. Mais quelques fois, vous pourriez avoir besoin de les inclure/définir  explicitement, ce qui fonctionne de la même manière que l'extrait de code que nous venons de voir.

Ecrivez toujours du code en utilisant la fonctionnalité la plus appropriée pour communiquer ses idées et son intention efficacement. En général, cela signifie utiliser les plus récentes et stables versions de JS. Evitez d'impacter négativement la lisibilité du code en essayant d'ajuster manuellement votre syntaxe ou de combler les écarts avec des API. Les outils sont là pour ça !

La transpilation et les polyfills sont deux techniques très efficaces pour gérer cet écart entre le code qui utilise les dernière fonctionnalités du langage et les vieux environnements qu'un site ou une application a besoin de supporter. Comme JS n'est pas prêt de s'arrêter de s'améliorer, cet écart ne partira jamais. Ces techniques devraient être embrassées comme un standard de toute chaine de production d'un projet JS pour aller vers l'avant.

## Qu'y a-t-il dans une Interprétation ?

Une question longuement débattue pour du code écrit en JS : s'agit-il de scripts interprétés ou d'un programme compilé ? L'opinion majoritaire semble être celle selon laquelle JS est un langage (de script) interprété. Mais la vérité est plus compliquée que ça.

Longtemps dans l'histoire des langages de programmation, les langages "interprétés" et de "script" ont été regardé de haut et jugé comme inférieur par leur homologues compilés. Les raisons de cette amertume sont nombreuses, incluant la perception selon laquelle il y a des manques dans l'optimisation des performances, l'aversion pour certaines caractéristiques de ces langages comme le fait que les langages scriptés utilisent généralement un typage dynamique au lieu d'un typage statique "plus mature".

Les langages perçus comme "compilés" produisent habituellement une représentation portable (en binaire) du programme qui est distribué pour une éxecution ultérieur. Comme on observe pas vraiment ce modèle avec JS (on distribue le code source et non sa version binaire), beaucoup déclarent éliminer JS de cette catégorie. En réalité, le modèle de distribution de la forme éxecutable d'un programme est devenue drastiquement plus varié et aussi moins pertinent au cours des dernieres décennies. Pour notre question, cela ne compte plus vraiment la forme du programme en circulation.

Ces déclarations malinformés et ses critiques devraient être mises de côté. La réelle raison qui compte pour avoir une image claire pour savoir si oui ou non JS est interprété ou compilé se base sur la nature de la façon dont les erreurs sont gérées.

Historiquement, les langages interprétés ou scriptés sont généralement executés de haut en bas et ligne par ligne. Il n'y a typiquement pas de passage initial sur le programme pour le traiter avant que son exécution commence (cf Figure 1).

<figure>
    <img src="images/fig1.svg" width="650" alt="Interpreting a script to execute it" align="center">
    <figcaption><em>Fig. 1: Interpreted/Scripted Execution</em></figcaption>
    <br><br>
</figure>

Dans les langages interprétés ou scriptés, une erreur à la ligne 5 du programme ne sera pas découverte avant que les lignes 1 à 4 ne soient exécutées. Surtout, une erreur à la ligne 5 pourrait être due a une condition à l'éxecution comme une variable ou valeur ayant une valeur non adaptée pour une opération, cela peut être aussi due a une déclaration ou une commande malformée à cette ligne. Suivant le contexte, différer la gestion d'erreur à la ligne ou l'erreur a lieu peut-être un effet désirable ou non.

Comparons ça aux langages qui font une analyse du code avant l'execution (typiquement appelé *parsing*)  comme illustré dans la figure 2 :

<figure>
    <img src="images/fig2.svg" width="650" alt="Parsing, compiling, and executing a program" align="center">
    <figcaption><em>Fig. 2: Parsing + Compilation + Execution</em></figcaption>
    <br><br>
</figure>

Dans ce modèle de traitement, une commande invalide (comme une mauvaise syntaxe) à la ligne 5 serait identifié pendant la phase d'analyse, avant que toute execution ait lieu et le programme ne serait pas lancé du tout. Pour identifié les erreurs de syntaxe (ou aussi appelée "statiques") il est généralement préféré d'en avoir connaissance en amont de toute exécution partielle condamnée.

Donc qu'ont les langages analysés en commun avec les langages compilés ? Tout d'abord, tous les langages compilés sont analysés. Donc un langage analysé est un peu déjà sur la voie d'être compilé. Dans la théorie classique de compilation, la dernière étape après l'analyse est la génération du code : produisant une forme executable.

Une fois toutes les sources du programmes complètement analysées, il est très commun que ses exécutions, d'une façon on d'une autre, inclueront une traduction depuis la forme analysé que le programme appelle un Arbre de la syntaxe abstraite (ASA) de cette forme d'exécution.

En d'autres termes, les langages analysés génèrent également généralement le code avant l'execution, donc ce n'est pas tellement de s'étirer de dire que dans l'idée, ce sont des langages compilés.

Le code source JS est analysé avant sont exécution. La spécification le requière car elle demande de déterminer et reporter les erreurs précoces - statiques, comme des duplications de nom de paramètre - avant que le code ne s'exécute. Ces erreurs ne peuvent pas être identifiées sans que le code ait été analysé.

Donc **JS est un langage analysé**, mais est-il *compilé* ?

La réponse est plus proche du oui que du non. Le JS parsé est convertie dans une forme optimisée (binaire) et ce "code" est ensuite exécuté (Figure 2). Le moteur ne repasse généralement pas par une execution ligne par ligne (commme dans la Figure 1) après avoir terminé tout le difficile travail d'analyse, cela serait trop inefficace.

Pour être précis, cette "compilation" produit un binary byte code (de toute sorte), qui est ensuite passé à une "machile virutelle JS" pour l'exécution. Certains aiment dire que cette VM "interprète" le code octal. Mais du coup, cela signifie que Java et des douzaines d'autres langages dirigés par la JVM, pour cette raison, sont interprétés plutôt que compilés. Evidemment, cela contredit l'affirmation typique selon laquelle Java/etc sont des langages compilés.

Il est intéressant de voir que malgré le fait que Java et JavaScript sont des langages très différents, la question de l'interprétation/compilation est très proche entre eux !

Un autre détail est que les moteurs JS peuvent employer plusieurs passages de JIT (Just-In-Time) traitement/optimisation sur le code généré après l'analyse qui pourrait aussi être labelisé aussi bien de compilation que d'intérpétation en fonction du point de vue. C'est en fait une situation fantastiquement complexe sous le capot du moteur JS.

Alors quid de ces petits détails ? Prenons un pas de recul et considérons la totalité de l'écoulement d'un programme source JS :

1. Après qu'un programme ait quitté l'éditeur d'un développeur, il est transpilé par Babel, empaqueté par Webpack (et potentiellement une demi douzaine d'autre processus de construction) puis il est délivré dans cette forme bien différente au moteur JS.
2. Le moteur JS analyse le code vers un ASA
3. Le moteur convertie l'ASA dans une sorte de code octal, un représentation binaire intermédiaire (IR) qui est convertie/affinée encore plus par l'optimisant compilateur JIT.
4. Finalement la machine virtuelle JS exécute le programme

Pour visualiser de nouveau ces étapes :

<figure>
    <img src="images/fig3.svg" width="650" alt="Steps of JS compilation and execution" align="center">
    <figcaption><em>Fig. 3: Parsing, Compiling, and Executing JS</em></figcaption>
    <br><br>
</figure>

Est-ce que JS est géré davantage comme un langage interprété ligne par ligne comme dans la Figure 1 ou est est-il plus proche d'un langage compilé traité par un ou plusieurs passages avant exécution (comme dans les Figures 2 et 3) ?

Je pense qu'il est clair que dans l'esprit, si ce n'est dans la pratique, **JS est un langage compilé**.

Et de nouveau, la raison qui compte, comme JS est compilé, nous sommes informés des erreurs statiques (comme les erreurs de syntaxes) avant que le code soit exécuté. C'est un modèle d'interaction substantiellement différent que l'on a avec les programmes scriptés et sans doute plus utile !

### Web Assembly (WASM)

Une préoccupation dominante qui a conduit un grand nombre d'évolution du JS est la performance, aussi bien concernant la vitesse à lquelle le JS peut être  analysé/compilé que la vitesse à laquelle ce code compilé peut-être éxécuté.

En 2013, des ingénieurs de Mozilla Firefox ont fait une démonstration d'un portage du moteur de jeu Unreal 3 de C vers JS. La capacité pour ce code d'être exécutable dans le moteur JS d'un navigateur à 60fps affirmait un jeu d'optimisations que le moteur JS pourrait réaliser spécifiquement car la version JS du code du moteur Unreal utilisait un style de code qui favorisait un sous-ensemble du langage appelé "ASM.js".

Ce sous-ensemble est du JS valide écrit d'une manière peu commune pour du code normal mais qui spécifie certaines informations de typage important au moteur qui lui permettent de réaliser des optimisations clés. ASM.js a été introduit comme une façon d'aborder les pressions sur les performances à l'execution du JS.

Cependant il est important de noter que l'ASM.js n'a jamais été prévu pour être codé par des développeurs mais plutôt d'être une représentation d'un programme transpilé depuis un autre langage (comme le C) où ces annotations de typage étaient insérées automatiquement par l'outil.

Plusieurs années après qu'ASM.js ait démontré la validité de créer des versions de programme via les outils pour être traité plus efficacement par le moteur JS, un autre groupe d'ingénieurs (provenant aussi initialement de Mozilla) ont sorti le Web Assembly (WASM).

WASM est similaire à ASM.js car son idée de départ est de fournir un chemin pour des programmes non JS (C, etc) pour être converti vers une forme qui pourrait être exécutée par un moteur JS. Contrairement à ASM.js, WASM a aussi choisi d'aborder certains des délais inhérents au parsing/compilation avant que le programme ne s'execute en représentant le programme dans une forme qui est entièrement différente du JS.

WASM est un format beaucoup plus proche de l'assembleur (d'où son nom) qui peut être traité par le moteur JS en sautant l'analyse/compilation que le moteur JS réalise normalement. L'analyse/compilation d'un programme en WASM se passe en avance de phase (AOT). Ce qui est distribué est un programme emballé en binaire prêt à être exécuté avec un minimum de traitement pour le moteur JS.

La motivation initiale pour WASM était clairement de potentiellement améliorer les performances. Alors que cela continue d'être un sujet, WASM est additionnelement motivé par le désir d'apporter plus de parité aux langages non JS vers les plateformes web. Par exemple, si un langage comme Go supporte la threaded programming alors que le JS ne le peut pas, WASM offre le potentiel pour un tel programme en Go d'être converti dans une forme que le moteur JS peut comprendre sans avoir besoin d'une fonctionnalité de threading dans le langage JS en lui même.

En d'autres temres, WASM soulage la pression d'ajouter de nouvelles fonctionnalités au JS qui sont majoritairement/exclusivement destinées à être utilisées par des programmes transpilés depuis d'autres langages. Cela signifie que le développement des fonctionnalités JS peut être jugé (par le TC39) sans être biaisé par les demandes et intérêts des écosystèmes des autres langages tout en permettant à ces langages d'avoir un chemin viable vers le web.

Une autre perspective qui émerge avec le WASM n'est pas directement lié au web (W). WASM est en train d'évoluer pour devenir une sorte de machine virtuelle multi-plateforme où les programmes peuvent être compilés une fois puis lancés dans une variété de différents environnements systèmes.

Donc WASM n'est pas seulement pour le web et WASM n'est pas non plus du JS. Ironiquement, même si WASM s'exécute dans le moteur JS, le langage JS est l'un des moins approprié pour sourcer des programmes WASM, car WASM repose lourdement sur des informations de typage statique. Même TypeScript (TS) - ostensiblement JS + du typage static - n'est pas bien approprié (tel qu'il est) pour être transpilé en WASM, bien que des variantes du langage comme AssemblyScript tentent de réduire l'écart entre JS/TS et WASM.

Ce livre ne porte pas sur WASM donc je ne vais pas passer trop de temps à l'aborder, excepté pour mon point final. *Certains* ont suggéré que WASM pointe vers un futur où JS est retiré, ou minimisé, du web. Ces personnes sont malades du JS et veulent n'importe quel langage pour le remplacer ! Comme WASM permet à d'autres langages d'etre exécuté par le moteur JS, ce n'est pas tellement un conte de fées fantaisiste.

Mais laissez moi juste déclarer : WASM ne remplacera pas JS. WASM augmente significativement ce que le web (JS inclus) peut accomplir. C'est une super chose, complètement indépendante de si oui non les gens l'utiliseratont pour s'échapper de l'obligation d'écrire du JS.

## Parlons *strict*

En 2009 avec la sortie de l'ES5, JS a ajouté le *mode strict* comme un méchanisme pour ecourager le développement de meilleurs programmes JS.

Les bénéfices du mode strict dépasse largement son cout, mais les vieilles habitudes ont du mal à disparaitre et l'inertie de codes existant (alias "legacy") est très difficile à changer. Donc malheureusement, plus de 10 ans plus tard, l'optionnalité du mode strict montre qu'il n'est toujours pas nécessairement la base des développeurs JS. 

Pourquoi le mode strict ? Le mode strict ne devrait pas être pensé comme une restriction de ce que vous pouvez ou ne pouvez pas faire mais plutôt comme un guide de la meilleure façon de faire pour que le moteur JS ait la meilleure chance d'optimiser efficacement l'éxecution du code. La plupart du code JS es réalisé par des équipes de développeurs, donc la *strictivité* du mode strict (avec les outils comme les linters !) sont souvent des aides à la collaboration sur le code pour éviter des erreurs problématiques qui peuvent se glisser sans le mode strict.

La plupart des contrôles du mode strict prennent la forme d'*erreurs précoces*, signifiant que ces erreurs ne son pas strictitement des erreurs de syntaxe mais sont quand même lancé au moment de la compilation (avant que le code soit exécuté). Par exemple, le mode strict n'autorise pas d'avoir deux paramètres de fonctions du même nom, et mène à une erreur précoce. Quelques autres contrôles du mode strict s'observent uniquement à l'exécution comme le fait que le `this` se définisse par défaut comme `undefined` plutôt que dans l'objet global.

Plutôt que de se battre et d'argumenter avec le mode strict, comme un enfant qui veut juste défier ce que ses parents lui disent, le meilleur état d'esprit est de percevoir le mode strict comme un linter qui vous rappelle comment le JS *devrait* être écrit pour avoir la meilleure qualité et la meilleur chance d'être performant. Si vous vous sentez menoté, essayant de contourner le mode strict, cela devrait être un drapeau rouge d'avertissement comme quoi vous devez revenir en arrière et repenser votre approche dans sa globalité.

Le mode strict est activé par fichier via un pragma special (rien n'est autorisé avant à l'exception des commentaires et des espaces) :

```js
// only whitespace and comments are allowed
// before the use-strict pragma
"use strict";
// the rest of the file runs in strict mode
```

| ATTENTION: |
| :--- |
| Il faut savoir que même un `;` perdu seul avant le pragma du mode strict le rendra inutile. Aucunes erreurs ne seront lancées car il s'agit de JS valide d'avoir l'expression d'une chaine littérale dans une poistion de déclaration mais cela n'allumera silencieusement pas le mode strict !  |

Le mode strict peut aussi être activé dans la portée d'une fonction, avec exactement les même règles :

```js
function someOperations() {
    // whitespace and comments are fine here
    "use strict";

    // all this code will run in strict mode
}
```

C'est intéressant de noter que si un fichier a le mode strict activé, les pragmas de mode strict dans les fonctions ne sont pas autorisé. Donc vous devez choisir l'un ou l'autre.

La **seule** bonne raison d'utiliser une approche par fonction est quand vous convertissez un fichier de programme non strict que vous voulez changer petit bout par petit bout dans le temps. Sinon, c'est largement mieux de simplement activer le mode strict pour la totalité du fichier/programme.

Beaucoup se sont demander s'il y aurait un moment où JS activerait le mode strict par défaut ? La réponse est, presque certainement non. Comme nous l'avons discuté plutôt à propose de la rétrocompatibilité, si une mise à jour de moteur JS considère que le mode strict est activé par défaut, même s'il n'est pas inscrit comme tel, il est possible que le code casse en raison des controles apportés par le mode strict.

Cependant, il y a quelques facteurs qui réduisent le futur impact de cette décision de ne pas activer le mode strict par défaut.

D'abord car tous le code virtuellement transpilé fini en mode strict même si la source du code ne le spécifie pas. La plupart du code JS produit est transpilé cela signifie donc que la plupart du JS adhère déjà au mode strict. Il est possible de défaire ce paramétrage mais vous devrez vraiment le vouloir donc c'est assez peu problable.

De plus, un vaste changement est en train d'arriver envers la plupart de nouveau code JS écrit en utilisant le format des modules ES6. Les modules ES6 présuppose que le mode strict est activé donc tout le code de ces fichiers est automatiquement en mode strict par défaut.

Pris ensemble, le mode strict est donc largement activé de facto par défaut même si techniquement il ne l'est pas réellement.

## Défini

JS est une implémentation du standard ECMAScript (Au moment d'écrire ces lignes, à la version ES2019), qui est guidé par le comité du TC39 et hébergé par ECMA. Il est exécuté dans les navigateurs et les environnements JS tels que Node.js.

JS est un langage multi-paradigme, signifiant que la syntaxe et ses possibilités permettent au développeurs de mixer, d'harmoniser (de se plier ou de reformer) des concepts provenant de différents paradigmes majeurs comme le procédural, l'orienté objet et le fonctionnel.

Js est un langage compilé, signifiant que les outils (incluant le moteur JS) traiter et vérifie le programme (rapportant les erreurs !) avant son exécution.

Avec notre langage *défini*, lançons nous dans la découverte de ses tenants et aboutissants.

[^specApB]: ECMAScript 2019 Language Specification, Appendix B: Additional ECMAScript Features for Web Browsers, https://www.ecma-international.org/ecma-262/10.0/#sec-additional-ecmascript-features-for-web-browsers (latest as of time of this writing in January 2020)
