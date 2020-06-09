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

<!-- @TODO HERE WORK GOES ON -->
## Functions

The word "function" has a variety of meanings in programming. For example, in the world of Functional Programming, "function" has a precise mathematical definition and implies a strict set of rules to abide by.

In JS, we should consider "function" to take the broader meaning of another related term: "procedure." A procedure is a collection of statements that can be invoked one or more times, may be provided some inputs, and may give back one or more outputs.

From the early days of JS, function definition looked like:

```js
function awesomeFunction(coolThings) {
    // ..
    return amazingStuff;
}
```

This is called a function declaration because it appears as a statement by itself, not as an expression in another statement. The association between the identifier `awesomeFunction` and the function value happens during the compile phase of the code, before that code is executed.

In contrast to a function declaration statement, a function expression can be defined and assigned like this:

```js
// let awesomeFunction = ..
// const awesomeFunction = ..
var awesomeFunction = function(coolThings) {
    // ..
    return amazingStuff;
};
```

This function is an expression that is assigned to the variable `awesomeFunction`. Different from the function declaration form, a function expression is not associated with its identifier until that statement during runtime.

It's extremely important to note that in JS, functions are values that can be assigned (as shown in this snippet) and passed around. In fact, JS functions are a special type of the object value type. Not all languages treat functions as values, but it's essential for a language to support the functional programming pattern, as JS does.

JS functions can receive parameter input:

```js
function greeting(myName) {
    console.log(`Hello, ${ myName }!`);
}

greeting("Kyle");   // Hello, Kyle!
```

In this snippet, `myName` is called a parameter, which acts as a local variable inside the function. Functions can be defined to receive any number of parameters, from none upward, as you see fit. Each parameter is assigned the argument value that you pass in that position (`"Kyle"`, here) of the call.

Functions also can return values using the `return` keyword:

```js
function greeting(myName) {
    return `Hello, ${ myName }!`;
}

var msg = greeting("Kyle");

console.log(msg);   // Hello, Kyle!
```

You can only `return` a single value, but if you have more values to return, you can wrap them up into a single object/array.

Since functions are values, they can be assigned as properties on objects:

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

In this snippet, references to three functions (`greeting()`, `question()`, and `answer()`) are included in the object held by `whatToSay`. Each function can be called by accessing the property to retrieve the function reference value. Compare this straightforward style of defining functions on an object to the more sophisticated `class` syntax discussed later in this chapter.

There are many varied forms that `function`s take in JS. We dig into these variations in Appendix A, "So Many Function Forms."

## Comparisons

Making decisions in programs requires comparing values to determine their identity and relationship to each other. JS has several mechanisms to enable value comparison, so let's take a closer look at them.

### Equal...ish

The most common comparison in JS programs asks the question, "Is this X value *the same as* that Y value?" What exactly does "the same as" really mean to JS, though?

For ergonomic and historical reasons, the meaning is more complicated than the obvious *exact identity* sort of matching. Sometimes an equality comparison intends *exact* matching, but other times the desired comparison is a bit broader, allowing *closely similar* or *interchangeable* matching. In other words, we must be aware of the nuanced differences between an **equality** comparison and an **equivalence** comparison.

If you've spent any time working with and reading about JS, you've certainly seen the so-called "triple-equals" `===` operator, also described as the "strict equality" operator. That seems rather straightforward, right? Surely, "strict" means strict, as in narrow and *exact*.

Not *exact*ly.

Yes, most values participating in an `===` equality comparison will fit with that *exact same* intuition. Consider some examples:

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
| Another way `===`'s equality comparison is often described is, "checking both the value and the type". In several of the examples we've looked at so far, like `42 === "42"`, the *type* of both values (number, string, etc.) does seem to be the distinguishing factor. There's more to it than that, though. **All** value comparisons in JS consider the type of the values being compared, not *just* the `===` operator. Specifically, `===` disallows any sort of type conversion (aka, "coercion") in its comparison, where other JS comparisons *do* allow coercion. |

But the `===` operator does have some nuance to it, a fact many JS developers gloss over, to their detriment. The `===` operator is designed to *lie* in two cases of special values: `NaN` and `-0`. Consider:

```js
NaN === NaN;            // false
0 === -0;               // true
```

