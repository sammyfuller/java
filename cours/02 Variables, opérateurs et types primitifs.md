---


---

<h1 id="chapitre-2">Chapitre 2</h1>
<h1 id="variables-opérateurs-et-types-primitifs">Variables, opérateurs et types primitifs</h1>
<p>Ce chapitre vous apprendra notamment à écrire des instructions utilisant des <strong>variables</strong>, qui stockent des valeurs (entiers, mots…) et des <strong>opérateurs</strong>, des symboles qui exécutent des opérations.</p>
<h2 id="déclaration-de-variables">Déclaration de variables</h2>
<p>L’une des plus puissantes capacités d’un langage de programmation est de pouvoir définir et manipuler des variables. Une <strong>variable</strong> est un emplacement en mémoire auquel on donne un nom et qui stocke une valeur. Une <strong>valeur (value)</strong> peut être un nombre, un texte, une image, un son ou d’autres types de données. Pour stocker une valeur, vous devez d’abord <strong>déclarer une variable</strong>.</p>
<pre class=" language-java"><code class="prism  language-java">String message<span class="token punctuation">;</span>
</code></pre>
<p>Cette instruction s’appelle une <strong>déclaration</strong> : elle déclare la variable nommée <code>message</code> de type <code>String</code>.</p>
<blockquote>
<p>Le type <code>String</code> (notez la majuscule) désigne une <strong>chaîne de caractères</strong> : une séquence de caractères, encadrée par des guillemets. Les caractères peuvent être des lettres, des chiffres, de la ponctuation, des symboles, des espaces, des passages à la ligne, etc. <code>String</code> n’est pas un type primitif Java, mais une <em>classe</em> (nous verrons cela plus loin).</p>
</blockquote>
<p>En Java, <strong>toutes</strong> les variables ont un <strong>type</strong> bien défini qui détermine quelles valeurs elles peuvent stocker. Par exemple, le type <code>int</code> peut stocker des entiers, et <em>uniquement</em> des entiers. On dit que Java est un langage <strong>à typage statique</strong>, par opposition aux langages dits <strong>à typage dynamique</strong>, dans lesquels une variable peut stocker n’importe quel type de valeur (ex: PHP, JavaScript).</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span> x<span class="token punctuation">;</span>
String firstName<span class="token punctuation">;</span>
String lastName<span class="token punctuation">;</span>
<span class="token keyword">int</span> hour<span class="token punctuation">,</span> minute<span class="token punctuation">;</span>  <span class="token comment">// déclaration multiple</span>
</code></pre>
<blockquote>
<p>Comme pour toute instruction Java, une déclaration de variable se termine obligatoirement par un point-virgule.</p>
</blockquote>
<blockquote>
<p><code>x</code> n’est pas <em>a priori</em> un très bon nom pour une variable. En général, on devrait toujours utiliser des noms qui indiquent le plus clairement et le plus concisément possible ce que la variable représente (c’est un exercice beaucoup plus compliqué qu’il n’y parait).</p>
</blockquote>
<p>Rappelons que Java est sensible à la casse. La convention pour le nommage des variables en Java est celle du <em>camelCase</em> :</p>
<ul>
<li>tous les mots sont collés ;</li>
<li>tout en minuscules, sauf la première lettre de chaque mot à partir du deuxième.</li>
<li>ex: <code>i, index, firstName, nbFrags, tailleDeMarge</code></li>
</ul>
<p>Il y a des mots réservés en Java (<code>class, int, static, public, if</code> et des dizaines d’autres) que vous ne pouvez pas utiliser, car ils sont utilisés pour structurer le programme. Le compilateur se chargera de vous prévenir si vous enfreignez cette règle.</p>
<h2 id="affectation-assignment">Affectation (<em>Assignment</em>)</h2>
<p>Maintenant que nous savons déclarer des variables, nous allons pouvoir les utiliser pour stocker des valeurs. C’est l’instruction d’<strong>affectation</strong>.</p>
<pre class=" language-java"><code class="prism  language-java">String message<span class="token punctuation">;</span>
<span class="token keyword">int</span> hour<span class="token punctuation">,</span> minute<span class="token punctuation">;</span>

