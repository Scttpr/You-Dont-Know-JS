# You Don't Know JS Yet: Get Started - 2nd Edition
# Chapitre 1 : Qu'est-ce que JavaScript ?

Vous ne connaissez pas encore JavaScript. Tout comme moi, du moins pas complètement. D'ailleurs comme aucun de nous. Cependant nous pouvons tous faire plus ample connaissance avec JavaScript.

Dans ce premier chapitre du premier livre de la série *You Don't Know JS Yet* (YDKJSY), nous allons prendre le temps de construire de solides bases pour préparer la suite. Nous allons donc commencer par explorer toute une variété d'importants détails de fond, d'effacer quelques mythes et idées fausses à propos de ce qu'est réellement le langage (et ce qu'il n'est pas).

C'est un aperçu fondamental dans l'identité et la façon dont Javascript est organisé et maintenu que tous les développeurs JS devrait comprendre. Si vous voulez faire plus amples connaissance avec JS, voici la première étape de votre voyage : débuter.

<!-- In this first chapter of the first book of the *You Don't Know JS Yet* (YDKJSY) series, we will take some time to build a foundation to move forward on. We need to start by covering a variety of important background housekeeping details, clearing up some myths and misconceptions about what the language really is (and isn't!). -->

<!-- This is valuable insight into the identity and process of how JS is organized and maintained; all JS developers should understand it. If you want to get to know JS, this is how to *get started* taking the first steps in that journey. -->

## A propos du livre

Je souligne le mot voyage car *connaître JS* n'est pas une destination, c'est une direction. Quel que soit le temps passé avec le langage, vous allez toujours trouver quelque chose à apprenddre pour le comprendre un peu mieux. Donc ne percevez pas ce livre comme quelque chose à rusher pour une prouesse de rapidité. C'est plutôt dans la patience et la persistence que vous ferez les meilleurs premiers petits pas.

<!-- I emphasize the word journey because *knowing JS* is not a destination, it's a direction. No matter how much time you spend with the language, you will always be able to find something else to learn and understand a little better. So don't look at this book as something to rush through for a quick achievement. Instead, patience and persistence are best as you take these first few steps. -->

A la suite de ce chapitre de fond, le reste du livre présente un panomara de haut-niveau de ce que vous trouverez en creusant et en étudiant le JS dans ces livres.

<!-- Following this background chapter, the rest of the book lays out a high-level map of what you will find as you dig into and study JS with the YDKJSY books. -->

En particulier, le chapitre 4 identifie trois piliers principaux autour duquel le JS est organisé: portée/closure, prototypes:objets et types/coercition. JS est un langage vaste et sophistiqué, avec beaucoup de fonctionnalités et capacités. Mais tout le JS est fondé sur ces trois piliers fondateurs.

<!-- In particular, Chapter 4 identifies three main pillars around which the JS language is organized: scope/closures, prototypes/objects, and types/coercion. JS is a broad and sophisticated language, with many features and capabilities. But all of JS is founded on these three foundational pillars. -->

Gardez à l'esprit que même si ce livre est intitulé "Débuter", il n'est pas destiné à être un livre d'introduction. Le travail principal de ce livre est de vous préparer à étudier JS profondément tout au long de la série. Il est écrit en assumant que vous êtes déjà familié avec JS avec déjà plusieurs mois d'experience. Donc pour en tirer le plus grand bénéfice, soyez certain d'avoir déjà passé beaucoup de temps à écrire du code JS pour construire votre expérience.

<!-- Keep in mind that even though this book is titled "Get Started," it's **not intended as a beginner/intro book**. This book's main job is to get you ready for studying JS deeply throughout the rest of the series; it's written assuming you already have familiarity with JS over at least several months experience before moving on in YDKJSY. So to get the most out of *Get Started*, make sure you spend plenty of time writing JS code to build up your experience. -->

Même si vous avez déjà écrit beaucoup de JS, ce livre ne devrait pas être efleuré ni sauté. Prenez votre temps pour parcourir l'ensemble de son contenu : **un bon début dépend toujours d'un solide premier pas.**

<!-- Even if you've already written a lot of JS before, this book should not be skimmed over or skipped; take your time to fully process the material here. **A good start always depends on a solid first step.** -->

## Qu'y a-t-il avec ce nom ?

Le nom JavaScript est probablement le plus mal compris des noms de langages de programmation.

<!-- The name JavaScript is probably the most mistaken and misunderstood programming language name. -->

Est-il lié à Java ? Est-ce uniquement la version scriptée de Java ? Est-ce uniquement pour écrire des scripts et non de réels programmes ?

<!-- Is this language related to Java? Is it only the script form for Java? Is it only for writing scripts and not real programs? -->

La vérité est que le nom JavaScript est un artefact une combine marketing. Quand Brendan Eich a d'abord conçu le langage, il l'a appelé Mocha. En interne à Netscape, la marque LiveScript était utilisée. Mais quand il a fallu le nommé publiquement, "JavaScript" remporta les suffrages.

<!-- The truth is, the name JavaScript is an artifact of marketing shenanigans. When Brendan Eich first conceived of the language, he code-named it Mocha. Internally at Netscape, the brand LiveScript was used. But when it came time to publicly name the language, "JavaScript" won the vote. -->

Pourquoi ? Car le langage est originellement designé pour attirer une audience principalement composée de développeurs Java et parce que le mot "script" était populaire à ce moment, faisant référent à des programmes très légers. Ces programmes ultra légers seraient les premier à s'insérer dans les pages de cette nouvelle chose appelée web !

<!-- Why? Because this language was originally designed to appeal to an audience of mostly Java programmers, and because the word "script" was popular at the time to refer to lightweight programs. These lightweight "scripts" would be the first ones to embed inside of pages on this new thing called the web! -->

En d'autre termes, JavaScript était un stratagème marketing pour positionner le langage comme une bonne alternative pour écrire le plus lourd et bien connu Java de cette époque. C'est pour cette raison qu'il aurait tout aussi bien pu s'appeler "WebJava".

<!-- In other words, JavaScript was a marketing ploy to try to position this language as a palatable alternative to writing the heavier and more well-known Java of the day. It could just as easily have been called "WebJava," for that matter. -->

Il y a quelques similitudes superficielles entre le code JavaScript et le code Java. Ces ressemblances ne proviennent pas forcément d'un développement partagé mais plutôt d'une volonté des deux langages de viser les développeurs avec des attentes assummées de syntaxe par rapport au C (et par extension au C++).

<!-- There are some superficial resemblances between JavaScript's code and Java code. Those similarities don't particularly come from shared development, but from both languages targeting developers with assumed syntax expectations from C (and to an extent, C++). -->

Par exemple on utilise le `{` pour commencer un bloc de code et `}` pour le terminer, comme en C/C++ et Java. On utilise aussi le `;` pour ponctuer la fin d'une déclaration.

<!-- For example, we use the `{` to begin a block of code and the `}` to end that block of code, just like C/C++ and Java. We also use the `;` to punctuate the end of a statement. -->

D'une certaine manière, les relations légales sont plus profonde que la syntaxe. Oracle (via Sun), l'entreprise qui possède et maintient Java a aussi déposé la marque "JavaScript" (via Netscape). Cette marque n'est presque jamais appliquée et semble de pouvoir jamais l'être à l'heure d'aujourd'hui.

<!-- In some ways, legal relationships run even deeper than the syntax. Oracle (via Sun), the company that still owns and runs Java, also owns the official trademark for the name "JavaScript" (via Netscape). This trademark is almost never enforced, and likely couldn't be at this point. -->

Pour ces raisons, certains ont suggéré qu'on utilise JS au lien de JavaScript. C'est un raccourci très commun et même un bon candidat pour vendre officiellement le langage. En effet, ces livres utilisent presque exclusivement le terme JS pour faire référence au langage.

<!-- For these reasons, some have suggested we use JS instead of JavaScript. That is a very common shorthand, if not a good candidate for an official language branding itself. Indeed, these books use JS almost exclusively to refer to the language. -->

Plus éloigné de la marque détenue par Oracle, le nom officiel du langage spécifié par le TC39 et formalisé par les standards ECMA est **ECMAScript**. En effet, depuis 2016, le nom officiel du langage a été suffixé par l'année de révision. Au moment d'écrire ces lignes, il s'agit de la version ECMAScript 2019, autrement abrégée ES2019.

<!-- Further distancing the language from the Oracle-owned trademark, the official name of the language specified by TC39 and formalized by the ECMA standards body is **ECMAScript**. And indeed, since 2016, the official language name has also been suffixed by the revision year; as of this writing, that's ECMAScript 2019, or otherwise abbreviated ES2019. -->

En d'autres termes, le JavaScript/JS qui est éxéxuté par votre navigateur ou dans Node.js est *une* implémentation du standard ES2019

<!-- In other words, the JavaScript/JS that runs in your browser or in Node.js, is *an* implementation of the ES2019 standard. -->

| NOTE: |
| :--- |
| N'utilisez pas des termes comme "JS6" ou "ES8" pour faire référence au langage. Certain le font mais ces appelations contribuent à perpétuer la confusion. Vous devriez coller à "ES20xx" ou juste "JS" |

<!-- | NOTE: |
| :--- |
| Don't use terms like "JS6" or "ES8" to refer to the language. Some do, but those terms only serve to perpetuate confusion. "ES20xx" or just "JS" are what you should stick to. | -->

Que vous l'appeliez JavaScript, JS, ECMAScript, ou ES2019, ce n'est définitivement pas une variante du langage Java !

<!-- Whether you call it JavaScript, JS, ECMAScript, or ES2019, it's most definitely not a variant of the Java language! -->

> "Java is to JavaScript as ham is to hamster." --Jeremy Keith, 2009

## Spécifications du langage

J'ai mentionné le TC39, le comité de direction technique qui gère JS. Leur première tâche est de gérer les spécifications offcieielles du langage. Il se réunit régulièrement pour valider les changements agréés qu'ils soumettent ensuite à ECMA, l'organisation qui gère les standards.

<!-- I mentioned TC39, the technical steering committee that manages JS. Their primary task is managing the official specification for the language. They meet regularly to vote on any agreed changes, which they then submit to ECMA, the standards organization. -->

