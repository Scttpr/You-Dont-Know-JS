# Vous ne connaissez pas encore JS : Débuter - 2nd Edition
# Chapitre 3: Creuser jusqu'aux racines du JS

Si vous avez lu les chapitres 1 et 2 et pris le temps de les digérer un peu vous commencez probablement à *capter* JS un peu plus. Si vous les avez sauté ou survolé (surtout le chapitre 2), je vous recommence de revenir en arrière et de passer du temps sur ce matériau.

Dans le chapitre 2 nous avons arpenter la syntaxe, les modèles et les comportements à un haut niveau. Dans ce chapitre, notre attention portera plutôt vers les racines bas-niveau des caractéristiques du JS qui soutiennent chaque ligne de code écrite.

Attention : ce chapitre creuse plus profondément dans le langage que ce dont vous avez l'habitude de voir en programmation. Mon but est de vous aider à apprécier le coeur du fonctionnement de JS, ce qui marque. Ce chapitre devrait commencer par la réponse à quelques "Pourquoi ?" qui ont peut-être émergées au gré de votre exploration du JS. Cependant, ce contenu n'est pas une présentation exhaustive du langage (l'ensemble des autres livres est là pour ça !). Notre but ici est de juste *débuter* pour devenir plus confortable avec le langage et son rythme, son comportement.

Ne courrez pas trop vite à travers ce contenu pour ne pas vous y perdre. Comme je l'ai déjà dit, **prenez votre temps**. Même ainsi vous allez probablement terminer ce chapitre avec des questions en suspend. Ce n'est pas grave car il y a toute la série de livre devant vous qui n'attendent que vous !

## Itération

Comme les programmes sont essentiellement construits pour traiter des données (et prendre des décisions sur ces données), les modèles utilisés pour le traitement ont un gros impact sur la lisibilité des programmes.

Le modèle itérateur est présent depuis des décennies et suggère une approche standardisée pour consommer les données depuis une source un *chunk* à la fois. L'idée est qu'il est plus commun et pratique d'itérer la source de données pour progressivement gérer la collection de donnée en traitant la première partie, puis la suivante, etc. plutôt que de traiter tout l'ensemble en même temps.

Imaginez une structure de donnée qui représente une requête `SELECT` d'une base de données relationnelle qui, organise généralement les résultats en lignes. Si la requête avait une seule ou quelques lignes, vous pourriez traiter le résultat en une seule fois et assigner chaque ligne à une variable locale et réaliser quelques opérations appropriées sur ces données.

Mais si la requête avait 100, 1000 (ou plus !) lignes, vous aurez besoin d'un traitement itératif pour traiter les données (généralement une boucle).

Le modèle itérateur définit une structure de donnée appelée un "itérateur" qui possède une référence à une source de données (comme les lignes du résultat de la requête) qui expose une méthode comme `next()`. `next()` retourne la prochaine donnée (c'est-à-dire un "enregistrement" ou une "ligne" de la requête de base de données).

Vous ne savez pas toujours combien de fois vous aurez besoin d'itérer une donnée donc le modèle indique généralement la fin du traitement par une valeur spécifique ou une exception une fois l'ensemble traité et la fin dépassée.

L'importance du modèle itérateur est dans l'adhésion à une façon *standard* de traiter la donnée itérativement qui crée une façon plus propre et simple de comprendre le code plutôt que d'avoir une façon de traiter chaque source/structure de données différemment.

Après de nombreuses années de différents efforts de la communauté JS autour d'une technique d'itération approuvée mutuellement, l'ES6 a standardisé un protocol spécifique pour le modèle itérateur directement dans le langage. Le protocole définit une méthode `next()` qui retourne un objet appelé *résultat d'itérateur*. Cet objet à les propriétés `value` et `done`, un booléen qui vaut `false` jusqu'à ce que l'itération soit complète.

### Consommer les itérateurs

Avec le protocole d'itération mis en place par l'ES5, il est possible de traiter une source de données valeur par valeur, vérifiant après chaque appel `next()` si la valeur de `done` est `true` pour stoper l'itération. Cependant cette approche est plutôt manuelle, donc ES6 inclue plusieurs mécanismes (syntaxiques et des APIs) pour standardiser la consommation de ces itérateurs.

L'un de ces mécanisme est la boucle `for..of` :

```js
// given an iterator of some data source:
var it = /* .. */;

// loop over its results one at a time
for (let val of it) {
    console.log(`Iterator value: ${ val }`);
}
// Iterator value: ..
// Iterator value: ..
// ..
```

| NOTE: |
| :--- |
| Nous allons omettre la boucle manuelle équivalente ici mais elle est définitivement moins lisble que la boucle `for..of` |

Un autre mécanisme souvent utilisé pour consommer des itérateurs est l'opérateur `...`. Cet opérateur possède deux formes symétriques : *spread* et *rest* (ou collecter, comme je préfère). La forme *spread* est un consommeur d'itérateur.

Pour *spread* un itérateur, vous devez avoir quelque chose à *spread* dedans. Il y a deux possibilités en JS : un tableau ou une liste d'arguments dans un appel de fonction.

Un *spread* de tableau :

```js
// spread an iterator into an array,
// with each iterated value occupying
// an array element position.
var vals = [ ...it ];
```

Un *spread* d'appel de fonction :

```js
// spread an iterator into a function,
// call with each iterated value
// occupying an argument position.
doSomethingUseful( ...it );
```

Dans les deux cas, la forme de  `...` suit le protocole de consommation d'itérateur (comme la boucle `for..of`) pour retrouver toutes les valeurs disponibles depuis un itérateur pour les placer (alias *spread*) dans le contexte à la réception (tableau, liste d'arguments).

### Itérables

Le protocole de consommation d'itérateur est techniquement défini pour consommer des *itérables*, c'est-à-dire une valeur qui peut-être itérée.

Le protocole crée automatiquement une instance d'itérateur depuis un itérable et consommes *juste cette instance* jusqu'à sa complétion. Cela signifie qu'un seul itérable peut-être consommer plus d'une fois. A chaque fois, une nouvelle instance de l'itérateur sera créée et utilisée.

Où trouve-t-on les itérables ?

ES6 définie la structure/collection des types de données basiques comme des itérables. Cela inclut les *strings*, les tableaux, les *maps*, les *sets*, etc.

Considérez :

```js
// an array is an iterable
var arr = [ 10, 20, 30 ];

for (let val of arr) {
    console.log(`Array value: ${ val }`);
}
// Array value: 10
// Array value: 20
// Array value: 30
```
Comme les tableaux sont des itérables, nous pouvons faire une copie superficielle du tableau en consommant l'itérateur via l'opérateur de *spread* `...` :

```js
var arrCopy = [ ...arr ];
```

Nous pouvons aussi itérer les caractères dans une *string* un par un :

```js
var greeting = "Hello world!";
var chars = [ ...greeting ];

chars;
// [ "H", "e", "l", "l", "o", " ",
//   "w", "o", "r", "l", "d", "!" ]
```

Une structure de donnée `Map` utilise des objets comme clés, associant une valeur (de n'importe quel type) a un objet. Les *Maps* ont une itération par défaut différente que celle vue jusque là dans le sens où cette itération ne se fait pas seulement sur chacune de ses valeurs mais plutôt sur chaque *entrées*. Une *entrée* est un *tuple* (un tableau de deux éléments) incluant à la fois la clé et la valeur.

Considérez :

```js
// given two DOM elements, `btn1` and `btn2`

var buttonNames = new Map();
buttonNames.set(btn1,"Button 1");
buttonNames.set(btn2,"Button 2");

for (let [btn,btnName] of buttonNames) {
    btn.addEventListener("click",function onClick(){
        console.log(`Clicked ${ btnName }`);
    });
}
```

Dans la boucle `for..of` sur l'itération par défaut du *map*, on utilise la syntaxe `[btn,btnName]` (appellée "déstructuration de tableau") pour casser chaque *tuple* consommé en une paire clé/valeur (`btn1` / `"Button 1"` et `btn2` / `"Button 2"`).

Chacun des itérateurs intégrés à JS expose une itération par défaut qui devrait probablement correspondre à votre intuition. Cependant vous pouvez aussi choisir une itération spécifique si nécessaire. Par exemple, si nous voulons consommer seulement les valeurs sur le *map* `buttonNames`, nous pouvons appeler `values()` pour avoir un itérateur uniquement sur les valeurs :

```js
for (let btnName of buttonNames.values()) {
    console.log(btnName);
}
// Button 1
// Button 2
```

Ou si nous voulions l'index et la valeur sur une itération de tableau, on pourrait utiliser un itérateur d'entrées avec la méthode `entries()` :

```js
var arr = [ 10, 20, 30 ];

for (let [idx,val] of arr.entries()) {
    console.log(`[${ idx }]: ${ val }`);
}
// [0]: 10
// [1]: 20
// [2]: 30
```

Pour la majeure partie, tous les itérateurs intégrés dans JS ont trois formes d'itérateurs possible : clés seules (`keys()`), valeurs seules (`values()`), et entrées (`entries()`).

Au delà des itérateurs intégrés, vous pouvez aussi vous assurer que votre structure de données adhère au protocole d'itération. Se faisant vous optez pour la possibilité de consommer votre donnée avec la boucle `for..of` ou l'opérateur `...`. "Standardiser" sur le protocole signifie que votre code est dans l'ensemble plus lisible.

| NOTE: |
| :--- |
| Vous avez peut-être remarqué un changement nuancé dans cette présentation. Nous avons commencé à parler de consommation **d'itérateurs** pour ensuite parler d'itération sur des **itérables**. Le protocole de consommation d'itération a besoin d'un *itérable* mais la raison pour laquelle nous pouvons fournir directement un *itérateur* est qu'un itérateur est juste un itérable de lui même ! Quand on crée une instance d'itérateur depuis un itérateur existant, l'itérateur lui même est retourné. |

## Closure

Sans doute sans s'en rendre compte, presque tous les développeurs JS ont utilisé des *closures*. En fait, la *closure* est l'une des fonctionnalités de programmation les plus répandues dans une majorité de langages. C'est peut-être même aussi important à comprendre qu'une variable ou une boucle. C'est aussi fondamental que ça.

Pourtant cela semble caché, presque magique et c'est souvent abordé de façon très abstraite ou dans des termes très informels qui n'aident pas plus que ça à comprendre ce que c'est.

Nous devons être capable de reconnaître quand une *closure* est utilisée dans les programmes comme le manque de présence de *closure* cause parfois des bugs (ou des problèmes de performances).

Définissons concrètement une *closure* de façon pragmatique :

> Une *closure* est quand une fonction se souvient et continue d'accéder aux variables provenant des portées extérieures même quand cette fonction est éxécutée dans une portée différente.

Nous identifions deux caractéristiques différentes ici. D'abord que la *closure* fait partie de la nature d'une fonction. Les objets n'ont pas de *closures*, les fonctions oui. Deuxièmement, pour observer une *closure*, il faut éxécuter une fonction dans une portée différente de là où elle a été originellement définie.

Considérez :

```js
function greeting(msg) {
    return function who(name) {
        console.log(`${ msg }, ${ name }!`);
    };
}

var hello = greeting("Hello");
var howdy = greeting("Howdy");

hello("Kyle");
// Hello, Kyle!

hello("Sarah");
// Hello, Sarah!

howdy("Grant");
// Howdy, Grant!
```

D'abord la fonction extérieure `greeting(..)` est éxécutée, créant une instance de la fonction intérieure `who(..)`. Cette fonction ferme sur la variable `msg` qui est le paramètre provenant de la fonction extérieure `greeting(..)`. Quand la fonction intérieure est retournée, sa référence est assignée à la variable `hello` dans la portée extérieure. Ensuite nous appelons `greeting(..)` une deuxième fois, créant une nouvelle instance de la fonction intérieure avec une nouvelle *closure* sur une nouveau `msg` et retourne cette référence pour être assignée à `howdy`.

Quand la fonction `greeting(..)` termine son éxécution, nous devrions normalement nous attendre à ce que toutes ses variables soient ramassées (retirées de la mémoire). Nous devrions nous attendre à ce que chaque `msg` s'en aille, mais en fait non. La raison est la *closure*. Comme les instances de la fonction intérieure sont toujours en vie (assignées respectivement à `hello` et `howdy`), leurs *closures* préservent toujours les variables `msg`.

Ces *closures* ne sont pas des instantanés de la valeur de la variable `msg`, elles sont un lien direct et préservé de la variable elle même. Cela signifie que la *closure* peut réellement observer (ou faire !) des mises à jour de ces variables dans le temps.

```js
function counter(step = 1) {
    var count = 0;
    return function increaseCount(){
        count = count + step;
        return count;
    };
}

var incBy1 = counter(1);
var incBy3 = counter(3);

incBy1();       // 1
incBy1();       // 2

incBy3();       // 3
incBy3();       // 6
incBy3();       // 9
```

Chaque instance de la fonction intérieure `increaseCount()` est fermée sur les variables `count` et `step` provenant de la portée de la fonction extérieure `counter(..)`. `step` reste le même dans le temps mais `count` est mis à jour à chaque appel de cette fonction intérieure. Comme la *closure* se fait sur les variables et n'est pas seulement un instantané des valeurs, ces mises à jour sont préservées.

Les *closures* sont communes quand on travaille avec du code asynchrone comme avec les *callbacks*, considérez :

```js
function getSomeData(url) {
    ajax(url,function onResponse(resp){
        console.log(
            `Response (from ${ url }): ${ resp }`
        );
    });
}

getSomeData("https://some.url/wherever");
// Response (from https://some.url/wherever): ...
```

La fonction intérieure `onResponse(..)` est fermée sur `url` et donc la préserve et s'en souvient jusqu'à ce que l'appel Ajax retourne et éxécute `onResponse(..)`. Bien que `getSomeData(..)` termine son éxécution immédiatement, le paramètre `url` est gardé en vie dans la *closure* tant qu'on en a besoin.

Ce n'est pas nécessairement que la portée extérieure est une fonction même si c'est souvent le cas, il faut juste une variable d'une portée extérieure accessible et utilisée dans une fonction intérieure :

```js
for (let [idx,btn] of buttons.entries()) {
    btn.addEventListener("click",function onClick(){
       console.log(`Clicked on button (${ idx })!`);
    });
}
```
 Parce que cette boucle utilise la déclaration `let`, chaque itération a des variables `idx` and `btn`  avec une nouvelle portée de bloc (alias locale). La boucle crée aussi une nouvelle fonction intérieure `onClick(..)` à chaque fois. Celle-ci ferme sur `idx`, la préservant ainsi aussi longtemps que le gestionnaire de clic est en place sur le `btn`. Donc quand chacun des boutons est cliqué, son contrôleur peut affichier la valeur index associée car il se souvient de sa variable `idx`.

Souvenez vous : cette *closure* ne se fait pas sur la valeur (like `1` or `3`) mais sur la variable `idx` elle-même.

La *closure* est l'un modèle de programmation les plus importants quel que soit le langage. C'est spécialement vrai en JS où il est difficile de penser pouvoir faire quelque chose d'utile sans tirer partie des *closures* d'une façon ou d'une autre.

Si vous vous sentez toujours incertain et troublé par les *closures*, la majorité du livre 2, *Scope & Closures* est focalisé sur cette question.

## `this` Keyword

L'un des mécanismes les plus puissants du JS est aussi l'un des moins bien compris : le mot-clé `this`. Une incompréhension commune repose dans le fait que le `this` d'une fonction fait référence à la fonction elle-même. En raison de la façon dont le `this` fonctionne dans d'autres langages, une autre incompréhension repose dans le fait que `this` pointe vers une instance à laquelle une méthode appartient. Les deux sont incorrectes.

Comme présenté précédemment, quand une fonction est définie, elle est *attachée* à sa portée englobante via la *closure*. La portée est l'ensemble des règles qui controlent la façon dont les références aux variables sont résolues.

Mais les fonctions ont aussi une autre caractéristique en plus de leur portée qui influence ce à quoi elles ont accès. Cette caractéristique est ce qu'on pourrait appeler un *contexte d'éxécution* et il est exposé à la fonction via son mot-clé `this`.

La portée est statique et contient un ensemble fixe de variables à disposition au moment et l'endroit où vous l'avez définie, mais le contexte d'éxécution est dynamique, entièrement dépendant de **la façon dont elle est appelée** (quel que soit l'endroit où elle a été définie ou appelée).

`this` n'est pas une caractéristique fixe d'une fonction basée sur sa définition mais plutôt une caractéristique dynamique déterminée à chaque fois que la fonction est appelée.

Une façon de voir le contexte d'éxécution est de se le représenter comme un objet dont les propriétés sont rendues disponible à une fonction au moment où elle s'éxécute. Comparé à la portée, qui peut également être perçue comme un objet - sauf que celui-ci serait caché dans le moteur JS - mais qui est toujours la même pour cette fonction et ses propriétés prennent la forme de variables disponibles dans la fonction.

```js
function classroom(teacher) {
    return function study() {
        console.log(
            `${ teacher } says to study ${ this.topic }`
        );
    };
}
var assignment = classroom("Kyle");
```

La fonction extérieure `classroom(..)` ne fait pas référence au mot-clé `this` donc elle est similaire aux fonctions vues jusqu'à maintenant. Par contre, la fonction intérieure` study()` référence `this` ce qui en fait une fonction consciente du `this`. En d'autres termes, c'est une fonction dépendante de son contexte d'éxécution.

| NOTE: |
| :--- |
| `study()` est aussi fermée sur la variable `teacher`. |

La fonction intérieure `study()` retournée par `classroom("Kyle")` est assignée à la variable `assignment`. Donc comment `assignment()` (alias `study()`) peut-être appelée ?


```js
assignment();
// Kyle says to study undefined  -- Oops :(
```

Dans cet extrait, on appelle `assignment()` comme une fonction classique, sans fournir de contexte d'éxécution.

Comme le programme n'est pas en mode strict (voir le chapitre 1, "Strictly Speaking"), les fonctions consciente du contexte qui sont appelées sans le spécifier définissent l'objet global comme contexte par défaut (`window` dans un navigateur). Comme il n'y a pas de variable globale nommée `topic` (et donc pas de telle propriété dans l'objet global), `this.topic` est résolu en `undefined`.
In this snippet, we call `assignment()` as a plain, normal function, without providing it any *execution context*.

