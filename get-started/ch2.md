# Vous ne connaissez pas encore JS : Débuter - 2e édition
# Chapter 2: Arpenter JS

La meilleur façon d'apprendre JS est en l'écrivant.

Pour cela, vous avez besoin de savoir comment le langage fonctionne, c'est ce que nous allons aborder ici. Même si vous avez programmé avec d'autres langages par le passé, prenez le temps d'être à l'aise avec JS et prenez soin de vous entrainer sur chaque point.

Ce chapître n'est pas une référence exhaustie sur chaque détail de la syntaxe du langage. Sont but n'est pas non plus d'être une introduction complète à JS pour les débutants.

Nous allons plutôt arpenter certains des sujets les plus importants du langage. Notre but est d'avoir un meilleur ressenti pour pouvoir avancer et coder nos programmes avec davantage de confiance. Nous allons réaborder plusieurs de ces sujets successivement et en détail au gré de ce livre et de ceux du reste de la série.

Ne considérez pas ce chapître comme une lecture rapide, il est long et il y a plein de détails qui donne matière à réfléchir. Prenez votre temps.

| CONSEIL: |
| :--- |
| Si vous êtes toujours en train de vous familiariser avec JS, je vous suggère de prendre un maximum de temps pour travailler sur ce chapître. Prenez chaque partie et réfléchissez, explorez le sujet pendans un temps. Jetez un oeil à des programmes JS existants et comparer ce que vous voyez aux explications et aux opinions présentées ici. Vous tirerez beaucoup plus partie du reste du livre avec de solide bases sur la *nature* du JS. |

## Chaque fichier est un programme