message <span class="token operator">=</span> <span class="token string">"Salut !"</span><span class="token punctuation">;</span>
hour <span class="token operator">=</span> <span class="token number">11</span><span class="token punctuation">;</span>
minute <span class="token operator">=</span> <span class="token number">59</span><span class="token punctuation">;</span>
</code></pre>
<p>Voici donc trois affectations. On dit qu’on <strong>affecte (<em>assign</em>)</strong> la valeur <code>11</code> à la variable <code>hour</code>, ou encore qu’on <strong>attribue</strong> la valeur <code>"Salut !"</code> à la variable <code>message</code>. On rappelle qu’une variable doit avoir le même type que la valeur qu’on lui affecte.</p>
<pre class=" language-java"><code class="prism  language-java">hour <span class="token operator">=</span> <span class="token string">"onze"</span><span class="token punctuation">;</span>    <span class="token comment">// Erreur de compilation</span>
message <span class="token operator">=</span> <span class="token number">123</span><span class="token punctuation">;</span>    <span class="token comment">// Erreur de compilation</span>
message <span class="token operator">=</span> <span class="token string">"123"</span><span class="token punctuation">;</span>  <span class="token comment">// OK</span>
</code></pre>
<p>Une variable doit être <strong>initialisée</strong> (c’est-à-dire qu’elle doit avoir reçu une valeur) <em>avant</em> d’être utilisée dans une expression. Vous pouvez déclarer puis affecter une valeur en deux temps, comme nous l’avons fait jusqu’à présent, ou bien déclarer et initialiser en même temps :</p>
<pre class=" language-java"><code class="prism  language-java">String message <span class="token operator">=</span> <span class="token string">"Salut !"</span><span class="token punctuation">;</span>
<span class="token keyword">int</span> hour <span class="token operator">=</span> <span class="token number">11</span><span class="token punctuation">,</span> minute <span class="token operator">=</span> <span class="token number">59</span><span class="token punctuation">;</span>
</code></pre>
<p>Une erreur commune en Java est de confondre l’opérateur d’affectation (<code>=</code>) avec le concept mathématique d’égalité. En mathématiques, <code>a = 7</code> ou <code>7 = a</code> sont équivalents (commutativité). L’affectation, elle, se fait de droite à gauche. Ainsi <code>7 = a;</code> n’est pas légal en Java car <code>7</code> n’est pas un nom de variable.</p>
<p>De plus, une variable (comme le nom l’indique) peut voir sa valeur varier tout au long de son existence. L’affectation d’une variable à une autre n’entraîne pas que les deux variables auront toujours la même valeur par la suite.</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span> a <span class="token operator">=</span> <span class="token number">5</span><span class="token punctuation">;</span>
<span class="token keyword">int</span> b <span class="token operator">=</span> a<span class="token punctuation">;</span>  <span class="token comment">// les valeurs de a et b sont les mêmes</span>
a <span class="token operator">=</span> <span class="token number">3</span><span class="token punctuation">;</span>      <span class="token comment">// les valeurs de a et b ne sont plus les mêmes</span>
</code></pre>
<p>Cela diffère de nouveau du signe mathématique : en math, si <code>a = b</code> dans une démonstration, cela reste vrai pour la suite.</p>
<h2 id="afficher-la-valeur-des-variables">Afficher la valeur des variables</h2>
<p>Vous pouvez afficher la valeur courante d’une variable en utilisant <code>print</code> ou <code>println</code>. Cela peut être requis dans votre programme mais il peut également être utile d’afficher à l’écran le contenu de certaines variables à un moment donné pendant la phase de développement, pour vérifier que tout se passe bien et traquer les erreurs éventuelles.</p>
<pre class=" language-java"><code class="prism  language-java">String firstLine <span class="token operator">=</span> <span class="token string">"Salut !"</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span>firstLine<span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">int</span> hour <span class="token operator">=</span> <span class="token number">11</span><span class="token punctuation">;</span>
<span class="token keyword">int</span> minute <span class="token operator">=</span> <span class="token number">59</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">" Il est "</span> <span class="token operator">+</span> hour <span class="token operator">+</span> <span class="token string">":"</span> <span class="token operator">+</span> minute <span class="token operator">+</span> <span class="token string">"."</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p><code>&gt; Salut ! Il est 11:59.</code></p>
<blockquote>
<p>j’utiliserai la notation <code>&gt;</code> pour indiquer qu’il s’agit de la sortie du programme (ce qu’il affiche)</p>
</blockquote>
<blockquote>
<p>Notez ici l’utilisation très pratique de l’opérateur <code>+</code> pour les <code>String</code> : il n’opère pas d’addition mais effectue une <strong>concaténation</strong>, en convertissant au besoin les entiers en <code>String</code>.</p>
</blockquote>
<blockquote>
<p>Même si vous utilisez plusieurs instructions <code>print</code> consécutivement, n’oubliez pas d’effectuer un <code>println</code> (même vide) à la fin. Sur certains systèmes, les résultats de <code>print</code> sont stockés dans un tampon et pas forcément affichés immédiatement. Un <code>println</code> force l’affichage (<em>flush</em>,  “vider le tampon”).</p>
</blockquote>
<h2 id="les-opérateurs-arithmétiques">Les opérateurs arithmétiques</h2>
<p>Un <strong>opérateur</strong> est un symbole qui représente une opération simple (pas forcément mathématique). Les opérations arithmétiques courantes sont représentées en Java par les opérateurs <code>+, -, *, /</code>.</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span> hour <span class="token operator">=</span> <span class="token number">11</span><span class="token punctuation">;</span>
<span class="token keyword">int</span> minute <span class="token operator">=</span> <span class="token number">59</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span><span class="token string">"Nombre de minutes depuis minuit : "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>hour <span class="token operator">*</span> <span class="token number">60</span> <span class="token operator">+</span> minute<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p><code>&gt; Nombre de minutes depuis minuit : 719</code></p>
<p><code>hour * 60 + minute</code> est une <strong>expression</strong>, qui représente une valeur unique qui sera calculée à l’exécution (ici, <code>719</code>). Quand le programme est exécuté et qu’une expression doit être évaluée, chaque variable est remplacée par sa valeur courante et les opérateurs sont appliqués pour fournir un résultat. Le résultat est ensuite utilisé dans l’instruction qui contient la ou les expressions. Voici ce que fait la JVM :</p>
<ol>
<li><code>hour * 60 + minute</code></li>
<li><code>11 * 60 + 59</code></li>
<li><code>660 + 59</code></li>
<li><code>719</code></li>
<li><code>System.out.println(719);</code></li>
</ol>
<p>Java tient compte de la précédence mathématique (du <code>*</code> sur le <code>+</code>, par exemple). Si les opérateurs ont la même précédence, les opérations sont effectuées de gauche à droite. Pour forcer un ordre spécifique et passer outre les précédences, utilisez des parenthèses.</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span> res1 <span class="token operator">=</span> <span class="token number">1</span> <span class="token operator">+</span> <span class="token number">2</span> <span class="token operator">*</span> <span class="token number">3</span><span class="token punctuation">;</span>    <span class="token comment">// 7</span>
<span class="token keyword">int</span> res2 <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token number">1</span> <span class="token operator">+</span> <span class="token number">2</span><span class="token punctuation">)</span> <span class="token operator">*</span> <span class="token number">3</span><span class="token punctuation">;</span>  <span class="token comment">// 9</span>
</code></pre>
<p>Java possède de nombreux opérateurs (pas seulement arithmétiques) que nous découvrirons au fur et à mesure. Sachez que des règles de précédences existent pour tous ces opérateurs (voir <a href="https://docs.oracle.com/javase/tutorial/java/nutsandbolts/operators.html">la doc d’Oracle</a> pour un rapide coup d’œil sur les opérateurs et leurs priorités).</p>
<p>Les opérateurs arithmétiques se comporteront donc en grande partie comme vous vous y attendriez.  Mais il y a une subtilité pour la division sur des entiers : Java va effectuer une <em>division entière</em>.</p>
<pre class=" language-java"><code class="prism  language-java">System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span><span class="token string">"Fraction de l'heure passée : "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>minute <span class="token operator">/</span> <span class="token number">60</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p><code>&gt; Fraction de l'heure courante : 0</code></p>
<p>En effet, <code>59 / 60 = 0 (reste 59)</code> en division entière, et ce n’est ici visiblement pas le résultat que l’on souhaite afficher.</p>
<blockquote>
<p>L’opérateur <code>%</code> (appelé “modulo”) est le cinquième opérateur arithmétique : il calcule le reste de la division entière. Ainsi <code>59 % 60 = 59</code> et <code>14 % 3 = 2</code>. Gardez-le en tête, cet opérateur est parfois bien utile en programmation.</p>
</blockquote>
<p>On peut ici s’en sortir en calculant un pourcentage à la place :</p>
<pre class=" language-java"><code class="prism  language-java">System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span><span class="token string">"Pourcentage de l'heure passée : "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span>minute <span class="token operator">*</span> <span class="token number">100</span> <span class="token operator">/</span> <span class="token number">60</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">" %"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p><code>&gt; Pourcentage de l'heure passée : 98 %</code></p>
<p>C’est toujours arrondi, mais c’est mieux que <code>0</code>. Parfois, lorsqu’il n’arrive pas à résoudre complètement un problème et pour ne pas perdre trop de temps, le développeur pourra proposer un compromis qui satisfera tout le monde. Bien sûr, ici, la solution n’est pas bien loin : il suffit d’utiliser des nombres à virgule flottante.</p>
<h2 id="nombres-flottants-floating-point-numbers">Nombres flottants (<em>floating-point numbers</em>)</h2>
<p>Un <strong>nombre flottant (floating-point number)</strong> représente un “nombre à virgule flottante”, aussi bien des entiers que des fractions. En Java, le type nombre flottant par défaut est appelé <strong>double</strong> (pour <em>double précision</em>).</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">double</span> minute <span class="token operator">=</span> <span class="token number">59.0</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span><span class="token string">"Fraction de l'heure passée : "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>minute <span class="token operator">/</span> <span class="token number">60.0</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p><code>&gt; Fraction de l'heure passée : 0.9833333333333333</code></p>
<p>Cette fois, la division est appliquée sur des <code>double</code>, et non des <code>int</code>, et donc Java effectue une division en nombres flottants.</p>
<p>Les nombres flottants peuvent être une grande source de confusion. En Java, la conversion automatique du type <code>double</code> au type <code>int</code> n’est pas autorisée (perte potentielle d’informations) mais l’inverse est légal :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">1.1</span><span class="token punctuation">;</span>  <span class="token comment">// Erreur de compilation: double-&gt;int interdit</span>
<span class="token keyword">double</span> d <span class="token operator">=</span> <span class="token number">1</span><span class="token punctuation">;</span>   <span class="token comment">// OK, conversion implicite int-&gt;double</span>
<span class="token keyword">double</span> unTiers <span class="token operator">=</span> <span class="token number">1</span> <span class="token operator">/</span> <span class="token number">3</span><span class="token punctuation">;</span>  <span class="token comment">// Méfiez-vous du loup</span>
</code></pre>
<p>Dans la dernière instruction, souvenons-nous que la JVM va d’abord évaluer l’expression <code>1 / 3</code> (elle doit faire le calcul avant d’effectuer l’affectation). Ce sont deux entiers, elle va donc effectuer une division entière et obtenir un <code>int</code> : <code>0</code>. Ensuite elle va utiliser ce résultat dans l’expression d’affectation. Elle doit affecter un <code>int</code> à un <code>double</code>, ce qui est légal. Elle effectue la conversion implicite : <code>0-&gt;0.0</code> et affecte ce résultat à la variable <code>unTiers</code>, alors que le programmeur inattentif s’attendra à ce qu’elle stocke <code>0.333...</code> C’est un problème sournois car c’est une instruction parfaitement légale et le compilateur ne bronchera pas.</p>
<p>Comment résoudre ce problème ? Il suffit de faire en sorte que l’expression soit calculée en nombres flottants, en forçant la division en flottants :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">double</span> ok <span class="token operator">=</span> <span class="token number">1.0</span> <span class="token operator">/</span> <span class="token number">3.0</span><span class="token punctuation">;</span>  <span class="token comment">// 0.3333333333333333</span>
</code></pre>
<p>Évitez de vous fier aux conversions automatiques de Java : <strong>utilisez toujours les mêmes types à droite et à gauche d’une affectation</strong>. Cela vous épargnera ce type de souci.</p>
<h2 id="erreurs-darrondi">Erreurs d’arrondi</h2>
<p>Un autre gros problème existe avec les calculs flottants : ils sont seulement <em>approximativement</em> corrects. Certains nombre (par exemple des entiers pas trop grands) peuvent être représentés exactement. Mais ce n’est pas le cas pour des fractions comme <code>1 / 3</code> ou des nombres irrationnels comme Pi : il n’est pas possible de représenter complètement ces nombres en notation décimale, encore moins sur un ordinateur (qui a une mémoire finie), et encore moins dans une variable (stockée sur un petit espace mémoire).</p>
<p>Mais le problème des arrondis de flottants sur ordinateur est plus vil. Quelques exemples en Java :</p>
<pre class=" language-java"><code class="prism  language-java">System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token number">0.1</span> <span class="token operator">*</span> <span class="token number">10</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token number">0.1</span> <span class="token operator">+</span> <span class="token number">0.1</span> <span class="token operator">+</span> <span class="token number">0.1</span> <span class="token operator">+</span> <span class="token number">0.1</span> <span class="token operator">+</span> <span class="token number">0.1</span>
                 <span class="token operator">+</span> <span class="token number">0.1</span> <span class="token operator">+</span> <span class="token number">0.1</span> <span class="token operator">+</span> <span class="token number">0.1</span> <span class="token operator">+</span> <span class="token number">0.1</span> <span class="token operator">+</span> <span class="token number">0.1</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token number">2.0</span> <span class="token operator">-</span> <span class="token number">1.1</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p><code>&gt; 1.0</code><br>