Maintenant considérez :

```js
var homework = {
    topic: "JS",
    assignment: assignment
};

homework.assignment();
// Kyle says to study JS
```

Une copie de la référence de la fonction `assignment` est définie comme une propriété de l'objet `homework` et est ensuite appelée `homework.assignment()`. Cela signifie que `this` pour cet appel de fonction sera l'objet `homework`. Ainsi, `this.topic` se résoud en `"JS"`.

Enfin :

```js
var otherHomework = {
    topic: "Math"
};

assignment.call(otherHomework);
// Kyle says to study Math
```

Une troisième façon d'invoquer une fonction est avec la méthode `call(..)` qui prend un objet (`otherHomework` ici) pour utiliser comme paramètre la référence `this` pour cet appel. La référence de propriété `this.topic` est résolue en `"Math"`.

La même fonction consciente de son contexte est invoquée de trois façons différentes et donne des réponses différentes à chaque fois en fonction de l'objet auquel fait référence le `this`

Le bénifice de ces fonctions est la faculté à être plus flexible et d'être réutilisée avec des données de différents objets. Une fonction qui ferme sur une portée ne peut jamais faire référence à une portée différente ou un ensemble de variables. Mais une fonction qui a un `this` dynamique conscient de son contexte peut-être très utile pour certaines tâches.