La syntaxe JS et son comportement sont définis dans les spécifications ES.

<!-- JS's syntax and behavior are defined in the ES specification. -->

ES2019 est la dixième spécification/révision majeure depuis l'origine de JS en 1995, donc dans l'adresse URL officielle des spécifications hébergée par ECMA, vous toruvertez "10.0".

https://www.ecma-international.org/ecma-262/10.0/


<!-- ES2019 happens to be the 10th major numbered specification/revision since JS's inception in 1995, so in the specification's official URL as hosted by ECMA, you'll find "10.0": -->

<!-- https://www.ecma-international.org/ecma-262/10.0/ -->

Le comité TC39 est composé d'entre 50 et environ 100 différentes personnes provenant de différentes entreprises investies dans le web comme les développeurs de navigateurs (Mozilla, Google, Apple), les fabriquants d'appareils (Samsung, etc). Tous les membres sont volontaires bien que la plupart des employés de ces entreprises peuvent recevoir des compensations contre leur travail au sein du comité.

<!-- The TC39 committee is comprised of between 50 and about 100 different people from a broad section of web-invested companies, such as browser makers (Mozilla, Google, Apple) and device makers (Samsung, etc). All members of the committee are volunteers, though many of them are employees of these companies and so may receive compensation in part for their duties on the committee. -->

TC39 se réunit généralement tous les mois pour trois jours pour vérifier le travail réalisé par ses membres depuis le dernier meeting, pour discuter des problèmes et voter les propositions. Les lieux de réunions tourne entre les entreprises membre prête à accueillir l'événement.

<!-- TC39 meets generally about every other month, usually for about three days, to review work done by members since the last meeting, discuss issues, and vote on proposals. Meeting locations rotate among member companies willing to host. -->

Toutes les propositions du TC39 passent pas un processus découpé en cinq étapes. Comme nous sommes des développeurs, la première étape est le 0, de 0 à 4 donc. Vous pouvez trouver davatange d'informations ici : https://tc39.es/process-document/

<!-- All TC39 proposals progress through a five-stage process—of course, since we're programmers, it's 0-based!—Stage 0 through Stage 4. You can read more about the Stage process here: https://tc39.es/process-document/ -->

L'étape 0 signifie que quelqu'un au TC39 pense qu'une idée en vaut la peine et planifie de travailler sur le sujet. Cela signifie que beaucoup d'idées qui sont proposées par des non membres du TC39 via des réseaux informels comme les réseaux sociaux ou les billtes de blog sont vraiment des "pré-étape 0". Vous devez être un membre du TC39 pour soutenir une proposition pour être officiellement considéré comme étape 0.

<!-- Stage 0 means roughly, someone on TC39 thinks it's a worthy idea and plans to champion and work on it. That means lots of ideas that non-TC39 members "propose," through informal means such as social media or blog posts, are really "pre-stage 0." You have to get a TC39 member to champion a proposal for it to be considered "Stage 0" officially. -->

Une fois qu'une proposition atteint l'étape 4, elle est éligbile pour être incluse dans la prochaine révision anuelle du langage. Cela peut prendre de quelques mois à quelques années pour qu'une proposition passe toutes les étapes.

<!-- Once a proposal reaches "Stage 4" status, it is eligible to be included in the next yearly revision of the language. It can take anywhere from several months to a few years for a proposal to work its way through these stages. -->

Toutes les propositions sont gérées publiquement, sur le dépôt Github du TC39 : https://github.com/tc39/proposals

<!-- All proposals are managed in the open, on TC39's Github repository: https://github.com/tc39/proposals -->

Toute personne, du TC39 ou non, est encouragée à participer à ses discussions publiques et au processus de travail sur ses propositions. Cependant, seul les membres du TC39 peuvent assister aux réunions et voter les propositions et changements. Donc, de ce fait, la voie d'un membre du TC39 porte beaucoup de poids sur les futures direction que JS prendra.

<!-- Anyone, whether on TC39 or not, is welcome to participate in these public discussions and the processes for working on the proposals. However, only TC39 members can attend meetings and vote on the proposals and changes. So in effect, the voice of a TC39 member carries a lot of weight in where JS will go. -->

Contrairement à des mythes établit et perpétué frustreusement, il n'y a *pas* de multiples versions de JavaScript dans la nature. Il n'y a qu'**un JS**, le standard officiel maintenu par le TC39 et ECMA.

<!-- Contrary to some established and frustratingly perpetuated myth, there are *not* multiple versions of JavaScript in the wild. There's just **one JS**, the official standard as maintained by TC39 and ECMA. -->

Au début des années 2000, quand Microsoft a maintenu un forked et rétro-ingénieurisé (et pas totalement compatible) version de JS appelée "JScript", il y a avait légitimement "plusieurs version" de JS. Mais ces jours sont loin. Il n'est donc plus d'actualité et imprécis d'affirmer cela aujourd'hui.

<!-- Back in the early 2000s, when Microsoft maintained a forked and reverse-engineered (and not entirely compatible) version of JS called "JScript," there were legitimately "multiple versions" of JS. But those days are long gone. It's outdated and inaccurate to make such claims about JS today. -->

Tous les fabriquants de navigateurs et d'appareils majeurs se sont engagés pour garder leur implémentation de JS conforme à cette spécification centrale. Bien sûr, les moteurs développent des fonctionnalités à des époques différentes. Mais il ne devrait jamais être possible que le moteur v8 (celui de Chrome) implémente une fonctionnalité spécifiée différemment et de façon non compatible par rapport au moteur SpiderMonkey (celui de Mozilla)

<!-- All major browsers and device makers have committed to keeping their JS implementations compliant with this one central specification. Of course, engines implement features at different times. But it should never be the case that the v8 engine (Chrome's JS engine) implements a specified feature differently or incompatibly as compared to the SpiderMonkey engine (Mozilla's JS engine). -->

Cela signigie que vous pouvez apprendre **un JS** et compter sur ce même JS de partout.

<!-- That means you can learn **one JS**, and rely on that same JS everywhere. -->

### Le web dirige tout ce qui touche au JS

Alors que la liste des environnements qui execute JS s'étend constamment (des navigateurs aux serveurs (Node.js), en passant par les robots, les ampoules, etc.), l'environnement qui dirige JS est le web. En d'autres termes, la façon dont JS est implémenté pour les navigateurs web est, en tout pragmatisme, la seule réalité qui compte.

<!-- While the array of environments that run JS is constantly expanding (from browsers, to servers (Node.js), to robots, to lightbulbs, to...), the one environment that rules JS is the web. In other words, how JS is implemented for web browsers is, in all practicality, the only reality that matters. -->

Pour la majeure partie, le JS définit dans les spécifications et le JS éxécusté dans les moteurs JS des navigateurs sont les mêmes. Mais il y a quelques différentes qui nécessite d'être considérées.

<!-- For the most part, the JS defined in the specification and the JS that runs in browser-based JS engines is the same. But there are some differences that must be considered. -->

Parfois, les spécifications JS dicteront quelques nouveaux ou affiné comportements et pourtant ce ne correpondra pas exactement à comment cela marche dans les moteurs JS des navigateurs web. Une telle différence est hisrotique : les moteurs JS ont eu plus de 20ans de comportement observable autour de petits bouts de fonctionnalités sur lesquels les contenus webs en sont venu à compter dessus. De ce fait, parfois les moteurs JS refuseront de se conformer à un changement dicté par la spécification car cela pourrait casser du contenu web.

<!-- Sometimes the JS specification will dictate some new or refined behavior, and yet that won't exactly match with how it works in browser-based JS engines. Such a mismatch is historical: JS engines have had 20+ years of observable behaviors around corner cases of features that have come to be relied on by web content. As such, sometimes the JS engines will refuse to conform to a specification-dictated change because it would break that web content. -->

Dans ces cas, souvent le TC39 fera marche arrière et choisira simplement de se conformer la spécification à la réalité du web. Par exemple, TC39 a planifié d'ajouter la méthode `contains(..)` aux *Arrays* mais il se trouve que ce nom rentrait en conflit avec un vieux *framework* JS toujours utilisé par quelques sites. Ils ont donc changé le nom pour un `includes(..)` rassembleur. La même chose est arrivée pour la crise comique/tragique de la communauté JS surnommé "smooshgate", quand la méthode `flatten(..)` prévue a été finalement renommée `flat(..)`.

<!-- In these cases, often TC39 will backtrack and simply choose to conform the specification to the reality of the web. For example, TC39 planned to add a `contains(..)` method for Arrays, but it was found that this name conflicted with old JS frameworks still in use on some sites, so they changed the name to a non-conflicting `includes(..)`. The same happened with a comedic/tragic JS *community crisis* dubbed "smooshgate," where the planned `flatten(..)` method was eventually renamed `flat(..)`. -->

Mais de temps en temps, TC39 décidera que la spécification devrait fermement coller sur certains points, bien que cela assez peu probable que les moteurs JS des navigateurs web se conformeront un jour.

<!-- But occasionally, TC39 will decide the specification should stick firm on some point even though it is unlikely that browser-based JS engines will ever conform. -->

La solution ? Appendix B, "Les fonctionnalités ECMAScript additionnelles pour les navigateurs web".[^specApB]. Les spécifications JS incluent cet appendix pour détailler toute différence connue entre la spécification officielle et la réalité du JS sur le web. En d'autres termes, il y a des exceptions qui sont autorisées *seulement* pour le JS du web. Les autres environnements JS doivent suivre la loi à la lettre.

<!-- The solution? Appendix B, "Additional ECMAScript Features for Web Browsers".[^specApB] The JS specification includes this appendix to detail out any known mismatches between the official JS specification and the reality of JS on the web. In other words, these are exceptions that are allowed *only* for web JS; other JS environments must stick to the letter of the law. -->

Les sections B.1 et B.2 couvrent les *additions* au JS (syntaxes et APIs) que le JS du web iunclut, encore une fois, pour des raisons historiques mais dont TC39 ne projette pas formellement spécifier dans le coeur de JS. Des exemples : inclure le `0`- pour les octaux libéraux préfixés, le global `escape(..)` / `unescape(..)` utilitaires, String "helpers" comme `anchor(..)` et `blink()` et la méthode RegExp  `compile(..)`.