<code>&gt; 0.9999999999999999</code><br>
<code>&gt; 0.8999999999999999</code></p>
<p>Les flottants sont stockés en notation binaire sur ordinateur (comme, au final, toute valeur). <code>0.1</code> est un nombre fini en notation décimale, mais pas en binaire (<code>0.00011001100110011...</code>). Donc l’ordinateur est incapable de le stocker de manière exacte. Il arrondit. Les erreurs d’arrondis peuvent ainsi donner très rapidement des résultats de calculs formellement inexacts, comme on le voit sur les deux derniers exemples.</p>
<p>Ce n’est un problème que si vous recherchez absolument à travailler avec des valeurs absolument exactes. En dehors de ça, les types flottants ont un gros avantage : ils sont extrêmement rapides à manipuler pour le processeur. Dans de très nombreuses applications (physique, graphisme, 3D, cryptage, jeux, analyse statistique, multimédia…), les approximations sont tout à fait acceptables et le problème est de toute façon largement compensé par la rapidité de traitement.</p>
<p>Mais si vous travaillez sur une application qui gère des sommes d’argent, par exemple, les erreurs d’arrondi deviennent inacceptables. La solution courante est d’utiliser des entiers : 123,45 € sera représenté en centimes par le nombre <code>12345</code>, puis divisé par <code>100</code> lorsque l’on souhaite afficher la valeur effective en euros. Additions et soustractions sur un entier ne provoqueront aucune approximation. Attention : cette solution fonctionne tant que le nombre n’atteint pas la limite du plus grand entier représentable par un type Java.</p>
<blockquote>
<p>Une autre solution est d’utiliser une classe spécialisée dans les grands nombres : les classes <code>java.math.BigInteger</code> et <code>java.math.BigDecimal</code> sont capables de traiter exactement des séquences de chiffres aussi longues que souhaitées (dans la limite de mémoire disponible, bien sûr). L’inconvénient est que les opérations sur ces nombres sont beaucoup plus lentes qu’avec des types primitifs.</p>
</blockquote>
<p>Nous allons maintenant examiner de plus près tous les types de nombres disponibles, ainsi que les autres types dits <em>primitifs</em>.</p>
<h2 id="les-types-primitifs-de-java">Les types primitifs de Java</h2>
<p>Un <strong>type primitif</strong> est un type de base défini dans le langage lui-même. Ce sont les “briques de données basiques” à partir desquelles tous les autres types (les classes) sont construits. Java possède <strong>huit types primitifs</strong> : 4 types entiers (<code>byte, short, int, long</code>), 2 types flottants (<code>float, double</code>), le type <code>char</code> et le type <code>bool</code>.</p>
<p>Le nom des types primitifs s’écrit en minuscules (Java est sensible à la casse, <code>double</code> et <code>Double</code> ne désignent pas la même chose). C’est une façon de les reconnaître facilement, car tous les autres types sont des classes et la convention pour un nom de classe est de commencer par une majuscule.</p>
<h3 id="les-4-types-entiers">Les 4 types entiers</h3>