## Prototypes

Là où `this` est une caractéristique de l'éxécution de la fonction, un prototype est une caractéristique d'un objet et plus spécifiquement la résolution de l'accès à une propriété.

Pensez au prototype comme un lien entre deux objets caché en arrière-plan même s'il est possible de l'exposer et de l'observer. Ce lien se fait au moment où l'objet est créé, il est lié avec un autre objet qui existe déjà.

Une série d'objets liés ensemble via des prototypes s'appelle une "chaîne de prototype".

L'objectif de ce lien (par exemple d'un objet B vers un autre objet A) est que les accès à B pour les propriétés/méthodes que B n'a pas sont *délégués* à A. La délégation d'accès d'une propriété/méthode autorise deux (ou plus !) objets à coopérer l'un avec l'autre pour réaliser une tâche.

Considérez définir un objet comme un litéral normal :

```js
var homework = {
    topic: "JS"
};
```

L'objet `homework` a seulement une seule propriété : `topic`. Cependant, son lien de prototypage par défault se connecte à l'objet `Object.prototype` qui intègre des méthodes communes comme `toString()` et `valueOf()`, entre autres.

On peut observer la délégation du lien de prototypage de `homework` à `Object.prototype` :

```js
homework.toString();    // [object Object]
```
`homework.toString()` fonctionne même si `homework` n'a pas de méthode `toString()` définie. La délégation appelle en fait `Object.prototype.toString()`.