<!-- Section B.1 and B.2 cover *additions* to JS (syntax and APIs) that web JS includes, again for historical reasons, but which TC39 does not plan to formally specify in the core of JS. Examples include `0`-prefixed octal literals, the global `escape(..)` / `unescape(..)` utilities, String "helpers" like `anchor(..)` and `blink()`, and the RegExp `compile(..)` method. -->

La section B.3 inclut quelques conflits où le code peut séxécuter à la fois dans les moteurs des navigateurs web et dans les moteurs non-web mais où le comportmeent *pourrait* être différent, résultant en différents résultats. La plupart des changements listés implique des siutations qui sont labelisées comme des erreurs précoces quand le code s'éxecute en *strict mode*.

<!-- Section B.3 includes some conflicts where code may run in both web and non-web JS engines, but where the behavior *could* be observably different, resulting in different outcomes. Most of the listed changes involve situations that are labeled as early errors when code is running in strict mode. -->

L'appendix B *"Je t'ai eu"* ne sont pas souvent rencontrées mais c'est toujours une bonne idée d'éviter ces constructions pour être sûr dans le futur. Partout où il est possible, adhérez à la spécification JS et ne comptez pas sur des comportement applicables unqiuement dans certains environnements JS.

<!-- Appendix B *gotchas* aren't encountered very often, but it's still a good idea to avoid these constructs to be future safe. Wherever possible, adhere to the JS specification and don't rely on behavior that's only applicable in certain JS engine environments. -->

### Pas tout le (web) JS...
Est-ce que ce code est un programme JS ?

<!-- Is this code a JS program? -->

```js
alert("Hello, JS!");
```

Cela dépend de la façon dont vous voyez les choses. La fonction `alert(..)` présentée ici n'est pas incluse dans la spécification JS malgré le fait que ce soit le cas dans tous les environnements JS web. Toutefois, vous ne le trouverez pas dans l'Appendix B, qu'en penser ?

<!-- Depends on how you look at things. The `alert(..)` function shown here is not included in the JS specification, but it *is* in all web JS environments. Yet, you won't find it in Appendix B, so what gives? -->

Différents environnements JS (comme les moteurs JS des navigateurs, Node.js, etc.) ajoute des API au scope global de vos programmes JS qui vous donne des fonctionnalités spécifiques à l'environnement, comme pouvoir afficher une fenêtre pop-up d'alerte dans le navigateur de l'utilisateur.

<!-- Various JS environments (like browser JS engines, Node.js, etc.) add APIs into the global scope of your JS programs that give you environment-specific capabilities, like being able to pop an alert-style box in the user's browser. -->

En fait, une grande variété d'API assimilées JS comme `fetch(..)`, `getCurrentLocation(..)`, et `getUserMedia(..)` sont toutes des API web qui ressemblent à JS. Dans Node.js, on a accès à des centaines de méthodes d'API provenant de modules intégrés, comme `fs.write(..)`.

<!-- In fact, a wide range of JS-looking APIs, like `fetch(..)`, `getCurrentLocation(..)`, and `getUserMedia(..)`, are all web APIs that look like JS. In Node.js, we can access hundreds of API methods from various built-in modules, like `fs.write(..)`. -->

Un autre exemple commun est la méthode `console.log(..)` (et toutes les autres méthodes  `console.*`). Celles-ci ne sont pas spécifiées dans JS mais de part leur utilité universelle sont définies par presque tous les environnements JS, selon un consensus à peu près convenu.

<!-- Another common example is `console.log(..)` (and all the other `console.*` methods!). These are not specified in JS, but because of their universal utility are defined by pretty much every JS environment, according to a roughly agreed consensus. -->

Donc `alert(..)` et `console.log(..)` ne sont pas définis par JS. Mais ils *ressemblent* à JS. Ce sont des fonctions et des méthodes d'objets qui suivent les règles syntaxiques du JS. Les comportements derrière sont controlés par l'environnement exécutant le moteur JS, mais à la surface elles respectent JS pour pouvoir jouer dans son terrain de jeu.

<!-- So `alert(..)` and `console.log(..)` are not defined by JS. But they *look* like JS. They are functions and object methods and they obey JS syntax rules. The behaviors behind them are controlled by the environment running the JS engine, but on the surface they definitely have to abide by JS to be able to play in the JS playground. -->

La plupart des différences entre navigateurs dont les gens se plaignent avec le "JS est incohérent !" sont en fait dues au différents dans la façon dont le comportement de ses environnement fonctionne, pas dans la façon dont le JS en soi fonctionne.

<!-- Most of the cross-browser differences people complain about with "JS is so inconsistent!" claims are actually due to differences in how those environment behaviors work, not in how the JS itself works. -->

Donc un appel `alert(..)` *est* du JS mais `alert` en soi n'en est pas réellement, il s'agit juste d'un invité, ce n'est pas une partie de la spécification JS offcielle.

<!-- So an `alert(..)` call *is* JS, but `alert` itself is really just a guest, not part of the official JS specification. -->

### Ce n'est pas toujours du JS

L'utilisation de la console/REPL (Read-Evaluate-Print-Loop) de vos outils de développeurs dans le navigateur (ou dans Node) ont l'air de plutôt être un simple environnement JS au premier regard. Mais ce n'est pas vraiment le cas.

<!-- Using the console/REPL (Read-Evaluate-Print-Loop) in your browser's Developer Tools (or Node) feels like a pretty straightforward JS environment at first glance. But it's not, really. -->

Les outils développeur sont... des outils pour les développeurs. Leur premier rôle est de rendre la vie des développeurs plus simple. Ils priorisent l'expérience développeur (DX). Ce n'est *pas* leur but de précisément et purement strictement refléter toutes les nuances du comportement JS de la spécification. De ce fait, il y a beaucoup d'excentricités qui pourrait agir comme un "pigé" si vous considéré la console comme un environnement JS *pur*.

<!-- Developer Tools are... tools for developers. Their primary purpose is to make life easier for developers. They prioritize DX (Developer Experience). It is *not* a goal of such tools to accurately and purely reflect all nuances of strict-spec JS behavior. As such, there's many quirks that may act as "gotchas" if you're treating the console as a *pure* JS environment. -->

D'ailleurs, cet avantage est une bonne chose ! Je suis ravi que les outils développeurs rendent la vie des développeurs plus simple ! Je suis content qu'on ait de belles fonctionnalités comme l'auto-complete des variables/propriétés, etc. Je pointe juste du doigt le fait que nous ne pouvons et nous ne devrions pas attendre de tels outils de *toujours* strictement adhérer à la façon dont les programmes JS sont gérés car ce n'est pas leur rôle.

<!-- This convenience is a good thing, by the way! I'm glad Developer Tools make developers' lives easier! I'm glad we have nice UX charms like auto-complete of variables/properties, etc. I'm just pointing out that we can't and shouldn't expect such tools to *always* adhere strictly to the way JS programs are handled, because that's not the purpose of these tools. -->

Depuis que de tels outils varient en comportmenet d'un navigateur à un autre et depuis qu'ils ont changé (parfois fréquemment), je ne vais pas ici coder en dur chaque détail spéciifque, rendant ainsi ce livre très vite obsolète.

<!-- Since such tools vary in behavior from browser to browser, and since they change (sometimes rather frequently), I'm not going to "hardcode" any of the specific details into this text, thereby ensuring this book text is outdated quickly. -->

Je vais plutôt faire juste allusion à quelques exemples de trucs à certains points dans différents consoles d'environnements JS pour appuyer mon propos sur le fait de ne pas supposer qu'il s'agit de JS natif en les utilisant :

<!-- But I'll just hint at some examples of quirks that have been true at various points in different JS console environments, to reinforce my point about not assuming native JS behavior while using them: -->

* Que ce soit une déclaration `var` ou `function` au plus haut-niveau du *scope* global de la console crée en fait de réelle variables globales (reflétant ainsi la propriété `window` et vice-versa).
* Ce qui arrive en utilisant de multiples déclarations `let` et `const` au plus haut niveau du scope global.
* Que `"use strict";` sur une entrée de ligne (en allant à la ligne après) active le mode strict pour le reste le session de cette console, de la même façon que sur la première ligne d'un fichier .js, ainsi que la façon dont vous pouvez utiliser `"use strict";` au delà de cette première ligne et toutefois conserver ce mode strict activer pour la session
* Comment le lien par défaut du `this` en dehors du mode strict fonctionne pour les appels de cfonctions et la façon dont l'usage de l'objet global va contenir les variables globales attendues.
* Comment *l'hoisting* (voir livre 2,  *Scope & Closures*) fonctionne au sein des différentes lignes de code.
* Et beaucoup d'autre...

<!-- * Whether a `var` or `function` declaration in the top-level "global scope" of the console actually creates a real global variable (and mirrored `window` property, and vice versa!).

* What happens with multiple `let` and `const` declarations in the top-level "global scope."

* Whether `"use strict";` on one line-entry (pressing `<enter>` after) enables strict mode for the rest of that console session, the way it would on the first line of a .js file, as well as whether you can use `"use strict";` beyond the "first line" and still get strict mode turned on for that session.

* How non-strict mode `this` default-binding works for function calls, and whether the "global object" used will contain expected global variables.

* How hoisting (see Book 2, *Scope & Closures*) works across multiple line entries.

* ...several others -->

La console développeur n'essaye pas de prétendre être un compilateur JS qui gère votre code exactement de la même façon le moteur JS gèrerait un fichier .js. Elle essaye de faire en sorte que ce soit plus facile et plus rapide d'entrer quelques ligne de code et d'en voir le résultat rapidement. Il s'agit donc d'usages complètement différents, et de ce fait, ce n'est pas raisonnable de s'attendre à un outil qui gère les deux de la même façon.

<!-- The developer console is not trying to pretend to be a JS compiler that handles your entered code exactly the same way the JS engine handles a .js file. It's trying to make it easy for you to quickly enter a few lines of code and see the results immediately. These are entirely different use cases, and as such, it's unreasonable to expect one tool to handle both equally. -->