In the case of `NaN`, the `===` operator *lies* and says that an occurrence of `NaN` is not equal to another `NaN`. In the case of `-0` (yes, this is a real, distinct value you can use intentionally in your programs!), the `===` operator *lies* and says it's equal to the regular `0` value.

Since the *lying* about such comparisons can be bothersome, it's best to avoid using `===` for them. For `NaN` comparisons, use the `Number.isNaN(..)` utility, which does not *lie*. For `-0` comparison, use the `Object.is(..)` utility, which also does not *lie*. `Object.is(..)` can also be used for non-*lying* `NaN` checks, if you prefer. Humorously, you could think of `Object.is(..)` as the "quadruple-equals" `====`, the really-really-strict comparison!

There are deeper historical and technical reasons for these *lies*, but that doesn't change the fact that `===` is not actually *strictly exactly equal* comparison, in the *strictest* sense.

The story gets even more complicated when we consider comparisons of object values (non-primitives). Consider:

```js
[ 1, 2, 3 ] === [ 1, 2, 3 ];    // false
{ a: 42 } === { a: 42 }         // false
(x => x * 2) === (x => x * 2)   // false
```

What's going on here?

It may seem reasonable to assume that an equality check considers the *nature* or *contents* of the value; after all, `42 === 42` considers the actual `42` value and compares it. But when it comes to objects, a content-aware comparison is generally referred to as "structural equality."

JS does not define `===` as *structural equality* for object values. Instead, `===` uses *identity equality* for object values.

In JS, all object values are held by reference (see "Values vs References" in Appendix A), are assigned and passed by reference-copy, **and** to our current discussion, are compared by reference (identity) equality. Consider:

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

In this snippet, `y === x` is true because both variables hold a reference to the same initial array. But the `=== [1,2,3]` comparisons both fail because `y` and `x`, respectively, are being compared to new *different* arrays `[1,2,3]`. The array structure and contents don't matter in this comparison, only the **reference identity**.

JS does not provide a mechanism for structural equality comparison of object values, only reference identity comparison. To do structural equality comparison, you'll need to implement the checks yourself.

But beware, it's more complicated than you'll assume. For example, how might you determine if two function references are "structurally equivalent"? Even stringifying to compare their source code text wouldn't take into account things like closure. JS doesn't provide structural equality comparison because it's almost intractable to handle all the corner cases!

### Coercive Comparisons

Coercion means a value of one type being converted to its respective representation in another type (to whatever extent possible). As we'll discuss in Chapter 4, coercion is a core pillar of the JS language, not some optional feature that can reasonably be avoided.

But where coercion meets comparison operators (like equality), confusion and frustration unfortunately crop up more often than not.

Few JS features draw more ire in the broader JS community than the `==` operator, generally referred to as the "loose equality" operator. The majority of all writing and public discourse on JS condemns this operator as poorly designed and dangerous/bug-ridden when used in JS programs. Even the creator of the language himself, Brendan Eich, has lamented how it was designed as a big mistake.

From what I can tell, most of this frustration comes from a pretty short list of confusing corner cases, but a deeper problem is the extremely widespread misconception that it performs its comparisons without considering the types of its compared values.

The `==` operator performs an equality comparison similarly to how the `===` performs it. In fact, both operators consider the type of the values being compared. And if the comparison is between the same value type, both `==` and `===` **do exactly the same thing, no difference whatsoever.**

If the value types being compared are different, the `==` differs from `===` in that it allows coercion before the comparison. In other words, they both want to compare values of like types, but `==` allows type conversions *first*, and once the types have been converted to be the same on both sides, then `==` does the same thing as `===`. Instead of "loose equality," the `==` operator should be described as "coercive equality."

Consider:

```js
42 == "42";             // true
1 == true;              // true
```

In both comparisons, the value types are different, so the `==` causes the non-number values (`"42"` and `true`) to be converted to numbers (`42` and `1`, respectively) before the comparisons are made.

Just being aware of this nature of `==`—that it prefers primitive numeric comparisons—helps you avoid most of the troublesome corner cases, such as staying away from a gotchas like `"" == 0` or `0 == false`.

You may be thinking, "Oh, well, I will just always avoid any coercive equality comparison (using `===` instead) to avoid those corner cases"! Eh, sorry, that's not quite as likely as you would hope.