### Liaison d'objets

Pour définir une liaison de prototype d'objet, vous pouvez créer un objet en utilisant l'utilitaire `Object.create(..)` :

```js
var homework = {
    topic: "JS"
};

var otherHomework = Object.create(homework);

otherHomework.topic;   // "JS"
```

Le premier argument de `Object.create(..)` spécifie un objet à lier au nouvel objet, la méthode retourne ensuite le nouvel (et lié) objet.

La figure 4 montre comment les trois objets (`otherHomework`, `homework`, et `Object.prototype`) sont liés dans la chaîne de prototype :

<figure>
    <img src="images/fig4.svg" width="200" alt="Prototype chain with 3 objects" align="center">
    <figcaption><em>Fig. 4: Objects in a prototype chain</em></figcaption>
    <br><br>
</figure>

La délégation au sein de la chaîne s'applique uniquement pour les accès 

La délégation via la chaîne de prototypes s'applique uniquement aux accès pour rechercher la valeur dans une propriété. Si vous attribuez à une propriété d'un objet, cela s'appliquera directement à l'objet indépendamment de l'endroit où cet objet est lié au prototype.

| TIP: |
| :--- |
| `Object.create(null)` crée un objet qui est lié à aucune liaison de prototypes, c'est purement un objet autonome. Dans certaines circonstances, cela peut-être préférable. |