Presque tous les sites web (et applications web) que vous utilisez sont composés de plein de fichiers JS différents (généralement avec l'extension de fichier .js). C'est tentant de voir cela (l'application) comme un seul programme, mais JS le voit différemment.

Dans JS, chaque fichier autonome est son propre programme distinct.

C'est premièrement important dans la compréhension de la gestion des erreurs. Comme JS traite chaque fichier comme une programme, l'un peut échouer (pendant l'analyse/compilation ou l'éxécution) sans que cela empêche nécessairement le fichier suivant d'être traité. Evidemment, si vous application repose sur cinq fichier .js et que l'un d'eux échoue, l'application ne fonctionnera probablement que partiellement. C'est donc important de s'assurer que chaque fichier fonctionne bien et qu'autant que possible il gère les exceptions dans d'autres fichiers du mieux possible.

Cela peut vous surprendre de considérer les fichiers .js séparés comme des programmes distincts. Depuis le point de vue de l'usage qu'on fait d'une application, cela ressemble bien à un seul gros programme. Ceci est du au fait que l'éxécution de l'application autorise ces programmes individuels à coopérer et agit comme un seul programme.

| NOTE: |
| :--- |
| Beaucoup de projets utilisent des outils de *build* qui finisse par combiné les fichiers séparés en un seul ensuite délivré à la page web. Quand cela arrive, JS traite ce fichier combiné comme un programme entier. |

La seule façon dont de multiples fichiers .js séparés peuvent agir comme un seul programme est en se partageant leur état (et en donnant accès à leurs fonctionnalités publiques) via le *global scope*.

En addition à ce format, JS supporte les modules depuis l'ES6. Les modules sont aussi basés sur leur fichier. Si un fichier est chargé via le mécanisme de chargement de module comme la déclaration `import` ou une balise `<script type=module>`, tout ce code est traité comme un seul module.

Bien que vous ne penseriez pas qu'un module - une collection d'état et des méthodes publiquement exposées pour opérer sur cet état - est un programme en soi, JS le traite effectivement séparément. Comme la façon dont le *global scope* permet à des fichiers de se mixer à l'éxécution, importer un module dans un autre autorise l'inter-opération entre eux au moment de l'éxécution.

Quel que soit le modèle d'organisation de code (et ses mécaniques de chargement) utilisé pour un fichier (autonome ou module), vous devriez toujours penser chaque fichier comme un (mini) programme qui pourra coopérer avec d'autres (mini) programmes pour éxécuter les fonctions de votre application.

## Valeurs

L'unité d'information la plus fondamentale dans un programme est une valeur. Les valeurs sont des données. Elles permettent au programme de maintenir leur état. Les valeurs existent en deux formes en JS : **primitive** et **objet**.

Les valeurs sont intégrées dans les programmes en utilisant des *literals*:

```js
greeting("My name is Kyle.");
```

Dans ce programme, la valeur `"My name is Kyle."` est une *primitive string literal*. Les chaînes sont des collections ordonnées de caractères généralement utilisées pour représenter des mots ou des phrases.

J'ai utilisé le caractère guillemet `"` pour *délimiter* (entourer, séparer, définir) la valeur de la chaîne. J'aurais pu aussi utiliser le caractère apostrophe `'`. Le choix de l'un ou l'autre est entièrement stylistique. Pour des questions de maintenabilité et de lecture, le plus important est d'en choisir un et de l'utiliser sur l'ensemble du programme.

Il est aussi possible d'utiliser l'accent grave pour les délimiter `` ` ``. Toutefois, ce n'est plus un choix seulement stylistique car cela induit un changement de comportement :

```js
console.log("My name is ${ firstName }.");
// My name is ${ firstName }.

console.log('My name is ${ firstName }.');
// My name is ${ firstName }.

console.log(`My name is ${ firstName }.`);
// My name is Kyle.
```

En considérant que ce programme a déjà défini une variable `firstName` avec la valeur `"Kyle"`, la chaîne délimitée par  `` ` `` résoud l'expression variable (indiqué par `${ .. }`) à sa valeur courante. Ca s'appelle **l'interpolation**

La chaîne délimitée avec l'accent grave `` ` `` peut-être utilisée sans expressions interpolées, mais elle en perd tout son intérêt :

```js
console.log(
    `Am I confusing you by omitting interpolation?`
);
// Am I confusing you by omitting interpolation?
```

La meilleure approche est d'utiliser `"` ou `'` (encore une fois, choisissez en une et tenez y vous) pour les chaînes de caractères *sauf si vous avez besoin* d'interpolation. Réservez  `` ` `` uniquement pour les chaînes qui incluent des expressions interpolées.

En plus des chaînes de caractères, les programmes JS contiennent souvent d'autres valeurs *primitive literal* comme les booléens et les nombres :

```js
while (false) {
    console.log(3.141592);
}
```

`while` représente un type de boucle, une façon de répété des opérations *tant que* la condition est vraie.

Dans ce cas, la boucle ne se lancera jamais (et rien ne sera log) car nous avons utilisé la valeur booléenne `false` comme condition de la boucle. `true` aurait entrainé une boucle infinie, donc faites attention !

Le nombre `3.141592` est, comme vous devez le savoir, une approximation du nombre PI aux six premiers chiffres. Plutôt que d'intégrer une telle valeur, vous utiliserez généralement pour ce cas la valeur prédéfinie `Math.PI`. Une autre variation sur les nombres est le type primitif `bigint` (big-integer) qui est utilisé pour stocker arbitrairement des grands nombres.

Les nombres sont le plus souvent utilisés dans les programmes pour compter les étapes comme les itérations de boucle et pour accéder à des informations situées à des positions numériques (comme un index de tableau). Nous couvriront les tableaux/objets plus tard mais pour exemple, s'il y avait un tableau appelé `names`, on pourrait accéder à l'élément en deuxième position comme cela :

```js
console.log(`My name is ${ names[1] }.`);
// My name is Kyle.
```

Nous avons utilisé `1`pour l'élément en deuxième position au lieu de `2` car comme dans la plupart des langages de programmation, les tableaux JS commencent à l'indice 0 (`0` est la première position).

En plus des chaînes de caractères, des booléens et des nombres, deux autres valeurs *primitives* existent dans les programmes JS : `null` et `undefined`. Bien qu'il y ait des différences entre les deux (certaines historiques et d'autres contemporaines), pour la majeure partie ces deux valeurs réponde au besoin d'indiquer le vide ou l'absence de valeur.

Beaucoup de développeur préfèrent traiter les deux dans ce but ce qui explique le fait qu'on dise qu'elle ne sont pas distinguables. En faisant attention, c'est toujours possible. Cependant, il est plus sûr et préférable d'utiliser seulement `undefined` comme la seule valeur vide même si `null` semble attractive en raison de son écriture plus courte.

```js
while (value != undefined) {
    console.log("Still got something!");
}
```

La dernière valeur primitive à connaître est symbol qui est une valeur à l'usage spécifique qui se comporte comme une valeur caché indevinable. Les Symbols sont presque exclusivement utilisés comme des clés spéciales sur les objets :


```js
hitchhikersGuide[ Symbol("meaning of life") ];
// 42
```

Vous ne rencontrerez pas souvent d'utilisation directe des symbols dans des programmes JS classiques. Ils sont principalement utilisés pour du code bas-niveau comme dans les librairies et les frameworks.

### Tableaux et objets

Outre les primitives, l'autre type de valeurs en JS est l'objet.

Comme mentionné plus tôt, les tableaux sont un type d'objet spécial qui comprennent une liste de données indexées numériquement.

```js
var names = [ "Frank", "Kyle", "Peter", "Susan" ];

names.length;
// 4

names[0];
// Frank

names[1];
// Kyle
```

Les tableaux JS peuvent contenir n'importe quel type de données (primitives ou objets, incluant d'autres tableaux). Comme on verra à la fin du chapître 3, même les fonctions sont des valeurs qui peuvent être stockées dans des tableaux ou des objets.

| NOTE: |
| :--- |
| Les fonctions, comme les tableaux, sont un type spécial d'objets (alias sous-type). On abordera le sujet des fonctions rapidement. |

Les objets sont une collection à clé non ordonnée de différentes valeurs. En d'autres termes, vous accédez à un élément par une chaîne de caractère représentant le nom de la localisation (alias clé ou propriété) plutôt que par une position numérique (comme pour les tableaux). Par exemple :

```js
var me = {
    first: "Kyle",
    last: "Simpson",
    age: 39,
    specialties: [ "JS", "Table Tennis" ]
};

console.log(`My name is ${ me.first }.`);
```

Ici `me` représente un objet et `first` représente le nom de la localisation d'une information dans cet objet. Une autre option syntaxique est d'accéder à l'information dans un objet en utilisant sa propriété/clé entre crochets `[ ]`, comme dans  `me["first"]`.

### Détermination du type de valeur

Pour distinguer les valeurs, l'opérateur `typeof` vous dit son type intégré s'il est primitif ou renvoie `"object"` dans les autres cas :

```js
typeof 42;                  // "number"
typeof "abc";               // "string"
typeof true;                // "boolean"
typeof undefined;           // "undefined"
typeof null;                // "object" -- oops, bug!
typeof { "a": 1 };          // "object"
typeof [1,2,3];             // "object"
typeof function hello(){};  // "function"
```