<table>
<thead>
<tr>
<th>nom</th>
<th>taille</th>
<th align="right">domaine de valeurs</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>byte</code></td>
<td>1 octet</td>
<td align="right"><code>-128 -&gt; +127</code></td>
</tr>
<tr>
<td><code>short</code></td>
<td>2 octets</td>
<td align="right"><code>-32 768 -&gt; +32 767</code></td>
</tr>
<tr>
<td><code>int</code></td>
<td>4 octets</td>
<td align="right"><code>-2 147 483 648 -&gt; +2 147 483 647</code></td>
</tr>
<tr>
<td><code>long</code></td>
<td>8 octets</td>
<td align="right"><code>-9e18 -&gt; +9e18</code></td>
</tr>
</tbody>
</table><p>On devrait toujours utiliser le type le plus “petit” possible par rapport aux valeurs que pourra prendre la variable. Mais en pratique, on utilise par commodité le type <code>int</code> systématiquement quand on a besoin d’un entier, même quand on sait que les valeurs de notre variable pourraient aisément tenir dans un <code>short</code> ou même un <code>byte</code>. Néanmoins, quand vous avez énormément de variables entières à traiter en même temps, il peut être intéressant de typer plus “petit” pour utiliser moins de mémoire. Par exemple, cent millions de <code>int</code> prendront 400 Mo de mémoire là où des <code>short</code> n’en utiliseraient que 200 Mo.</p>
<p>Le type <code>long</code> sera à utiliser lorsque le domaine de <code>int</code> ne suffit pas. Les littéraux de type <code>long</code> s’écrivent avec un ‘<code>l</code>’ ou un ‘<code>L</code>’ accolé, pour les distinguer d’une valeur de type <code>int</code> (les littéraux sans marquage sont considérés comme <code>int</code> par Java).</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">byte</span> b <span class="token operator">=</span> <span class="token number">100</span><span class="token punctuation">;</span>
<span class="token keyword">short</span> s <span class="token operator">=</span> <span class="token operator">-</span><span class="token number">32000</span><span class="token punctuation">;</span>
<span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">10</span><span class="token punctuation">;</span>
<span class="token keyword">long</span> lg <span class="token operator">=</span> 123L<span class="token punctuation">;</span>
</code></pre>
<h3 id="les-2-types-flottants">Les 2 types flottants</h3>