Ne pensez pas que le comportement que vous constatez dans la console des outils du développeur sont une *exacte* représentation à la lettre  de la sémantique JS. Pour cela, lisez la spécification. Pensez plutôt à la console comme un environnement "JS-friendly". Ca sera plus utile.

<!-- Don't trust what behavior you see in a developer console as representing *exact* to-the-letter JS semantics; for that, read the specification. Instead, think of the console as a "JS-friendly" environment. That's useful in its own right. -->

## Différents visages

Le terme "paradigme" dans le contexte d'un langage de programmation fait référérence à un large (presque universel) état d'esprit et une approche de structuration du code. Au sein d'un paradigme, il y a toute une myriade de cariations de style et de forme qui distinguent les programmes, incluant un nombre incalculable de libraitires, de frameworks qui laisse leur signature singulière sur un code donné.

<!-- The term "paradigm" in programming language context refers to a broad (almost universal) mindset and approach to structuring code. Within a paradigm, there are myriad variations of style and form that distinguish programs, including countless different libraries and frameworks that leave their unique signature on any given code. -->

Mais quel que soit le style individuel d'un programme, les divisions de la vue d'ensemble autour d'un paradigme sont presque toujours évidentes au premier regard pour tout programme.

<!-- But no matter what a program's individual style may be, the big picture divisions around paradigms are almost always evident at first glance of any program. -->

Des catégories de code typique au niveau d'un paradigme incluent le procédural, l'objet orienté (OO/classes) et fonctionnel (FP) :

* Le style procédural organise le code de haut en bas, dans une progression linéaire au sein d'opérations prédétérminés, souvent collectés ensemble au sein d'unités liées appelée procédures.
* Le style orienté objet organise le code en collectant la logique et les données ensemble dans des unités appelées classes
* Le style fonctionnel organise le code en fonctions (du traitement pure par opposition aux procédures) et en adaptation de ces fonctions comme valeurs

<!-- Typical paradigm-level code categories include procedural, object-oriented (OO/classes), and functional (FP):

* Procedural style organizes code in a top-down, linear progression through a pre-determined set of operations, usually collected together in related units called procedures.

* OO style organizes code by collecting logic and data together into units called classes.

* FP style organizes code into functions (pure computations as opposed to procedures), and the adaptations of those functions as values. -->

Ces paradigmes ne sont ni bon ni mauvais. Ce sont des orientations qui guide et qui forge la façon dont les développeurs aobrdent les problèmes et leurs solutions, comment ils structurent et maintiennes leur code.

<!-- Paradigms are neither right nor wrong. They're orientations that guide and mold how programmers approach problems and solutions, how they structure and maintain their code. -->

Certains langages sont fortement liés à l'un de ces paradigmes : C est procédural, Java/C++ sont presque entièrement orienté objet et Haskell is fonctionnel de bout en bout.

<!-- Some languages are heavily slanted toward one paradigm—C is procedural, Java/C++ are almost entirely class oriented, and Haskell is FP through and through. -->

Mais beaucoup de langages supporte différents modèles de code qui peuvent provenir, et même être un mix, de différents paradigmes. Ces bien nommés "langages multi-paradigmes" offre une flexibilité ultime. Dans certains cas, un programme peut même avoir deux ou plusieurs expressions de ces paradigmes se cotoyant.

<!-- But many languages also support code patterns that can come from, and even mix and match from, different paradigms. So called "multi-paradigm languages" offer ultimate flexibility. In some cases, a single program can even have two or more expressions of these paradigms sitting side by side. -->

JavaScript est sans aucun doute un langage multi-paradigme. Vous pouvez écrire du procédural, du orienté objet et du fonctionnel et vous pouvez choisir tel ou tel paradigme à chaque ligne de code plutôt que de forcer le choix vers du tout ou rien.

<!-- JavaScript is most definitely a multi-paradigm language. You can write procedural, class-oriented, or FP-style code, and you can make those decisions on a line-by-line basis instead of being forced into an all-or-nothing choice. -->

## Vers l'avant et vers l'arrière

L'un des principes fondamentaux qui guide JavaScript est la préservation de la *rétro-compatibilité*. Beaucoup de gens sont perdus vis à vis des implications de ce terme et souvent le confondent avec le terme lié mais différent de *compatbilité ascendante*.

<!-- One of the most foundational principles that guides JavaScript is preservation of *backwards compatibility*. Many are confused by the implications of this term, and often confuse it with a related but different term: *forwards compatibility*. -->

Remettons les pendules à l'heure.

<!-- Let's set the record straight. -->

La rétrocompatibilité signifie qu'une fois quelque chose accpeté comme du JS valide, il n'y aura pas de futurs changements du langage qui rendront ce code invalide. Le code écrit en 1995 (aussi primitif et limité soit-il) doit toujours fonctionner aujourd'hui. Comme le proclament souvent les membres du TC39 : "On ne casse pas le web !".

<!-- Backwards compatibility means that once something is accepted as valid JS, there will not be a future change to the language that causes that code to become invalid JS. Code written in 1995—however primitive or limited it may have been!—should still work today. As TC39 members often proclaim, "we don't break the web!" -->

L'idée est que les développeurs JS peuvent écrire du code en toute confiance en sachant que ce code ne cessera pas de fonctionner de façon inprédictible à cause du mise à jour d'un navigateur. Cela rend la décision de choisir JS pour un programme plus sage et un investissement plus sur, pour des années dans le futur.

<!-- The idea is that JS developers can write code with confidence that their code won't stop working unpredictably because a browser update is released. This makes the decision to choose JS for a program a more wise and safe investment, for years into the future. -->

Cette "garantie" n'est pas un détail. Maintenir la rétro compatbilité sur maintenant presque 25 ans d'histoire du langage crée un énorme poids et tout un tas de challenges uniques. Il vous serait difficile de trouver beaucoup d'autres exemples d'un tel travail de rétrocompatibilité.

<!-- That "guarantee" is no small thing. Maintaining backwards compatibility, stretched out across almost 25 years of the language's history, creates an enormous burden and a whole slew of unique challenges. You'd be hard pressed to find many other examples in computing of such a commitment to backwards compatibility. -->

Le cout de coller à un tel principe de devrait pas être vulgairement mis de côté. Cela crée nécessairement une bar très haute pour inclure, changer ou étendre le langage. Chaque décision devient effectivement permanente, les bonnes comme les mauvaises. Une fois que c'est du JS, cela ne peut pas être retiré car cela pourrait casser des programmes, même si on aimerait vraiment, vraiment, les retirer !

<!-- The costs of sticking to this principle should not be casually dismissed. It necessarily creates a very high bar to including changing or extending the language; any decision becomes effectively permanent, mistakes and all. Once it's in JS, it can't be taken out because it might break programs, even if we'd really, really like to remove it! -->

Il y a quelques exceptions à cette règle. JS a eu quelques changements non rétrocompatibles, mais le TC39 est extrêmement prudent à ce sujet. Il étudie le code existant sur le web (via la récolte des données des navigateurs) pour estimer l'impact de tels changements et les navigateurs décident à la fin et votent si ils sont prêts à ou non à recevoir les foures des utilisateurs pour de très petits changements comparé aux bénéfices d'améliorer ou réparer certains aspects du langages pour bien d'autres sites (et utilisateurs).

<!-- There are some small exceptions to this rule. JS has had some backwards-incompatible changes, but TC39 is extremely cautious in doing so. They study existing code on the web (via browser data gathering) to estimate the impact of such breakage, and browsers ultimately decide and vote on whether they're willing to take the heat from users for a very small-scale breakage weighed against the benefits of fixing or improving some aspect of the language for many more sites (and users). -->

Ce genre de changements sont rares et concernent presque tous des petits cas spécifiques qui ne peuvent pas évidemment casser beaucoup de sites.

<!-- These kinds of changes are rare, and are almost always in corner cases of usage that are unlikely to be observably breaking in many sites. -->

Il faut maintenant comparer la rétrocompatibilité à son homologue : la compatibilité ascendente. La compatibilité ascendante signifie qu'inclure une nouvelle addition à un langage dans un programme ne causerait pas une plantage de ce programme s'il était éxecuté par un vieux moteur JS. JS n'est pas compatible ascendamment bien que beaucoup le souhaiterait et croient incorrectement à ce mythe.

<!-- Compare *backwards compatibility* to its counterpart, *forwards compatibility*. Being forwards-compatible means that including a new addition to the language in a program would not cause that program to break if it were run in an older JS engine. **JS is not forwards-compatible**, despite many wishing such, and even incorrectly believing the myth that it is. -->

Pas opposition, HTML et CSS ne sont pas rétrocompatible mais compatible ascendemment. Si vous ressortez de l'HTML ou du CSS écrit en 1995, c'est totalement possible que celui-ci ne fonctionne pas  (ou fonctionne) aujourd'hui. Mais si vous utilisez une fonctionnalité datant de 2019 dans un navigateur de 2010, la page ne sera pas cassée mais le CSS/HTML non compatible ne sera pas traité quand le reste du HTML/CSS serait traité en conséquence.

<!-- HTML and CSS, by contrast, are forwards-compatible but not backwards-compatible. If you dug up some HTML or CSS written back in 1995, it's entirely possible it would not work (or work the same) today. But, if you use a new feature from 2019 in a browser from 2010, the page isn't "broken" -- the unrecognized CSS/HTML is skipped over, while the rest of the CSS/HTML would be processed accordingly. -->

Cela semble désirable d'inclure une compatbilité ascendente dans un design de langage de programmation, mais c'est généralement peu pratique de le faire. La structuration (HTML) ou la stylisation (CSS) sont déclaratifs par nature donc c'est beaucoup plus facile de sauter des déclarations non reconnues avec un impact minimal sur les autres déclarations reconnues.

<!-- It may seem desirable for forwards-compatibility to be included in programming language design, but it's generally impractical to do so. Markup (HTML) or styling (CSS) are declarative in nature, so it's much easier to "skip over" unrecognized declarations with minimal impact to other recognized declarations. -->