| ATTENTION: |
| :--- |
| `typeof null` retourne malheureusement `"object"` au lieu de `"null"`. `typeof` retourne aussi `"function"` pour les fonctions mais pas la valeur attendue `"array"` pour les tableaux. |

Convertir une valeur d'un type à un autre, comme d'une chaîne de caractère à un nombre, est une opération appelée en JS "coercition". Nous aborderons ce sujet plus en détail plus tard dans ce chapître.

Les valeurs primitives et les valeurs objets se comportent différemment quand elles sont affectées ou transmises. Nous couvrirons ces détails dans l'annexe A, "Valeurs vs Références".

## Déclarer et utiliser des variables

Pour être explicite avec quelque chose qui n'était peut-être pas évident dans la partie précédente : dans les programmes JS, les valeurs peuvent apparaîtrent comme des valeurs littérals (comme le montre les nombreux exemples précédents) ou elles peuvent être stockées dans des variables - voyez ça comme des petits conteneurs de valeurs.

Les variables ont besoin d'être déclarées (créées) pour être utilisées. Il y a différentes formes syntaxiques qui déclarent des variables (alias identifieurs) et chaque forme entraine un comportement implicite.

Par exemple, cette déclaration `var` :

```js
var myName = "Kyle";
var age;
```

Le mot-clé `var` déclare la variable à utiliser dans cette partie du programme et autorise optionnellement une assignation de valeur initiale.

`let` est un autre mot-clé similaire :

```js
let myName = "Kyle";
let age;
```

Il y a quelques différences entre `let`et `var`, la plus évidente est le fait que `let` autorise un accès plus limité à la variable que `var`. Cela s'appelle le *"block scoping"* par opposition à la portée classique ou la portée de fonction.

Considérez :

```js
var adult = true;

if (adult) {
    var myName = "Kyle";
    let age = 39;
    console.log("Shhh, this is a secret!");
}

console.log(myName);
// Kyle

console.log(age);
// Error!
```

Tenter d'accéder à `age` en dehors du `if` entraine une erreur car `age` est *block-scoped* au `if` alors que `myName` ne l'est pas.

*Block-scoping* est très utile pour limiter la façon dont les déclarations de variable se propagent dans notre programme, cela prévient les chevauchements de leurs noms.

Mais `var` est toujours utile car ce qu'il communique "cette variable sera visible dans une portée plus grande (pour toute une fonction)". Les deux formes de déclaration peuvent être appropriées quel que soit la partie du programme, cela dépend des circonstances.

| NOTE: |
| :--- |
| Il est très commun de suggérer que `var` devrait être évité en faveur de `let` (ou `const`) généralement en raison d'une confusion perceptible dans la façon dont la portée de `var` fonctionne depuis la naissance de JS. Je crois que c'est un conseil trop restrictif et finalement peu aidant. C'est assumer le fait que vous soyiez imcapable d'apprendre à utiliser une fonctionnalité correctement en combinaison avec d'autres. Je pense que vous *pouvez* et *devriez* apprendre toutes les fonctionnalités disponibles afin de les utiliser de façon appropriées ! |

Un troisième type de déclaration est `const`. C'est comme `let` avec quelques limitations supplémentaires tel qu'il est obligatoire de lui attribuer une valeur à la déclaration et que celle-ci ne peut pas être ré-assignée une valeur différente plus tard.

Considérez :

```js
const myBirthday = true;
let age = 39;

if (myBirthday) {
    age = age + 1;    // OK!
    myBirthday = false;  // Error!
}
```

La constant `myBirthday` n'a pas le droit d'être ré-assignée.

Les variables déclarées avec `const` ne sont pas inchangeables, elles ne peuvent juste pas être ré-assignée. Il est déconseillé d'utiliser `const` avec les objets car ces valeurs peuvent toujours être changées même si la variable ne peut pas être ré-assignée. Cela conduit à de potentielles confusions dans le code donc je trouve qu'il est plus sage d'éviter des situations telles que :

```js
const actors = [
    "Morgan Freeman", "Jennifer Aniston"
];

actors[2] = "Tom Cruise";   // OK :(
actors = [];                // Error!
```

Le meilleur usage sémantique de `const` est quand vous avez une valeur primitive simple à qui vous voulez donner un nom utile comme `myBirthday` au lieu de `true`. Cela rend les programmes plus facile à lire.


| TIP: |
| :--- |
| Si vous vous cantonnez à utiliser `const` uniquement pour des valeurs primitives, vous évitez toutes confusion de ré-assignation (non autorisées) vs. mutations (autorisées) ! C'est la façon la plus sûre d'utiliser `const`. |

Outre  `var` / `let` / `const`, il y a d'autres formes syntaxique pour déclarer des identifieurs (variables) dans différentes portées. Par exemple :

```js
function hello(myName) {
    console.log(`Hello, ${ myName }.`);
}

hello("Kyle");
// Hello, Kyle.
```

L'identifieur `hello` est créé dans la portée externe et est automatiquement associée pour faire référence à la fonction. Mais le nom du paramètre `myName` est créé uniquement à l'intérieur de la fonction et est donc uniquement accessible à l'intérieur de la portée de la fonction. `hello` et `myName` se comporte générallement comme si déclaré avec `var`.

Une autre syntae pour déclarer une variable est la clause `catch` :

```js
try {
    someError();
}
catch (err) {
    console.log(err);
}
```

`err` est une variable *block-scoped* qui existe uniquement dans la clause `catch` comme si elle avait été déclarée avec `let`

## Fonctions