<table>
<thead>
<tr>
<th>nom</th>
<th align="center">taille</th>
<th align="right">domaine de valeurs</th>
<th align="center">précision approximative</th>
<th align="right">exemple</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>float</code></td>
<td align="center">4 octets</td>
<td align="right"><code>-/+ 3.4e38</code></td>
<td align="center">~6-7 chiffres significatifs</td>
<td align="right"><code>3.14f 3.14F</code></td>
</tr>
<tr>
<td><code>double</code></td>
<td align="center">8 octets</td>
<td align="right"><code>-/+ 1.79e308</code></td>
<td align="center">~15 chiffres significatifs</td>
<td align="right"><code>3.14 3.14d 3.14D</code></td>
</tr>
</tbody>
</table><h3 id="le-type-char">Le type <code>char</code></h3>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">char</span> c <span class="token operator">=</span> <span class="token string">'A'</span><span class="token punctuation">;</span>
</code></pre>
<p>Le type <code>char</code> de Java (2 octets) <em>est censé</em> représenter un caractère unique. Il est basé sur Unicode 1.0, dont les 16 bits d’encodage se sont par la suite révélés insuffisants pour coder tous les caractères souhaitables (différents alphabets, émoji…). Ainsi un “caractère” (<em>code point</em>) est aujourd’hui représenté par 1 ou 2 <code>char</code> (<em>code unit</em>). Cela pose problème parce que si vous essayez par exemple de lire un flux de caractères en analysant un par un les <code>char</code>, vous risquez d’interpréter un caractère encodé sur 2 <code>char</code> comme étant deux caractères encodés chacun sur 1 <code>char</code>.</p>
<p>Conclusion : <strong>utiliser le type <code>char</code> pour stocker un caractère est source d’erreurs potentielles</strong> parfois difficiles à localiser. N’utilisez ce type que si vous avez effectivement à travailler avec des <em>code units</em> UTF-16 (par exemple, si vous implémentez un éditeur de texte). Autrement, <strong>préférez-lui le type <code>String</code></strong>, qui ne vous posera pas de problème.</p>
<h3 id="le-type-bool">Le type <code>bool</code></h3>
<p>Le type <code>bool</code> représente une valeur logique (vrai/faux, <code>true/false</code>).</p>
<pre class=" language-java"><code class="prism  language-java">bool reallyWeird <span class="token operator">=</span> <span class="token number">2</span> <span class="token operator">&gt;</span> <span class="token number">3</span><span class="token punctuation">;</span>   <span class="token comment">// false</span>
<span class="token keyword">if</span> <span class="token punctuation">(</span>reallyWeird<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"La fin du monde est proche."</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>Nous examinerons cela avec plus de précision dans le chapitre sur la logique.</p>
<h2 id="ça-fonctionne-pas">“Ça fonctionne pas”</h2>
<p>Trois types d’erreurs peuvent se produire dans un programme : erreurs de compilation (<em>compile-time errors</em>), erreurs d’exécution (<em>run-time errors</em>) et erreurs de logique. Il est important de les distinguer.</p>
<h3 id="erreurs-de-compilation-compile-time-errors">Erreurs de compilation (<em>compile-time errors</em>)</h3>
<p><strong>Les erreurs de compilation</strong> se produisent lorsque vous violez les règles du langage. Par exemple, une parenthèse ouverte qui ne trouve pas sa copine fermée au bon endroit.</p>
<pre class=" language-java"><code class="prism  language-java">System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"Youhou"</span><span class="token punctuation">;</span>  <span class="token comment">// Erreur de compilation</span>
</code></pre>
<p>Si le compilateur rencontre ne serait-ce qu’une seule erreur, le programme ne peut être compilé, et un message d’erreur est affiché pour chaque problème rencontré.</p>
<p>Les messages d’erreur du compilateur sont souvent assez explicites : ils vous indiquent où se trouve l’erreur et de quoi il s’agit. Parfois, le message peut sembler plus cryptique. Un copié/collé du message dans Google vous donnera alors sans doute plus de précisions. Ce sont en général les erreurs les plus faciles à corriger.</p>
<p>Le compilateur vous sortira également des <strong>avertissements (warnings)</strong>. Ce sont des indications pointant des problèmes potentiels dans votre code, qui pourront entraîner un comportement inattendu lors de l’exécution. Ces problèmes potentiels n’empêchent pas la compilation, et il est aisé de les ignorer. Cependant, <strong>vous devriez prendre au sérieux tous les avertissements</strong> donnés par le compilateur. Certaines équipes de développement vont même jusqu’à configurer le compilateur pour traiter les avertissements comme des erreurs de compilation et ainsi obliger les développeurs à résoudre les problèmes associés.</p>
<h3 id="erreurs-dexécution-run-time-errors">Erreurs d’exécution (<em>run-time errors</em>)</h3>
<p>Le programme compile, ça ne veut pas dire qu’il fonctionne. Les <strong>erreurs d’exécution</strong> (“plantages” en langage technique) se produisent une fois le programme lancé. En Java, ça veut dire que c’est au moment où l’interpréteur (la JVM) exécute le <em>byte code</em> que quelque chose cloche. On appelle ces erreur des <strong>exceptions</strong>. Par exemple, une exception de type <code>ArithmeticException</code> se produit lorsque le programme arrive à un point où il est censé effectuer une division par zéro, une opération qu’il ne peut pas effectuer.</p>
<p>Quand ça arrive, l’interpréteur nous indique ce qui s’est passé (le type d’exception) et l’endroit où cela s’est produit dans le “déroulement” du programme, avec un fichier et une ligne précise dans ce fichier (gardez en tête que ce n’est pas forcément exactement à cet endroit que l’origine de l’erreur se trouve dans le code).</p>
<h3 id="erreurs-logiques">Erreurs logiques</h3>
<p>Le programme compile, il ne “plante” pas, mais il ne fait pas ce que vous voudriez qu’il fasse. Pourtant, il fait exactement ce que vous lui avez demandé de faire. Vous avez une ou plusieurs <strong>erreurs logiques</strong> dans votre programme. Par exemple,</p>
<p>Repérer une erreur logique, lorsqu’on ne sait pas la localiser simplement en regardant le code, se fait la plupart du temps en effectuant une phase de <em>debugging</em> : constatant le résultat inattendu, on utilise l’IDE pour suivre le flux d’exécution pas à pas, en vérifiant au passage le contenu des variables significatives, pour comprendre la différence entre ce qui se produit et ce qui devrait se produire. On effectue également souvent un débogage pour comprendre une erreur d’exécution.</p>