Considérez :

```js
homework.topic;
// "JS"

otherHomework.topic;
// "JS"

otherHomework.topic = "Math";
otherHomework.topic;
// "Math"

homework.topic;
// "JS" -- not "Math"
```

L'affectation de `topic` crée une propriété de ce nom directement dans `otherHomework`, il n'y a aucun effet sur la propriété `topic` dans `homework`. La prochaine déclaration accède à `otherHomework.topic` et on voit que la réponse est la nouvelle propriété : `"Math"`.

La figure 5 montre les objets/propriétés après l'affectation qui crée la propriété `otherHomework.topic` :

<figure>
    <img src="images/fig5.svg" width="200" alt="3 objects linked, with shadowed property" align="center">
    <figcaption><em>Fig. 5: Shadowed property 'topic'</em></figcaption>
    <br><br>
</figure>

Le `topic` dans `otherHomework` est *shadowing* la propriété du même dans l'objet `homework` de la chaîne.
The `topic` on `otherHomework` is "shadowing" the property of the same name on the `homework` object in the chain.

| NOTE: |
| :--- |
| Une autre façon franchement plus compliquée mais peut-être encore plus courante de créer un objet avec une liaison de prototype est d'utiliser le modèle de "classe prototypique", d'avant que "classe" (voir Chapitre 2, "Classes") ait été ajouté dans ES6. Nous aborderons ce sujet plus en détail dans l'annexe A, «Classes prototypiques». |