Mais le chaos et le non-déterminisme surviendrait si le moteur de langage de programmation sauterait sélectivement des déclarations (ou même des expressions !) qu'il ne comprendrait pas comme c'est impossible d'assurer qu'une partie suivante du programme n'aurait pas besoin de la partie sauter pour fonctionner.

<!-- But chaos and non-determinism would ensue if a programming language engine selectively skipped statements (or even expressions!) that it didn't understand, as it's impossible to ensure that a subsequent part of the program wasn't expecting the skipped-over part to have been processed. -->

Bien que JS ne le soit pas et ne peuve pas être compatible ascendamment, il est primordial de reconnaitre la rétrocompatibilité JS, incluant les bénéfices durables pour le web et les contraintes et difficultés pour le JS que cela engendre.

<!-- Though JS isn't, and can't be, forwards-compatible, it's critical to recognize JS's backwards compatibility, including the enduring benefits to the web and the constraints and difficulties it places on JS as a result. -->

### Jumping the Gaps

Alors que JS n'est pas compatible ascendemment, cela signifie qu'il y a toujours un potentiel écart entre le code que vous écrivez qui est du JS valide et les moteur les plus vieux que votre ou application a besoin de supporter. Si vous éxecuté un programme qui utilise une fonctionnalité ES2019 dans un moteur de 2016, vous allez très certainement voir votre programme crasher.

<!-- Since JS is not forwards-compatible, it means that there is always the potential for a gap between code that you can write that's valid JS, and the oldest engine that your site or application needs to support. If you run a program that uses an ES2019 feature in an engine from 2016, you're very likely to see the program break and crash. -->

Si la fonctionnalité est une nouvelle syntaxe, le programme échouera généralement complètement à la compilation et s'éxecueta, lançant une erreur de syntaxe. Si la fonctionnalité est une API (comme l'ES6 `Object.is(..)`), le programme pourrait se lancer pour lancer une exception pendant l'execution et stopper une fois en face de l'API inconnu.