There's a pretty good chance that you'll use relational comparison operators like `<`, `>` (and even `<=` and `>=`).

Just like `==`, these operators will perform as if they're "strict" if the types being relationally compared already match, but they'll allow coercion first (generally, to numbers) if the types differ.

Consider:

```js
var arr = [ "1", "10", "100", "1000" ];
for (let i = 0; i < arr.length && arr[i] < 500; i++) {
    // will run 3 times
}
```

The `i < arr.length` comparison is "safe" from coercion because `i` and `arr.length` are always numbers. The `arr[i] < 500` invokes coercion, though, because the `arr[i]` values are all strings. Those comparisons thus become `1 < 500`, `10 < 500`, `100 < 500`, and `1000 < 500`. Since that fourth one is false, the loop stops after its third iteration.

These relational operators typically use numeric comparisons, except in the case where **both** values being compared are already strings; in this case, they use alphabetical (dictionary-like) comparison of the strings:

```js
var x = "10";
var y = "9";

x < y;      // true, watch out!
```

There's no way to get these relational operators to avoid coercion, other than to just never use mismatched types in the comparisons. That's perhaps admirable as a goal, but it's still pretty likely you're going to run into a case where the types *may* differ.

The wiser approach is not to avoid coercive comparisons, but to embrace and learn their ins and outs.

Coercive comparisons crop up in other places in JS, such as conditionals (`if`, etc.), which we'll revisit in Appendix A, "Coercive Conditional Comparison."

## How We Organize in JS

Two major patterns for organizing code (data and behavior) are used broadly across the JS ecosystem: classes and modules. These patterns are not mutually exclusive; many programs can and do use both. Other programs will stick with just one pattern, or even neither!

In some respects, these patterns are very different. But interestingly, in other ways, they're just different sides of the same coin. Being proficient in JS requires understanding both patterns and where they are appropriate (and not!).

### Classes

The terms "object-oriented," "class-oriented," and "classes" are all very loaded full of detail and nuance; they're not universal in definition.

We will use a common and somewhat traditional definition here, the one most likely familiar to those with backgrounds in "object-oriented" languages like C++ and Java.

A class in a program is a definition of a "type" of custom data structure that includes both data and behaviors that operate on that data. Classes define how such a data structure works, but classes are not themselves concrete values. To get a concrete value that you can use in the program, a class must be *instantiated* (with the `new` keyword) one or more times.

Consider:

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

In the `Page` class, the data is a string of text stored in a `this.text` member property. The behavior is `print()`, a method that dumps the text to the console.

For the `Notebook` class, the data is an array of `Page` instances. The behavior is `addPage(..)`, a method that instantiates new `Page` pages and adds them to the list, as well as `print()` (which prints out all the pages in the notebook).

The statement `mathNotes = new Notebook()` creates an instance of the `Notebook` class, and `page = new Page(text)` is where instances of the `Page` class are created.

Behavior (methods) can only be called on instances (not the classes themselves), such as `mathNotes.addPage(..)` and `page.print()`.

The `class` mechanism allows packaging data (`text` and `pages`) to be organized together with their behaviors (e.g., `addPage(..)` and `print()`). The same program could have been built without any `class` definitions, but it would likely have been much less organized, harder to read and reason about, and more susceptible to bugs and subpar maintenance.

#### Class Inheritance

Another aspect inherent to traditional "class-oriented" design, though a bit less commonly used in JS, is "inheritance" (and "polymorphism"). Consider:

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

This `Publication` class defines a set of common behavior that any publication might need.

Now let's consider more specific types of publication, like `Book` and `BlogPost`:

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

Both `Book` and `BlogPost` use the `extends` clause to *extend* the general definition of `Publication` to include additional behavior. The `super(..)` call in each constructor delegates to the parent `Publication` class's constructor for its initialization work, and then they do more specific things according to their respective publication type (aka, "sub-class" or "child class").

Now consider using these child classes:

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

Notice that both child class instances have a `print()` method, which was an override of the *inherited* `print()` method from the parent `Publication` class. Each of those overridden child class `print()` methods call `super.print()` to invoke the inherited version of the `print()` method.

The fact that both the inherited and overridden methods can have the same name and co-exist is called *polymorphism*.