### `this` revisité

Nous avons abordé le mot-clé `this` plus tôt mais sa vrai importance brille quand on considère comment il alimente les appels de fonctions délégués par prototype. En effent, l'une des raisons principales qui font que `this` supporte un contexte dynamique repose sur la façon dont la fonction est appelée est telle que la méthode fait appel à des objets qui délèguent à travers la chaîne de prototype et maintiennent toujours le `this` attendu.

Considérez :

```js
var homework = {
    study() {
        console.log(`Please study ${ this.topic }`);
    }
};

var jsHomework = Object.create(homework);
jsHomework.topic = "JS";
jsHomework.study();
// Please study JS

var mathHomework = Object.create(homework);
mathHomework.topic = "Math";
mathHomework.study();
// Please study Math
```

Les deux objets `jsHomework` et `mathHomework` sont tout deux liés à l'objet `homework` qui comporte la fonction `study()`. `jsHomework` et `mathHomework` donnent tous les deux leur propre valeur à la propriété `topic` (voir la figure 6).

<figure>
    <img src="images/fig6.svg" width="495" alt="4 objects prototype linked" align="center">
    <figcaption><em>Fig. 6: Two objects linked to a common parent</em></figcaption>
    <br><br>
</figure>

`jsHomework.study()` délègue à `homework.study()` mais son `this` (`this.topic`) pour cette éxécution est résolu par `jsHomework` en raison de la façon dont la fonction est appelée, `this.topic` est `"JS"`. 