Le mot "fonction" a différents sens en programmation. Par exemple, dans le monde de la programmation fonctionnelle, la "fonction" a une définition mathématique précise qui implique des règles strictes à appliquer.

En JS, on devrait considérer une "fonction" dans un sens élargit d'un autre terme lié : "procédure". Une procédure est une collection de déclarations qui peut être invoquée une ou plusieurs fois, pouvant recevoir des entrées et pouvant renvoyer un ou des sorties.

Dans les premiers jours du JS, une définition de fonction ressemblait à ça :

```js
function awesomeFunction(coolThings) {
    // ..
    return amazingStuff;
}
```

Ceci s'appelle une déclaration de fonction car c'est une déclaration en soi, pas une expression dans une autre déclaration. L'association entre l'identifieur `awesomeFunction`et la valeur de la fonction a lieu pendant la phase de compilation du code, avant qu'il soit éxécuté.

Par opposition a une déclaration de fonction, une expression de fonction peut être définie et assignée comme ça :

```js
// let awesomeFunction = ..
// const awesomeFunction = ..
var awesomeFunction = function(coolThings) {
    // ..
    return amazingStuff;
};
```

Cette fonction est une expression qui est assignée à la variable `awesomeFunction`. Différente de la forme déclarative, une expression n'est pas associée à son identifieur jusqu'au moment de cette déclaration à l'éxécution.