Inheritance is a powerful tool for organizing data/behavior in separate logical units (classes), but allowing the child class to cooperate with the parent by accessing/using its behavior and data.

### Modules

The module pattern has essentially the same goal as the class pattern, which is to group data and behavior together into logical units. Also like classes, modules can "include" or "access" the data and behaviors of other modules, for cooperation sake.

But modules have some important differences from classes. Most notably, the syntax is entirely different.

#### Classic Modules

ES6 added a module syntax form to native JS syntax, which we'll look at in a moment. But from the early days of JS, modules was an important and common pattern that was leveraged in countless JS programs, even without a dedicated syntax.

The key hallmarks of a *classic module* are an outer function (that runs at least once), which returns an "instance" of the module with one or more functions exposed that can operate on the module instance's internal (hidden) data.

Because a module of this form is *just a function*, and calling it produces an "instance" of the module, another description for these functions is "module factories".

Consider the classic module form of the earlier `Publication`, `Book`, and `BlogPost` classes:

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

Comparing these forms to the `class` forms, there are more similarities than differences.

The `class` form stores methods and data on an object instance, which must be accessed with the `this.` prefix. With modules, the methods and data are accessed as identifier variables in scope, without any `this.` prefix.

With `class`, the "API" of an instance is implicit in the class definition—also, all data and methods are public. With the module factory function, you explicitly create and return an object with any publicly exposed methods, and any data or other unreferenced methods remain private inside the factory function.

There are other variations to this factory function form that are quite common across JS, even in 2020; you may run across these forms in different JS programs: AMD (Asynchronous Module Definition), UMD (Universal Module Definition), and CommonJS (classic Node.js-style modules). The variations are minor (not quite compatible). However, all of these forms rely on the same basic principles.

Consider also the usage (aka, "instantiation") of these module factory functions:

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

The only observable difference here is the lack of using `new`, calling the module factories as normal functions.

#### ES Modules

ES modules (ESM), introduced to the JS language in ES6, are meant to serve much the same spirit and purpose as the existing *classic modules* just described, especially taking into account important variations and use cases from AMD, UMD, and CommonJS.

The implementation approach does, however, differ significantly.

First, there's no wrapping function to *define* a module. The wrapping context is a file. ESMs are always file-based; one file, one module.

Second, you don't interact with a module's "API" explicitly, but rather use the `export` keyword to add a variable or method to its public API definition. If something is defined in a module but not `export`ed, then it stays hidden (just as with *classic modules*).

Third, and maybe most noticeably different from previously discussed patterns, you don't "instantiate" an ES module, you just `import` it to use its single instance. ESMs are, in effect, "singletons," in that there's only one instance ever created, at first `import` in your program, and all other `import`s just receive a reference to that same single instance. If your module needs to support multiple instantiations, you have to provide a *classic module-style* factory function on your ESM definition for that purpose.

In our running example, we do assume multiple-instantiation, so these following snippets will mix both ESM and *classic modules*.

Consider the file `publication.js`:

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

To import and use this module, from another ES module like `blogpost.js`:

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

And finally, to use this module, we import into another ES module like `main.js`:

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
| The `as newBlogPost` clause in the `import` statement is optional; if omitted, a top-level function just named `create(..)` would be imported. In this case, I'm renaming it for readability sake; its more generic factory name of `create(..)` becomes more semantically descriptive of its purpose as `newBlogPost(..)`. |

As shown, ES modules can use *classic modules* internally if they need to support multiple-instantiation. Alternatively, we could have exposed a `class` from our module instead of a `create(..)` factory function, with generally the same outcome. However, since you're already using ESM at that point, I'd recommend sticking with *classic modules* instead of `class`.

If your module only needs a single instance, you can skip the extra layers of complexity: `export` its public methods directly.

## The Rabbit Hole Deepens

As promised at the top of this chapter, we just glanced over a wide surface area of the main parts of the JS language. Your head may still be spinning, but that's entirely natural after such a firehose of information!

Even with just this "brief" survey of JS, we covered or hinted at a ton of details you should carefully consider and ensure you are comfortable with. I'm serious when I suggest: re-read this chapter, maybe several times.

In the next chapter, we're going to dig much deeper into some important aspects of how JS works at its core. But before you follow that rabbit hole deeper, make sure you've taken adequate time to fully digest what we've just covered here.