L'extrait de code ci-dessus serait beaucoup moins utile si `this` était résolu par `homework`. Pourtant, dans plein d'autres langages, il semblerait que `this` serait `homework` car la méthode `study()` est en effet définie par `homework`.

Contrairement à beaucoup d'autres langages, le fait que le `this` de JS soit dynamique est un élément essentiel autorisant la délégation de prototypes (et en effet la `class`) à fonctionner comme prévu !

## Se demander "pourquoi ?"

Le but de ce chapitre était de montrer qu'il y en a beaucoup plus sous le capot du JS qu'on pourrait le croire au premier coup d'oeil.

Alors que vous continuer de débuter en apprenant et en connaissant JS de plus en plus, l'une des compétences les plus importante que vous pouvez pratiquer est la curiosité, l'art de demander "Pourquoi ?" quand vous rencontrer quelque chose dans un langage.

Même si ce chapitre est allé assez loin sur certains points, de nombreux détails ont été survolés. Il y a bien plus à apprendre ici et le début du chemin commence par votre capacité à poser la bonne question sur votre code. Se poser la bonne question est une compétence essentielle pour devenir un meilleur développeur.

Dans le dernier chapitre de ce livre, nous allons brièvement regarder la façon dont JS est divisé et abordé dans le reste des livres de la série. Aussi, ne sauter pas l'annexe B de ce livre qui contient de la mise en pratique pour revoir certains des sujets abordés dans ce livre.