C'est extrêmement important de noter qu'en JS, les fonctions sont des valeurs qui peuvent être assignées (comme vu dans l'extrait plus haut) et transmises. En fait, les fonctions JS sont un type spécial du type de valeur objet. Tous les langages ne traitent pas les fonctions comme des valeurs, mais il est essentiel pour un langage de supporter le modèle de programmation fonctionnel, ce que JS fait.

Les fonctions JS peuvent recevoir des paramètres en entrée :

```js
function greeting(myName) {
    console.log(`Hello, ${ myName }!`);
}

greeting("Kyle");   // Hello, Kyle!
```

Dans cet extrait, `myName` est un paramètre qui agit comme variable locale dans la fonction. Les fonctions peuvent recevoir un nombre illimité de paramètres. Chaque paramètre est assigné à la valeur passée en argument à la position de l'appel (`"Kyle"`, dans ce cas).

Les fonctions peuvent retourner des valeurs grâce au mot-clé `return` :

```js
function greeting(myName) {
    return `Hello, ${ myName }!`;
}

var msg = greeting("Kyle");

console.log(msg);   // Hello, Kyle!
```

Vous pouvez seulement `return` une seule valeur mais si vous en avez plusieurs, vous pouvez les intégrer dans un seul objet/tableau.

Comme les fonctions sont des valeurs, elles peuvent être assignées en tant que propriété d'un objet :

```js
var whatToSay = {
    greeting() {
        console.log("Hello!");
    },
    question() {
        console.log("What's your name?");
    },
    answer() {
        console.log("My name is Kyle.");
    }
};

whatToSay.greeting();
// Hello!
```

Dans cet extrait, Les références à trois fonctions (`greeting()`, `question()`, et `answer()`) sont incluses dans un objet tenu par `whatToSay`. Chaque fonction peut être appellée en accèdant à la propriété pour en retrouver la référence. La comparaison entre ce style simple de définition de fonctions dans un objet et la syntaxe plus sophistiquée `class` sera abordée plus tard dans ce chapître.

Les fonctions prennent beaucoup de formes différentes en JS, on creusera ces variantes dans l'annexe A : "Tellement de forme de fonctions".

## Comparaisons

Prendre des décisions dans un programme nécessite de comparer des valeurs pour déterminer leur identité, leurs relations. JS possède différents mécanismes pour réaliser des comparaisons de valeurs, regardons cela de plus près.

### Equal...ish

La plus simple comparaison dans les programmes JS pose la question : "Est-ce que cette valeur X *est la même que* cette valeur Y ?" Mais que signifie exactement *est la même que* en JS ?

Pour des raisons ergonomiques et historiques, le sens est plus compliqué que l'espèce de correspondance *exacte*. Parfois, une comparaison d'égalité est en effet une correspondance exacte, mais d'autres fois, la comparaison désirée est plus large, autorisant une *étroite* ou une *interchangeable* correspondance. En d'autres termes, on a besoin de connaître les différentes nuances entre une **comparaison d'égalité** et une **comparaison d'équivalence**.

Si vous avez passé un peu de temps à lire et à travailler du JS, vous avez déjà du voir le bien connu opérateur "triple égal" `===` aussi décrit comme l'opérateur d'égalité stricte. Cela semble assez simple non ? Surement, "strict" veut dire strict comme étroit veut dire *exact*

Pas *exact*ement.

Bien sûr, la plupart des valeurs participant à une comparaison d'égalité avec le `===` va correspondre exactement à notre intuition. Considérez cet exemple.

```js
3 === 3.0;              // true
"yes" === "yes";        // true
null === null;          // true
false === false;        // true

42 === "42";            // false
"hello" === "Hello";    // false
true === 1;             // false
0 === null;             // false
"" === null;            // false
null === undefined;     // false
```

| NOTE: |
| :--- |
| La comparaison d'égalité avec le `===` est souvent décrite comme "vérifiant la valeur et le type". Dans beaucoup d'exemple qu'on a vu jusque là, comme `42 === "42"`, le type des deux valeurs (nombre et chaîne de caractères) semble être un facteur différenciant. Il y a plus que ça là dedans., Toutes les comparaisons de valeur en JS considère le type de valeur au moment de la comparaison, pas *juste* l'opérateur. Spécialement  `===` n'autorise aucune conversion de type (alias "coercition") dans ces comparaisons, là où d'autres comparaisons JS *autorise* la coercition. |


Mais l'opérateur `===` a quelques nuances dissimulées à ce comportement. Il est conçu pour *mentir* dans deux cas spéciaux : `NaN` et `-0`. Considérez :

```js
NaN === NaN;            // false
0 === -0;               // true
```

Dans le cas du `Nan`, l'opérateur `===` et dit que `NaN` n'est pas égal à `NaN`. Dans le cas du `-0` (oui, c'est un vraie valeur que vous pouvez utiliser intentionnellement dans vos programmes), l'opérateur `===` ment et dit qu'il est égal à un simple `0`.

Comme le mensonge pour ces comparaisons est ennuyant, il vaut mieux éviter le `===` dans ces cas. Pour les comparaisons `NaN` il y a l'utilitaire  `Number.isNaN(..)` qui ne ment pas. Pour la comparaison `-0`, on peut utiliser l'utilitaire `Object.is(..)` qui ne ment pas non plus. `Object.is(..)` peut aussi être utilisé pour la vérification du `NaN` si vous préférez. En fait, vous pourriez penser que `Object.is(..)` est le  "quadruple égal" `====`, la comparaison vraiment-vraiment stricte !

Il y a des raisons historiques et techniques profondes pour ces mensonges, mais ça ne change pas le fait que `===` n'est pas réellement une comparaison *strictement exacte* dans le plus *strict* des sens.

L'histoire devient encore plus compliquée quand on considère les comparaisons entre des valeurs objets (non primitives. Considérez :

```js
[ 1, 2, 3 ] === [ 1, 2, 3 ];    // false
{ a: 42 } === { a: 42 }         // false
(x => x * 2) === (x => x * 2)   // false
```

Que se passe-t-il ?

<!-- @todo WORK GOES ON HERE -->
Cela semble raisonnable de penser qu'une vérification d'égalité considère la *nature* ou le *contenu* de la valeur, après tout `42 === 42` prend la valeur `42` et la compare. Mais quand il s'agit d'objets, une comparaison du contenu est généralement appelée une "égalité structurelle".

Js ne définit pas `===` comme une égalité structurelle pour les valeurs d'un objet, il utilise `===` comme une égalité d'identité.

En JS toutes les valeurs objets sont tenue par référence (voir "Valeurs vs Références" en annexe A) et sont assignées et passées par copie de référence **et**, au regard de notre conversation, sont comparés par égalité de référence (identité). Considérez :

```js
var x = [ 1, 2, 3 ];

// assignment is by reference-copy, so
// y references the *same* array as x,
// not another copy of it.
var y = x;

y === x;              // true
y === [ 1, 2, 3 ];    // false
x === [ 1, 2, 3 ];    // false
```

Dans cet extrait, `y === x` est vrai car les deux variables portent la référence au même tableau initial. Mais la comparaison `=== [1,2,3]` échoue à chaque fois car `y` et `x` sont respectivement comparés à de nouveaux tableaux différents `[1,2,3]`. La structute du tableau et son contenu ne compte pas dans cette comparaison, seul la **référence, l'identité** compte.

JS n'a pas de mécanisme de comparaison d'égalité structurelle pour les valeurs objets, il n'y a que la comparaison d'identité. Pour avoir une comparaison d'égalité structurelle, il faudra réaliser vous même les validations.

Attention, c'est plus compliqué que ce que vous pensez. Par exemple, comment détermineriez vous so deux références de fonctions sont "structurellement équivalentes" ? Même une conversion en chaîne de caractère du code source ne prendrait pas en compte les éventuelles fermetures. JS ne fournit pas ce type de comparaison car c'est presque impossible de couvrir tous les cas particuliers.

### Comparaison coercitive

La coercition signifie la conversion d'une valeur d'un type vers sa représentation dans un autre type (tant que possible). Comme on le verra dans le chapître 4, la coercition est un pilier fondamental du langage JS, pas une petite fonctionnalité qu'il est possible d'oublier.

Mais quand la coercition rencontre les opérateurs de comparaison (comme l'égalité), cela fait malheureusement souvent émerger de la confusion et de la frustration.

Peu de fonctionnalités JS suscitent plus de colère dans la communauté JS que l'opérateur `==` généralement appelé l'opérateur "d'égalité lâche". La majorité des écrits et des discours publics sur JS condamnent cet opérateur mal conçu et et dangereux/porteur de bugs quand il est utilisé dans un programme JS. Même le créateur du langage, Brendan Eich, c'est lamenté en disant que son design était une grosse erreur.

De ce que je peux dire, la plupart de cette frustration vient d'une petit liste de cas particuliers, mais le problème profond vient d'une incompréhension largement répendue selon laquelle les comparaisons sont réalisées sans comparer le type des valeurs.

L'opérateur `==` réalise une comparaison d'égalité similaire à celle du `===`. En fait, les deux considèrent le type des valeurs comparés et si la comparaison est entre deux valeur de même type `==` et `===` **se comporte exactement de la même façon.**

Si les types de valeurs sont différents, le `==` diffère du `===` dans le sens où il autorise la coercition avant la comparaison. En d'autres termes, ils veulent tous les deux comparés des valeurs de types similaires mais `==` permet une convertion d'abord et une les valeurs converties des deux deux côtés, `==` fait la même chose que  `===`. Au lieu d'"égalité lâche", le  `==` devrait être décrit comme "égalité coercitive".

Considérez :

```js
42 == "42";             // true
1 == true;              // true
```

Dans les deux comparaisons, les types de valeurs sont différents donc le `==` entraine une convertion des valeurs non numérique  (`"42"` et `true`) en nombre (respectivement `42` et `1`) avant que la comparaison soit faite.

Le fait d'être conscient du fait que `==` préfère les comparaisons de nombres peut vous éviter beaucoup de problèmes dans certains cas particuliers comme d'éviter `"" == 0` ou `0 == false`.

Vous devez vous dire : "Bien, je vais juste toujours éviter la comparaison coercitive pour éviter les cas particuliers !" Mais désolé, ce n'est pas aussi simple que vous le pensez.

Il y a de grandes chance que vous utilisez des opérateurs de comparaison relationnels comme `<`, `>` (et même `<=` et `>=`).

Tout comme `==`, ces opérateurs réaliseront une comparaison "stricte" si le type des valeurs est le même mais opéreront une coercition d'abord (généralement vers des nombres) si les types différent. Considérez :

```js
var arr = [ "1", "10", "100", "1000" ];
for (let i = 0; i < arr.length && arr[i] < 500; i++) {
    // will run 3 times
}
```

La comparaison `i < arr.length` ne fera pas de coercition car `i` et `arr.length` sont toujours des nombres. Par contre  `arr[i] < 500` nécessite une coercition car les valeurs `arr[i]` sont des chaînes de caractères. Ces comparaisons deviennent ainsi `1 < 500`, `10 < 500`, `100 < 500`, et `1000 < 500`. Comme la 4e est fausse, la boucle s'arrêtera après sa troisième itération.

Ces opérateurs relationnels utilisent généralement les comparaisons numériques sauf dans le où les deux valeurs comparées sont déjà des chaînes de caractères. Dans ce cas, ils utilisent la comparaison alphabétique :

```js
var x = "10";
var y = "9";

x < y;      // true, watch out!
```

Il n'y a pas de façon d'éviter la coercition pour ces opérations relationnels autrement quand n'utilisant jamais différents types dans la comparaison. C'est peut-être un but admirable mais c'est presque sûr que vous allez vous retrouvez dans des situations où les types peuvent différer.

L'approche la plus sage n'est pas d'éviter à tout prix la comparaison coercitive mais plutôt de l'embracer et d'apprendre ses tenants et aboutissants.

Les comparaisons coercitives surgissent à d'autres endroits en JS comme dans les conditions (`if`, etc.) qu'on reverra dans l'annexe A "Comparaison coercitive conditionnelle".

## Comment on s'organise en JS

Deux principaux modèles pour organiser le code (données et comportements) sont utilisés dans l'éco-système JS : les classes et les modules. Ces modèles ne sont pas mutuellement exclusifs, beaucoup de programmes utilisent les deux. D'autres programmes n'en utiliseront qu'un ou même aucun !

A certains égards, ces modèles sont très différents. Mais ils sont d'une autre façon les deux côté d'une même pièce. Etre performant en JS demande de comprendre les deux modèles et de savoir quand ils sont appropriés (ou pas !).

### Classes

Les termes "orienté objets, "orienté classes" et "classes" sont tous chargés de plein de détails et nuances, ce ne sont pas des définitions universelles.

Nous utiliserons une définition plutôt traditionnelle ici, celle qui sera plus familière à ceux qui viennent de langages "orientés objets" comme C++ et Java.

Dans un programme, une classe est une définition d'un "type" de structure de donnée personnalisée qui inclut à la fois la donnée et ses comportement de traitement. Les classes définissent la façon dont la structure de la donnée fonctionne mais elles ne sont pas en soi des valeurs concrètes. Pour obtenir une valeur concrète utilisable dans votre programme, une classe a besoin d'être *instanciée* (avec le mot-clé `new`) une ou plusieurs fois.

Considérez :

```js
class Page {
    constructor(text) {
        this.text = text;
    }

    print() {
        console.log(this.text);
    }
}

class Notebook {
    constructor() {
        this.pages = [];
    }

    addPage(text) {
        var page = new Page(text);
        this.pages.push(page);
    }

    print() {
        for (let page of this.pages) {
            page.print();
        }
    }
}

var mathNotes = new Notebook();
mathNotes.addPage("Arithmetic: + - * / ...");
mathNotes.addPage("Trigonometry: sin cos tan ...");

mathNotes.print();
// ..
```
Dans la classe `Page`, la donnée est une chaîne de caractères stockée dans la propriété membre `this.text`. Le comportement est `print()`, une méthode qui affiche le texte dans la console.

Pour la classe `Notebook`, la donnée est un tableau d'instances de `Page`. Le comportement est `addPage(..)`, une méthode qui instancie une nouvelle `Page` et l'ajoute à la liste, elle contient également `print()` (qui affiche toutes les pages du carnet).

La déclaration `mathNotes = new Notebook()` crée une instance de la classe `Notebook` et `page = new Page(text)` est là où les instances de la classe `Page` sont créées.

Les comportements (méthodes) peuvent seulement être appelées par les instances (pas la classe elle-même) comme par exemple `mathNotes.addPage(..)` et `page.print()`.

Le mécanisme de classe autorise le empaquettage de données (`text` et `pages`) pour organiser ensemble leurs comportements (comme `addPage(..)` et `print()`). Le même programme aurait pu être conçu sans définitions de classes, mais il serait bien moins organisé, plus difficile à lire et, de ce fait, plus susceptible de générer des bugs et des soucis à la maintenance.

#### Héritage de classes

Un autre aspect des modèles traditionnels de l'orienté objet, même si moins communément utilisé en JS, est l'héritage (et "polymorphisme). Considérez :

```js
class Publication {
    constructor(title,author,pubDate) {
        this.title = title;
        this.author = author;
        this.pubDate = pubDate;
    }

    print() {
        console.log(`
            Title: ${ this.title }
            By: ${ this.author }
            ${ this.pubDate }
        `);
    }
}
```

Cette classe `Publication` définie un ensemble de comportements communs à toute publication.

Maintenant considérons un type plus spécifique de publication comme un livre ou un billet de blog :

```js
class Book extends Publication {
    constructor(bookDetails) {
        super(
            bookDetails.title,
            bookDetails.author,
            bookDetails.publishedOn
        );
        this.publisher = bookDetails.publisher;
        this.ISBN = bookDetails.ISBN;
    }

    print() {
        super.print();
        console.log(`
            Publisher: ${ this.publisher }
            ISBN: ${ this.ISBN }
        `);
    }
}

class BlogPost extends Publication {
    constructor(title,author,pubDate,URL) {
        super(title,author,pubDate);
        this.URL = URL;
    }

    print() {
        super.print();
        console.log(this.URL);
    }
}
```

`Book` et `BlogPost` utilisent la clause `extends` pour étendre leur définition générale de `Publication` afin d'inclure des comportements supplémentaires. L'appel `super(..)` dans chaque constructeur délègue le travail d'initialisation au constructeur de la class parente `Publication` et ensuite réalise des tâches spécifiques en fonction du type respectif de publication (alias des "sous-classes" ou "classes enfants").

Maintenant utilisons ces classes enfant :

```js
var YDKJS = new Book({
    title: "You Don't Know JS",
    author: "Kyle Simpson",
    publishedOn: "June 2014",
    publisher: "O'Reilly",
    ISBN: "123456-789"
});

YDKJS.print();
// Title: You Don't Know JS
// By: Kyle Simpson
// June 2014
// Publisher: O'Reilly
// ISBN: 123456-789

var forAgainstLet = new BlogPost(
    "For and against let",
    "Kyle Simpson",
    "October 27, 2014",
    "https://davidwalsh.name/for-and-against-let"
);

forAgainstLet.print();
// Title: For and against let
// By: Kyle Simpson
// October 27, 2014
// https://davidwalsh.name/for-and-against-let
```

Noté que les deux instances de classes enfant ont la méthode `print()` qui est un remplacement de la méthode `print()` *héritée* de la classe parent  `Publication`.

Le fait que les deux méthodes (la parente et l'héritée) peuvent avoir le même nom et co-existent est appelé le *polymorphisme*.

L'héritage est un outil puissant pour organiser la donnée et ses comportement dans des unités logiques séparées (les classes) mais en coopération en autorisant la classe enfant à accéder/utiliser les comportements et données de la classe parente.

### Modules

Le modèle de module a essentiellement le même but que le modèle avec les classes qui est de grouper les données et les comportements ensemble dans unités logiques. Comme les classes, les modules peuvent inclure ou accéder aux données et comportements d'autres modules pour des besoins de coopération.

Toutefois les modules ont quelques différences importantes avec les classes. Une notamment, est la syntaxe qui est complètement différente.

#### Modules classiques

ES6 a ajouté une forme syntaxique de module à la syntaxe native JS, ce qu'on verra plus tard. Mais depuis les débuts du JS, les modules sont un modèle commun et important qui a été mis à profit dans de nombreux programmes même sans syntaxe dédiée.

La marque de fabrique d'un *module classique* est une fonction extérieure (qui s'éxécute au moins une fois) qui retourne une "instance" du module avec une ou plusieurs fonctions exposées qui peuvent opérer sur les données interne (et cachées) de l'instance.

Parce qu'un module de cette forme est *juste* une fonction et que l'appelée produit une "instance" de ce module; une autre description de ces fonctions est les "usines de modules". 

Regardons une forme classique de module des classes `Publication`, `Book`, et `BlogPost` :

```js
function Publication(title,author,pubDate) {
    var publicAPI = {
        print() {
            console.log(`
                Title: ${ title }
                By: ${ author }
                ${ pubDate }
            `);
        }
    };

    return publicAPI;
}

function Book(bookDetails) {
    var pub = Publication(
        bookDetails.title,
        bookDetails.author,
        bookDetails.publishedOn
    );

    var publicAPI = {
        print() {
            pub.print();
            console.log(`
                Publisher: ${ bookDetails.publisher }
                ISBN: ${ bookDetails.ISBN }
            `);
        }
    };

    return publicAPI;
}

function BlogPost(title,author,pubDate,URL) {
    var pub = Publication(title,author,pubDate);

    var publicAPI = {
        print() {
            pub.print();
            console.log(URL);
        }
    };

    return publicAPI;
}
```

En comparant ces formes aux classes, on se rend compte qu'il y a plus de similarités que de différences.

Les classes stockent les méthodes et la donnée dans une instance objet qui est accessible via le préfixe `this`. Avec les modules, les méthodes et les données sont accessibles via des variables sans aucun préfixe.

Avec les classes, l'API d'une instance est implicite ainsi que la définition de la classe aussi, toutes les données et méthodes sont publiques. Avec la fonction usine de modules, vous créez explicitement et retournez un objet avec les méthodes exposées publiquement, toutes données ou autres méthodes non référencées restent privées dans la fonction usine.

Il y a d'autres variations de ces fonctions usine qui sont très commune en JS, même en 2020. Vous allez surement tomber sur ces formes dans différents programmes : AMD (Asynchronous Module Definition), UMD (Universal Module Definition), et CommonJS (classic Node.js-style modules). Les variations sont mineures (pas tout à fait compatible). Cependant toutes ces formes se basent sur les mêmes principes.

Considérons également l'usage (alias l'instanciation) de ces fonctions usine à modules :

```js
var YDKJS = Book({
    title: "You Don't Know JS",
    author: "Kyle Simpson",
    publishedOn: "June 2014",
    publisher: "O'Reilly",
    ISBN: "123456-789"
});

YDKJS.print();
// Title: You Don't Know JS
// By: Kyle Simpson
// June 2014
// Publisher: O'Reilly
// ISBN: 123456-789

var forAgainstLet = BlogPost(
    "For and against let",
    "Kyle Simpson",
    "October 27, 2014",
    "https://davidwalsh.name/for-and-against-let"
);

forAgainstLet.print();
// Title: For and against let
// By: Kyle Simpson
// October 27, 2014
// https://davidwalsh.name/for-and-against-let
```

La seule différence observable ici est l'absence du `new`, on appelle les usines à modules comme des fonctions normales.

#### ES Modules

Les modules ES (ESM), introduient dans le langage avec l'ES6 sont censés servir le même but que les *modules classiques* décrit juste au dessus, en tenant spécialement compte des variations importantes et des usages de AMD, UMD, and CommonJS.

L'approche dans l'implémentation diffère cependant beaucoup

D'abord, il n'y a pas de fonction englobante pour définit le module. Le contexte global est celui du fichier. Les ESM sont toujours basés sur les fichiers : un fichier, un module.

Deuxièmement, vous n'interagissez pas avec l'API d'un module explicitement. Vous allez plutôt utiliser le mot-clé `export` pour ajouter une variable ou une méthode à la définition de son API publique. Si quelque chose est défini dans le module mais n'est pas exporté, cela reste caché (comme dans les *modules classiques*).

Troisièmement, et sans doute la différence la plus notable avec les modèles déjà présentés, vous n'instanciez pas un module ES, vous l'importez juste pour en utiliser sa seule instance. Les ESM sont effectivement des "singletons" dans le sens où il n'y a qu'une seule instance créée au premier `import` et tous les autres `import` recevront une référence de cette instance. Si votre module nécessite des instanciations multiples, vous devez fournir une fonction usine comme pour les *modules classiques* à votre définition ESM.

Dans notre exemple, on suppose une instanciation multiple donc cet extrait va mixer l'ESM avec un *module classique*.

Considérez le fichier `publication.js` :

```js
function printDetails(title,author,pubDate) {
    console.log(`
        Title: ${ title }
        By: ${ author }
        ${ pubDate }
    `);
}

export function create(title,author,pubDate) {
    var publicAPI = {
        print() {
            printDetails(title,author,pubDate);
        }
    };

    return publicAPI;
}
```

Pour importer et utiliser ce module depuis un autre module comme `blogpost.js` :

```js
import { create as createPub } from "publication.js";

function printDetails(pub,URL) {
    pub.print();
    console.log(URL);
}

export function create(title,author,pubDate,URL) {
    var pub = createPub(title,author,pubDate);

    var publicAPI = {
        print() {
            printDetails(pub,URL);
        }
    };

    return publicAPI;
}
```

Finalement, pour utiliser ce module, on importe un autre module ES comme `main.js` :

```js
import { create as newBlogPost } from "blogpost.js";

var forAgainstLet = newBlogPost(
    "For and against let",
    "Kyle Simpson",
    "October 27, 2014",
    "https://davidwalsh.name/for-and-against-let"
);

forAgainstLet.print();
// Title: For and against let
// By: Kyle Simpson
// October 27, 2014
// https://davidwalsh.name/for-and-against-let
```

| NOTE: |
| :--- |
| La clause `as newBlogPost` dans la déclaration de l'import est optionnel. Si omise, une fonction nommée `create(..)` serait importée. Dans ce cas, je le renomme pour la lisibilité. Le terme très générique pour une usine de `create(..)` est beaucoup plus juste sémantiquement dans sa forme `newBlogPost(..)`. |

Comme montré, les modules ES peuvent utiliser des *modules classiques* en interne s'ils ont besoin de multiples instanciations. Nous aurions pu tout aussi bien exposer une classe de notre module plutôt que la fonction usine `create(..)` avec le même résultat. Cependant, comme vous utilisez déjà l'ESM ici, je recommande d'utiliser les *modules classiques* plutôt qu'une classe.

Si votre module a besoin d'une seule instance, vous pouvez sauter cette couche de complexité et exporter ses méthodes publiques directement.

## Le trou du lapin s'agrandit

Comme promis au début de ce chapître, on a juste jeté un coup d'oeil à la vaste surface des parties principales du langage JS. Votre tête est peut-être en train de tourner, c'est tout à fait normal après un tel déluge d'informations !

Même avec cette brève promenade, nous avons couvert ou fait allusion a une tonne de détails que vous devriez soigneusement considérer pour être sûr d'être confortable avec ces notions. Je suis sérieux quand je suggère de relire ce chapître plusieurs fois.

Dans le prochain chapître, nous allons creuser plus profondément certains aspects du fonctionnement du noyau JS. Mais avant de s'enfoncer dans le trou du lapin, soyez certains d'avoir pris le temps adéquat pour digérer complètement ce que nous venons de voir.