<!-- If the feature is a new syntax, the program will in general completely fail to compile and run, usually throwing a syntax error. If the feature is an API (such as ES6's `Object.is(..)`), the program may run up to a point but then throw a runtime exception and stop once it encounters the reference to the unknown API. -->

Est-ce que cela signifie que les développeurs JS devraient toujours laguer derrière le rythme du progrès utilisant du code compatible avec les environnement de moteur JS les plus vieux dont ils ont besoin de supporter ? Non !

<!-- Does this mean JS developers should always lag behind the pace of progress, using only code that is on the trailing edge of the oldest JS engine environments they need to support? No! -->

Mais cela signifie que les développeusr JS ont besoin de porter une attention particulière pour gérer cet écart.

<!-- But it does mean that JS developers need to take special care to address this gap. -->

Pour des nouvelles et incompatibles syntaxes, la solution est la transpilation. La transpilation est un terme inventé par la communauté pour décrire un outil qui convertie le code source du programme d'une forme vers une autre (mais toujours du code source textuel). Typiquement, les problèmes de compatibilité ascendante liés à la syntaxe sont résolu en utilisant un transpilateur (le plus commun est Babel (https://babeljs.io)) pour convertir d'une version plus récente de la syntaxe JS vers un équivalent dans une ancienne syntaxe.

<!-- For new and incompatible syntax, the solution is transpiling. Transpiling is a contrived and community-invented term to describe using a tool to convert the source code of a program from one form to another (but still as textual source code). Typically, forwards-compatibility problems related to syntax are solved by using a transpiler (the most common one being Babel (https://babeljs.io)) to convert from that newer JS syntax version to an equivalent older syntax. -->

Par exemple, un développeur pourrait écrire extrait de code comme :

<!-- For example, a developer may write a snippet of code like: -->

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

Le code pourrait ressemble à ça dans l'arborescence du code source pour cette application. Mais au moment de la mise en production pour déployer sur un site public, le transpileur Babel devrait convertir ce code en quelque chose qui ressemble à ça :

<!-- This is how the code would look in the source code tree for that application. But when producing the file(s) to deploy to the public website, the Babel transpiler might convert that code to look like this: -->

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

L'extrait d'origine repose sur `let` pour créer une variable `x` dans un bloc de portée circonscrit aux proposition du `if` et du `else` sans interférer l'un sur l'autre. Un programme équivalent (avec un minimum de réécriture) que Babel peut produire est de juste choisir de nommer deux différentes variables avec des noms uniques produisant le même résultat sans interférence.

<!-- The original snippet relied on `let` to create block-scoped `x` variables in both the `if` and `else` clauses which did not interfere with each other. An equivalent program (with minimal re-working) that Babel can produce just chooses to name two different variables with unique names, producing the same non-interference outcome. -->

| NOTE: |
| :--- |
| Le mot-clé `let`a été ajouté dans ES6 (en 2015). L'exemple qui précède de transpilation serait nécessaire uniquement si une application aurait besoin de se lancer dans un environnents JS pre-ES6. L'exemple ici est juste pour la simplicité d'illustration. Quand ES6 était nouveau, le besoin pour une telle transpilation était courante, mais en 2020, c'est beaucoup moins commun d'avoir besoin de supporter des environnements pre-ES6. La "cible" utilisée pour la transpilation est donc une fenêtre coulissante qui se déplace vers l'avant au gré des décisions prises par les sites/applications de stopper le support de tel ou tel vieux navigateur/moteur. |

<!-- | NOTE: |
| :--- |
| The `let` keyword was added in ES6 (in 2015). The preceding example of transpiling would only need to apply if an application needed to run in a pre-ES6 supporting JS environment. The example here is just for simplicity of illustration. When ES6 was new, the need for such a transpilation was quite prevalent, but in 2020 it's much less common to need to support pre-ES6 environments. The "target" used for transpiliation is thus a sliding window that shifts upward only as decisions are made for a site/application to stop supporting some old browser/engine. | -->

Vous vous demandez pourquoi se lancer dans les problèmes d'un outil pour convertir d'une nouvelle syntaxe vers une ancienne ? Ne pourrions-nous pas juste écrire deux variables et ne pas utiliser le mot-clé `let`? La raison est, il est fortement recommandé aux développeurs d'utiliser la dernière version de JS pour que leur code soit propre et communique son propose plus efficacement.

<!-- You may wonder: why go to the trouble of using a tool to convert from a newer syntax version to an older one? Couldn't we just write the two variables and skip using the `let` keyword? The reason is, it's strongly recommended that developers use the latest version of JS so that their code is clean and communicates its ideas most effectively. -->

Les développeurs devraient se focaliser sur l'écriture de formes propre et nouvelles et laisser les outils s'occuper de produire des versions assurant la compatibilité ascendante de ce code pour qu'il soit adapté au déploiement et à l'éxecution dans les plus vieux environnements JS

Developers should focus on writing the clean, new syntax forms, and let the tools take care of producing a forwards-compatible version of that code that is suitable to deploy and run on the oldest-supported JS engine environments.

### Combler l'écart

Si le problème de la compatibilité ascendante  n'est pas lié à la nouvelle syntaxe mais plutôt à une méthode d'API manquante qui a été rajouté récemmenet, la solution la plus commune est de fourinir une définition pour cette méthode qui relplace et se comporte comme si un plus vieil environnement l'avait déjà nativement défini. Ce modèle s'appelle un polyfill (alias "shim).

<!-- If the forwards-compatibility issue is not related to new syntax, but rather to a missing API method that was only recently added, the most common solution is to provide a definition for that missing API method that stands in and acts as if the older environment had already had it natively defined. This pattern is called a polyfill (aka "shim"). -->

Prenons l'exemple de ce code :

<!-- Consider this code: -->

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

Ce code utilise une fonctionnalité ES2019, la méthode `finally(..)` du prototype de promesse. Si ce code était utilisé dans un environnement pre-ES2019, la méthode `finally(..)` n'existerait pas et une erreur serait jetée. 

<!-- This code uses an ES2019 feature, the `finally(..)` method on the promise prototype. If this code were used in a pre-ES2019 environment, the `finally(..)` method would not exist, and an error would occur. -->

Un polyfill pour `finally(..)` dans un environnement pre-ES2019 pourrait ressembler à ça :

<!-- A polyfill for `finally(..)` in pre-ES2019 environments could look like this: -->

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

<!-- | WARNING: |
| :--- |
| This is only a simple illustration of a basic (not entirely spec-compliant) polyfill for `finally(..)`. Don't use this polyfill in your code; always use a robust, official polyfill wherever possible, such as the collection of polyfills/shims in ES-Shim. | -->

La déclaration `if` protège la définition du polyfill en le prévenant de s'éxecuter dans tout environnement ou le moteur JS a déjà défini cette méthode. Dans de plus vieux environnements, le polyfill est défini mais dans des environnements plus récents la déclaration du `if` est sautée silencieusement.

<!-- The `if` statement protects the polyfill definition by preventing it from running in any environment where the JS engine has already defined that method. In older environments, the polyfill is defined, but in newer environments the `if` statement is quietly skipped. -->

Les transpileurs comme Babel détecte typiquemnt les polyfills dont votre code a besoin et les fournit automatiquement pour vous. Mais quelques fois, vous ourriez avoir besoin de les inclure/définir  explicitement, ce qui fonctionne de la même manière que l'extrait de code que nous venon de voir.

<!-- Transpilers like Babel typically detect which polyfills your code needs and provide them automatically for you. But occasionally you may need to include/define them explicitly, which works similar to the snippet we just looked at. -->

Ecrivez toujours du code en utilisant la fonctionnalité la plus appropriée pour communiquer ses idées et son intention efficacement. En général, cela signifie utiliser les plus récentes et stables versions de JS. Evitez d'impacter négativement la lisibilité du code en essayant d'ajuster manuellement votre syntaxe ou de combler les écarts avec des API. Les outils sont là pour ça !

<!-- Always write code using the most appropriate features to communicate its ideas and intent effectively. In general, this means using the most recent stable JS version. Avoid negatively impacting the code's readability by trying to manually adjust for the syntax/API gaps. That's what tools are for! -->

La transpilation et les polyfill sont deux techniques très efficaces pour gérer cet écart entre le code qui utilise les dernière fonctionnalités du langage et les vieux environnements qu'un site ou une application a besoin de supporter. Comme JS n'est pas prêt de s'arrêter de s'améliorer, cet écart ne partira jamais. Ces technioques devrait être embrassées comme un standard de toute chaine de production d'un projet JS pour aller vers l'avant.

<!-- Transpilation and polyfilling are two highly effective techniques for addressing that gap between code that uses the latest stable features in the language and the old environments a site or application needs to still support. Since JS isn't going to stop improving, the gap will never go away. Both techniques should be embraced as a standard part of every JS project's production chain going forward. -->

## Qu'y a-t-il dans une Interprétation ?

Une question longuement débattue pour du code écrit en JS : s'agit-il de scripts interprétés ou d'un programme compilé ? L'opinion majoritaire semble être celle selon laquelle JS est un langage (de script) interprété. Mais la vérité est plus compliqué que ça.

<!-- A long-debated question for code written in JS: is it an interpreted script or a compiled program? The majority opinion seems to be that JS is an interpreted (scripting) language. But the truth is more complicated than that. -->

Longtemps dans l'histoire des langages de programmation, les langages "interprétés" et de "script" ont été regardé de haut et jugé comme inférieur par leur homologues compilés. Les raisons de cette amertume sont nombreuses, incluant la perception selon laquelle il y a des manques dans l'optimisation des performances, l'aversion pour certaines caractéristiques de ces langages comme le fait que les langages scriptés utilisent généralement un typage dynamique au lieu d'un typage statique "plus mature".

<!-- For much of the history of programming languages, "interpreted" languages and "scripting" languages have been looked down on as inferior compared to their compiled counterparts. The reasons for this acrimony are numerous, including the perception that there is a lack of performance optimization, as well as dislike of certain language characteristics, such as scripting languages generally using dynamic typing instead of the "more mature" statically typed languages. -->

Les langages perçus comme "compilés" produisent habituellement une représentation portable (en binaire) du programme qui est distribué pour une éxecution ultérieur. Comme on observe pas vrament ce modèle avec JS (on distribue le code source et non sa version n-binaire), beaucoup déclarent éliminer JS de cette catégorie. En réalité, le modèle de distribution de la forme éxecutable d'un programme est devenue drastiquement plus varié et aussi moins pertinent au cours des dernieres décennies. Pour notre question, cela ne compte plus vraiment la forme du programme en circulation.

<!-- Languages regarded as "compiled" usually produce a portable (binary) representation of the program that is distributed for execution later. Since we don't really observe that kind of model with JS (we distribute the source code, not the binary form), many claim that disqualifies JS from the category. In reality, the distribution model for a program's "executable" form has become drastically more varied and also less relevant over the last few decades; to the question at hand, it doesn't really matter so much anymore what form of a program gets passed around. -->

Ces déclarations malinformés et ses critiques devraient être mises de côté. La réelle rauson qui compte pour avoir une image clair pour savoir si oui ou non JS est interprété ou compilé se base sur la nature de la façon dont les erreurs sont gérées.

<!-- These misinformed claims and criticisms should be set aside. The real reason it matters to have a clear picture on whether JS is interpreted or compiled relates to the nature of how errors are handled. -->

Historiquement, les langages interprétés ou scriptés sont execturé généralement de faut en bas et ligne par ligne. Il n'y a typqieuement pas de passage initial sur le programme pour le traiter avant que son exécution commence (cf Figure 1).

<!-- Historically, scripted or interpreted languages were executed in generally a top-down and line-by-line fashion; there's typically not an initial pass through the program to process it before execution begins (see Figure 1). -->

<figure>
    <img src="images/fig1.svg" width="650" alt="Interpreting a script to execute it" align="center">
    <figcaption><em>Fig. 1: Interpreted/Scripted Execution</em></figcaption>
    <br><br>
</figure>

Dans les langages interprétés ou scriptés, une erreur à la ligne 5 du programme ne sera pas découverte avant que les lignes de 1 à 4 ne soient exécutés. Surtout, une erreur à la ligne 5 pourrait être due a une condition à l'éxecution comme une variable ou valeur ayant une valeur non adaptée pour une opération, cela peut être aussi due a une déclaration ou un commande malformée à cette ligne. Suivant le contexte, différenr la gestion d'erreur à la ligne ou l'erreur a lieu peut-être un effet désirable ou non.

<!-- In scripted or interpreted languages, an error on line 5 of a program won't be discovered until lines 1 through 4 have already executed. Notably, the error on line 5 might be due to a runtime condition, such as some variable or value having an unsuitable value for an operation, or it may be due to a malformed statement/command on that line. Depending on context, deferring error handling to the line the error occurs on may be a desirable or undesirable effect. -->

Comparons ça aux langages qui ont un passage de traitement avant l'execution (typiquement appelé *parsing*)  comme illustré dans la figure 2 :

<!-- Compare that to languages which do go through a processing step (typically, called parsing) before any execution occurs, as illustrated in Figure 2: -->

<figure>
    <img src="images/fig2.svg" width="650" alt="Parsing, compiling, and executing a program" align="center">
    <figcaption><em>Fig. 2: Parsing + Compilation + Execution</em></figcaption>
    <br><br>
</figure>

Dans ce modèle de traitement, une commande invalide (comme une mauvaise syntaxe) à la ligne 5 serait identifié pendant la phase de *parsing*, avant que toute execution ait lieu et le programme ne serait pas lancé du tout. Pour identifié les erreurs de syntaxe (ou autrement appelée "statiques") il est généralement préféré d'en avoir connaissance en amont de toute exécution partielle condamnée.

<!-- In this processing model, an invalid command (such as broken syntax) on line 5 would be caught during the parsing phase, before any execution has begun, and none of the program would run. For catching syntax (or otherwise "static") errors, generally it's preferred to know about them ahead of any doomed partial execution. -->

Donc qu'ont les langages "parsés" en commun avec les langages compilés ? Tout d'abord, tous les langages compilés sont parsés. Donc un langage parsé est un peu déjà sur la voie d'être déjà compilé. Dans la théorie classique de compilation, la dernière étape après le parsing est la génération du code : produisant une forme executable.

<!-- So what do "parsed" languages have in common with "compiled" languages? First, all compiled languages are parsed. So a parsed language is quite a ways down the road toward being compiled already. In classic compilation theory, the last remaining step after parsing is code generation: producing an executable form. -->

Une fois toutes les sources du programmes complètement parsés, il est très commun que ses exécutions seront, d'une façon on d'une autre, inclut une tradiction depuis la forme parsé que le programme appelle habituellement un Arbre Syntaxique Abstrait (AST) de cette forme d'exécution.

<!-- Once any source program has been fully parsed, it's very common that its subsequent execution will, in some form or fashion, include a translation from the parsed form of the program—usually called an Abstract Syntax Tree (AST)—to that executable form. -->

En d'autres termes, les langages parsés génère egalement généralement le code avant l'execution, donc ce n'est pas tellement de s'étirer de dire que dans l'idée, ce sont des langages compilés.

<!-- In other words, parsed languages usually also perform code generation before execution, so it's not that much of a stretch to say that, in spirit, they're compiled languages. -->

Le code source JS est parsé avant sont exécution. La spécification le requière car elle demande de déterminer et reporter les erreurs précoces - statiques, dans le code comme des duplicarion de nom de paramètre - avant que le code ne s'exécute. Ces erreurs ne peuvent pas être identifiées sans que le code ait été parsé.

<!-- JS source code is parsed before it is executed. The specification requires as much, because it calls for "early errors"—statically determined errors in code, such as a duplicate parameter name—to be reported before the code starts executing. Those errors cannot be recognized without the code having been parsed. -->

Donc **JS est un langage parsé**, mais est-il *compilé* ?

<!-- So **JS is a parsed language**, but is it *compiled*? -->

La réponse est plus proche du oui que du non. Le JS parsé est converte dans une forme optimisée (binaire) et ce "code" est ensuite exécuté (Figure 2). Le moteur ne repasse généralement pas par une execution ligne par ligne (commme dans la Figure 1) après avoir terminé tout le difficile travail de parsing, cela serait trop inefficace.

<!-- The answer is closer to yes than no. The parsed JS is converted to an optimized (binary) form, and that "code" is subsequently executed (Figure 2); the engine does not commonly switch back into line-by-line execution (like Figure 1) mode after it has finished all the hard work of parsing—most languages/engines wouldn't, because that would be highly inefficient. -->

Pour pêtre précis, cette "compilation" produit un code d'octets binaires (de toute sorte), qui est ensuite passé à une "machile virutelle JS" pour l'exécution. Certains aiment dire que cette VM "interprète" le code octal. Mais du coup, cela dignifie que Java et des douzaines d'autres langages dirigé par la JVM, pour cette raison, sont interprétés plutôt que compilés. Evidemment, cela contredit l'affirmation typique selon laquelle Java/etc est un langage compilé.

<!-- To be specific, this "compilation" produces a binary byte code (of sorts), which is then handed to the "JS virtual machine" to execute. Some like to say this VM is "interpreting" the byte code. But then that means Java, and a dozen other JVM-driven languages, for that matter, are interpreted rather than compiled. Of course, that contradicts the typical assertion that Java/etc are compiled languages. -->

Il est intéressant de voi que malgré le fait que Java et JavaScript sont des langages très différents, la question de l'interprétation/compilation est très proche entre eux !

<!-- Interestingly, while Java and JavaScript are very different languages, the question of interpreted/compiled is pretty closely related between them! -->

Un autre détail est que les moteurs JS peuvent employer plusieurs passages de JIT (Just-In_time) traitement/optimisation sur le code généré après le parsing qui encore pourrait être labelisé aussi bien compilation ou intérpétation en fonction du point de vue. C'est en fait une situation fantastiquement complexe sous le capot du moteur JS.

<!-- Another wrinkle is that JS engines can employ multiple passes of JIT (Just-In-Time) processing/optimization on the generated code (post parsing), which again could reasonably be labeled either "compilation" or "interpretation" depending on perspective. It's actually a fantastically complex situation under the hood of a JS engine. -->

Alors quid de ces petits détails ? Prenons un pas de recul et considérons la totalité de l'écoulement d'un programme source JS :

<!-- So what do these nitty-gritty details boil down to? Step back and consider the entire flow of a JS source program: -->

1. Après qu'un programme ait quitté l'éditeur d'un développeur, il est transpilé par Babel, empaqueté par Webpack (et potentiellement une demi douzaine d'autre processus de construction) puis il est délivré dans cette forme bien différente au moteur JS.
2. Le moteur JS pars le code vers un AST
3. Le moteur convertie l'AST dans une sorte de code octal, un représentation binaire intermédiaire (IR) qui est convertie/affinée encore plus par l'optimisant compilateur JIT.
4. Finalement la machine virtuelle JS exécute le programme

Pour visualiser de nouveau ces étapes :

<!-- 1. After a program leaves a developer's editor, it gets transpiled by Babel, then packed by Webpack (and perhaps half a dozen other build processes), then it gets delivered in that very different form to a JS engine.

2. The JS engine parses the code to an AST.

3. Then the engine converts that AST to a kind-of byte code, a binary intermediate representation (IR), which is then refined/converted even further by the optimizing JIT compiler.

4. Finally, the JS VM executes the program.

To visualize those steps, again: -->

<figure>
    <img src="images/fig3.svg" width="650" alt="Steps of JS compilation and execution" align="center">
    <figcaption><em>Fig. 3: Parsing, Compiling, and Executing JS</em></figcaption>
    <br><br>
</figure>

Est-ce que JS est géré davantage comme un langage interprété ligne par ligne comme dans la Figure 1 ou est est-il plus proche d'un langage compilé traité par un ou plusieurs passages avant exécution (comme dans les Figures 2 et 3) ?

<!-- Is JS handled more like an interpreted, line-by-line script, as in Figure 1, or is it handled more like a compiled language that's processed in one-to-several passes first, before execution (as in Figures 2 and 3)? -->

Je pense qu'il est clair que dans l'esprit, si ce n'est dans la pratique, **JS est un langage compilé**.

<!-- I think it's clear that in spirit, if not in practice, **JS is a compiled language**. -->

Et de nouveau, la raison qui compte, comme JS est compilé, ous sommes informés des erreurs statiques (comme les erreurs de syntaxes) avant que le code soit exécuté. C'est un modèle d'interaction substantiellement différent que l'ont avec les programmes scriptés et sans doute plus utile !


<!-- And again, the reason that matters is, since JS is compiled, we are informed of static errors (such as malformed syntax) before our code is executed. That is a substantively different interaction model than we get with traditional "scripting" programs, and arguably more helpful! -->

### Web Assembly (WASM)

Une préoccupation dominante qui a conduit un grand nombre d'évolution du JS est la performance, aussi bien concernant la vitesse à lquelle le JS peut être  parsé/compilé que la vitesse à laquelle ce code compilé peut -être éxécuté.

<!-- One dominating concern that has driven a significant amount of JS's evolution is performance, both how quickly JS can be parsed/compiled and how quickly that compiled code can be executed. -->

En 2013, des ingénieurs de Mozilla Firefox ont fait une démonstration d'un portage du moteur de jeu Unreal 3 de C  vers JS. La capacité pour ce code d'être exécutable dans le moteur JS d'un navigateur à 60fps affirmait un jeu d'optimisations que le que le moteur JS pourrait réaliser spécifiquement car la version JS du code du moteur Unreal utilisait un style de code qui favorisait un sous-ensemble du langage appelé "ASM.js".

<!-- In 2013, engineers from Mozilla Firefox demonstrated a port of the Unreal 3 game engine from C to JS. The ability for this code to run in a browser JS engine at full 60fps performance was predicated on a set of optimizations that the JS engine could perform specifically because the JS version of the Unreal engine's code used a style of code that favored a subset of the JS language, named "ASM.js". -->

Ce sous-ensemble est du JS valide écrit d'une manière peu commune pour du code normal mais qui spécifie certaines informations de typage important au moteur qui lui permettent de réaliser des optimisations clés. ASM.js a été introduit comme une façon d'aborder les pressions sur les performances à l'execution du JS.

<!-- This subset is valid JS written in ways that are somewhat uncommon in normal coding, but which signal certain important typing information to the engine that allow it to make key optimizations. ASM.js was introduced as one way of addressing the pressures on the runtime performance of JS. -->

Cependant il est important de note que l'ASM.js n'a jamais été prévu pour être codé par des développeurs mais pmitôt d'être une représentation d'un programme transpilé depuis un autre langage (comme le C) où ces annoations de typage étaient insérées automatiquement par l'outil.

<!-- But it's important to note that ASM.js was never intended to be code that was authored by developers, but rather a representation of a program having been transpiled from another language (such as C), where these typing "annotations" were inserted automatically by the tooling. -->

Plusoeurs années après qu'ASM.js ait démontré la validté de créer des versions de programme via les outils pour être traité plus efficaceme,t par le moteur JS, un autre groupe d'ingénirueus (provenant aussi initialement de Mozilla) ont sorti le Web Assembly (WASM).

<!-- Several years after ASM.js demonstrated the validity of tooling-created versions of programs that can be processed more efficiently by the JS engine, another group of engineers (also, initially, from Mozilla) released Web Assembly (WASM). -->

WASM est similaire à ASM.js car son idée de départ est de fournir un chemon pour des programmes non JS (C, etc) pour être converti vers une forme qui pourrait être exécuté par un moteur JS. Contrairement à ASM.js, WASM a aussi choisi d'aborder certains des délais inhérents au parsing/compilation avant que le programme ne s'execute en représentant le programme dans une forme qui est entièrement différente du JS.

<!-- WASM is similar to ASM.js in that its original intent was to provide a path for non-JS programs (C, etc.) to be converted to a form that could run in the JS engine. Unlike ASM.js, WASM chose to additionally get around some of the inherent delays in JS parsing/compilation before a program can execute, by representing the program in a form that is entirely unlike JS. -->

WASM est un format beaucoup plus proche de l'assembleur (d'où son nom) qui peut être traité par le moteur JS en sautant le parsing/compilation qu ele moteur JS réalise normalement. Le parsing/compilation d'un programme en WASM se passe en avance de phase (AOT). Ce qui est distribué est un programme emballé en binaire prêt à être exécute avec un minimum de traitement pour le moteur JS.

<!-- WASM is a representation format more akin to Assembly (hence, its name) that can be processed by a JS engine by skipping the parsing/compilation that the JS engine normally does. The parsing/compilation of a WASM-targeted program happen ahead of time (AOT); what's distributed is a binary-packed program ready for the JS engine to execute with very minimal processing. -->

La motivation initiale pour WASM était clairement de potentiellement améliorer les perforances. Alors que cela continue d'être un sujet, WASM est additionnelement motivé par le désir d'apporter plus de parité aux langages non JS vers les plateformes web. Par exemple, si un langage comme Go supporte la programmation threaded alors que le JS ne le peut pas, WASM offre le potentiel pour un tel programme en GO dêtre converti dans une forme que le moteur JS peut comprendre sans avoir besoin d'une fonctionnalité de threading dans le langage JS en lui même.

<!-- An initial motivation for WASM was clearly the potential performance improvements. While that continues to be a focus, WASM is additionally motivated by the desire to bring more parity for non-JS languages to the web platform. For example, if a language like Go supports threaded programming, but JS (the language) does not, WASM offers the potential for such a Go program to be converted to a form the JS engine can understand, without needing a threads feature in the JS language itself. -->

En d'autres temres, WASM soulage la pression d'ajouter de nouvelles fonctionnalités au JS qui sont majoritairement/exclusivement destiné à être utilisé par des programmes transpilés depuis d'autres langages. Cela signifie que le le développement des fonctionnalités JS peut être jugé (par le TC39) sans être biaisé par les demandes et intérêts des écosystèmes des autres langages tout en permettant à ces langages d'avoir un chemin viable vers le web.

<!-- In other words, WASM relieves the pressure to add features to JS that are mostly/exclusively intended to be used by transpiled programs from other languages. That means JS feature development can be judged (by TC39) without being skewed by interests/demands in other language ecosystems, while still letting those languages have a viable path onto the web. -->

Une autre perspective qui émerge avec le WASM n'est pas directement lié au web (W). WASM est en train d'évoluer pour devenir une sorte de machine virtuelle multi-mateforme où les programmes peuvent être compilés une fois puis lancé dans une variété de différents environnements systèmes.

<!-- Another perspective on WASM that's emerging is, interestingly, not even directly related to the web (W). WASM is evolving to become a cross-platform virtual machine (VM) of sorts, where programs can be compiled once and run in a variety of different system environments. -->

Donc WASM n'est pas seulement pour le web et WASM n'est pas non plus du JS. Ironiquement, même si WASM s'exécute dans le moteur JS, le langage JS est l'un des moins approprié pour sourcer des programmes WASM, car WASM repose lourdement sur des informations de typage statique. Même TypeScript (TS) - ostensiblement JS + du typage static - n'est pas bien approprié (tel qu'il est) pour être transpilé en WASM, bien que des variantes du langage comme AssemblyScript tentent de réduire l'écart entre JS/TS et WASM.

<!-- So, WASM isn't only for the web, and WASM also isn't JS. Ironically, even though WASM runs in the JS engine, the JS language is one of the least suitable languages to source WASM programs with, because WASM relies heavily on static typing information. Even TypeScript (TS)—ostensibly, JS + static types—is not quite suitable (as it stands) to transpile to WASM, though language variants like AssemblyScript are attempting to bridge the gap between JS/TS and WASM. -->

Ce livre ne porte pas sur WASM donc je ne pas passer trop de temps à l'aborder, excepté pour mon point final. *Certains* ont suggéré que WASM pointe vers un futur où JS est retiré, ou minimise, du web. Ces personnes sont malades du JS et veulent n'import quel langage pour le remplacer ! Comme WASM permet à dautres langages d'etre exécuté par le moteur JS, ce n'est pas tellement un conte de féées fantaisiste.

<!-- This book isn't about WASM, so I won't spend much more time discussing it, except to make one final point. *Some* folks have suggested WASM points to a future where JS is excised from, or minimized in, the web. These folks often harbor ill feelings about JS, and want some other language—any other language!—to replace it. Since WASM lets other languages run in the JS engine, on its face this isn't an entirely fanciful fairytale. -->

Mais laisser moi juste déclarer : WASM ne remplacera pas JS. WASM augmente significativement ce que le web (JS inclus) peut accomplir. C'est une super chose, complètement indépendante de si oui non les gens l'utiliseratont pour s'charper de l'obligation d'écrire du JS.

<!-- But let me just state simply: WASM will not replace JS. WASM significantly augments what the web (including JS) can accomplish. That's a great thing, entirely orthogonal to whether some people will use it as an escape hatch from having to write JS. -->

## Parlons *strict*

En 2009 avec la sortie de l'ES5, JS a ajouté le *mode strict* comme un méchanisme pour ecouragé le développement de meilleurs programmes JS.

<!-- Back in 2009 with the release of ES5, JS added *strict mode* as an opt-in mechanism for encouraging better JS programs. -->

Les bénéfices du mode strict dépasse largement son cout, mais les vieilles habitudes ont du mal à disparaitre et l'inertie de codes existant (alias "legacy") est très difficile à changer. Donc malheureusement, plus de 10 ans plus tard, l'optionnalité du mode strict montre qu'il n'est toujours pas nécessairement la base des développeurs JS. 

<!-- The benefits of strict mode far outweigh the costs, but old habits die hard and the inertia of existing (aka "legacy") code bases is really hard to shift. So sadly, more than 10 years later, strict mode's *optionality* means that it's still not necessarily the default for JS programmers. -->

Pourquoi le mode strict ? Le mode strict ne devrait pas être pensé comme une restriction de ce que vous pouvez ou ne pouvez pas faire mais plutpiot comme un guide de la meillere façon de faire pour que le moteur JS ait la meilleure chance d'optimiser efficacement l'éxecution du code. La plupart du code JS es tréalisé par des équipes de développeurs, donc la *strictivité* du mode strict (avec les outils comme les linters !) sont souvent des aides à la collaboration sur le code pour éviter des erreurs problématiques qui peuvent se glisser sans le mode strict.

<!-- Why strict mode? Strict mode shouldn't be thought of as a restriction on what you can't do, but rather as a guide to the best way to do things so that the JS engine has the best chance of optimizing and efficiently running the code. Most JS code is worked on by teams of developers, so the *strict*-ness of strict mode (along with tooling like linters!) often helps collaboration on code by avoiding some of the more problematic mistakes that slip by in non-strict mode. -->

La plupart des contrôles du mode strict prennent la forme d'*erreurs précoces*, signifiant que ces erreurs ne son pas strictitement des erreurs de syntaxe mais sont qand même lancé au moment de la compilation (avant que le code soit exécuté). Par exemple, le mode strict n'autorise pas d'avoir deux paramètres de fonctions du même nom, et mène à une erreur précode. Quelques autres contrôles du mode strict s'observent uniquement à l'exécution comme le fait que le `this` se définisse par défaut comme `undefined` plutôt que dans l'objet global.

<!-- Most strict mode controls are in the form of *early errors*, meaning errors that aren't strictly syntax errors but are still thrown at compile time (before the code is run). For example, strict mode disallows naming two function parameters the same, and results in an early error. Some other strict mode controls are only observable at runtime, such as how `this` defaults to `undefined` instead of the global object. -->

Plutôt que de se battre et d'argumenter avec le mode strict, comme un enfant qui veut juste défier ce que ses parents lui disent, le meilleir était d'esprit est de percevoir le mode strict comme un linter qui vous rappelle comment le JS *devrait* être écrit pour avoir la meilleure qualité et la meilleur chance d'être performant. Si vous vous sentez menoté, essayant de contourner le mode strict, cela devrait être un drapeau rouge d'avertissement comme quoi vous devez revenir en arrière et repenser votre approche dans sa globalité.

<!-- Rather than fighting and arguing with strict mode, like a kid who just wants to defy whatever their parents tell them not to do, the best mindset is that strict mode is like a linter reminding you how JS *should* be written to have the highest quality and best chance at performance. If you find yourself feeling handcuffed, trying to work around strict mode, that should be a blaring red warning flag that you need to back up and rethink the whole approach. -->

Le mode strict est activé par fichier via un pragma special (rien n'est autorisé avant à l'exception des commentaires et des espaces) :

<!-- Strict mode is switched on per file with a special pragma (nothing allowed before it except comments/whitespace): -->

```js
// only whitespace and comments are allowed
// before the use-strict pragma
"use strict";
// the rest of the file runs in strict mode
```

| ATTENTION: |
| :--- |
| Il faut savoir que même un `;` perdu seul avant le pragma du mode strict rendra ce pragma inutile. Aucunes erreurs ne seront lancées car il s'agit de JS valide d'avoir l'expression d'une chaine littérale dans une poistion de déclaration mais cela n'allumera silencieusement pas le mode strict !  |

<!-- | WARNING: |
| :--- |
| Something to be aware of is that even a stray `;` all by itself appearing before the strict mode pragma will render the pragma useless; no errors are thrown because it's valid JS to have a string literal expression in a statement position, but it also will silently *not* turn on strict mode! | -->

Le mode strict peut aussi être allumé dans la portée d'une fonction, avec exactement les même règles :

<!-- Strict mode can alternatively be turned on per-function scope, with exactly the same rules about its surroundings: -->

```js
function someOperations() {
    // whitespace and comments are fine here
    "use strict";

    // all this code will run in strict mode
}
```

C'est intéressant de noter que si un fichier a le mode strict activé, les pragmas de mode strict dans les fonctions ne sont pas autorisé. Donc vous devez choisir entre l'un ou l'autre.

<!-- Interestingly, if a file has strict mode turned on, the function-level strict mode pragmas are disallowed. So you have to pick one or the other. -->

La **seule** bonne raison d'utiliser une approche par fonction est quand vous convertissez un fichier de programme non strict que vous voulez changer petit bout par petit bout dans le temps. Sinon, c'est largement mieux de simplement activer le mode strict pour la totalité du fichier/programme.

<!-- The **only** valid reason to use a per-function approach to strict mode is when you are converting an existing non-strict mode program file and need to make the changes little by little over time. Otherwise, it's vastly better to simply turn strict mode on for the entire file/program. -->

Beaucoup se sont demander s'il y aurait un moment où JS rendrait le mode strict par défaut ? La réponse est, presque certainement non. Comme nous l'avons discuté plutôt à propose de la rétrocompatibilité, si une mise à jour de moteur JS considère que le mode strict, même s'il n'est pas inscrit comme tel, il est possible que le code casse en raison des controles apportés par le mode strict.

<!-- Many have wondered if there would ever be a time when JS made strict mode the default? The answer is, almost certainly not. As we discussed earlier around backwards compatibility, if a JS engine update started assuming code was strict mode even if it's not marked as such, it's possible that this code would break as a result of strict mode's controls. -->

Cependant, il y a quelques facteurs qui réduisent le futur impact de cette décision de ne pas rendre le strict mode par défaut.

<!-- However, there are a few factors that reduce the future impact of this non-default "obscurity" of strict mode. -->

D'abord car tous le code virtuellement transpilté fiini en mode strict même si la source du code ne le spécifie pas/ La plupart du code JS produit est transpilé cela signifie donc que la plupart du JS adhère déjà au mode strict. Il est possible de défaire ce paramétrage mais vous devrez aller vraiment le vouloir donc c'est assez peu problable.

<!-- For one, virtually all transpiled code ends up in strict mode even if the original source code isn't written as such. Most JS code in production has been transpiled, so that means most JS is already adhering to strict mode. It's possible to undo that assumption, but you really have to go out of your way to do so, so it's highly unlikely. -->

De plus, un vaste changement est en train d'arriver envers la plupart de nouveau code JS écrit en utilisant le format des modules ES6. Les modules ES6 suppose le mode strict donc tout le code de ces fichiers est automatiquement en mode strict par défaut.

<!-- Moreover, a wide shift is happening toward more/most new JS code being written using the ES6 module format. ES6 modules assume strict mode, so all code in such files is automatically defaulted to strict mode. -->

Pris ensemble, le mode strict est donc largement de facto par défaut même si techniqement il ne l'est pas réellement.

<!-- Taken together, strict mode is largely the de facto default even though technically it's not actually the default. -->

## Défini

JS est une implémentation du standard ECMAScript (Au moment d'écrire ces lignes, à la version ES2019), qui est guidé par le comité du TC39 et hébergé par ECMA. Il est exécuté dans les navigateurs et les environnements JS tels que Node.js.

<!-- JS is an implementation of the ECMAScript standard (version ES2019 as of this writing), which is guided by the TC39 committee and hosted by ECMA. It runs in browsers and other JS environments such as Node.js. -->

JS est un langage multi-paradigme, signifiant que la syntaxe et ses possibilités permettent au développeurs de mixer, d'harmoniser (de se plier ou de reformer) des concepts provenant de différents paradigmes majeurs comme le procédural, l'orienté objet et le fonctionnel.

Js est un langage compilé, signifiant que les outils (incluant le moteur JS) traiter et vérifie le programme (rapportant les erreurs !) avant son exécution.

Avec notre langage *défini*, lançons nous dans la découverte de ses tenants et aboutissants.

<!-- JS is a multi-paradigm language, meaning the syntax and capabilities allow a developer to mix and match (and bend and reshape!) concepts from various major paradigms, such as procedural, object-oriented (OO/classes), and functional (FP).

JS is a compiled language, meaning the tools (including the JS engine) process and verify a program (reporting any errors!) before it executes.

With our language now *defined*, let's start getting to know its ins and outs. -->

[^specApB]: ECMAScript 2019 Language Specification, Appendix B: Additional ECMAScript Features for Web Browsers, https://www.ecma-international.org/ecma-262/10.0/#sec-additional-ecmascript-features-for-web-browsers (latest as of time of this writing in January 2020)
