---


---

<h1 id="chapitre-3">Chapitre 3</h1>
<h1 id="entrées-et-sorties">Entrées et sorties</h1>
<p>Le fil rouge de ce chapitre sera la lecture d’entrées à partir du clavier et le formatage plus élaboré des sorties, mais nous continuerons d’explorer en même temps d’autres sujets.</p>
<h2 id="la-classe-system">La classe <code>System</code></h2>
<p>Nous avons utilisé <code>System.out.println</code> depuis le début sans vraiment savoir ce que c’était. <code>System</code> est une <strong>classe</strong> qui propose des méthodes (fonctions) relatives au « système », c’est-à-dire l’environnement sur lequel le programme tourne. Elle fournit également un <em>objet</em> nommé <code>out</code> qui dispose quant à lui de méthodes pour afficher une sortie (comme <code>println</code>). Voyons ce qui se passe quand on demande à <code>println</code> d’afficher la valeur de <code>System.out</code> :</p>
<pre class=" language-java"><code class="prism  language-java">System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>System<span class="token punctuation">.</span>out<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span> java<span class="token punctuation">.</span>io<span class="token punctuation">.</span>PrintStream<span class="token annotation punctuation">@1bce4f0a</span>
</code></pre>
<p>Cette sortie indique que <code>System.out</code> est un objet de la classe <code>PrintStream</code>, qui est définie dans un package appelé <code>java.io</code>. Un <strong>package</strong> est une collection de classes qui se rapportent au même thème : <code>java.io</code> contient les classes pour les <em>I/O</em> (<em>In/Out</em>, Entrées/Sorties). Les nombres/chiffres après le signe <code>@</code> désignent <strong>l’adresse</strong> de <code>System.out</code>, représentée par un nombre hexadécimal (base 16). L’adresse d’une valeur est sa location en mémoire.</p>
<p>Les classes <code>System</code> et <code>PrintStream</code> font partie de la ***Java Class Library (JCL)***, une large collection de classes que vous pouvez utiliser dans vos programmes. La JCL contient des classes spécialisées dans des domaines aussi variés que les mathématiques, les protocoles réseaux, les bases de données, les sons et images, le graphisme, les structures de données ou encore la compression de données.</p>
<h2 id="la-classe-scanner">La classe <code>Scanner</code></h2>
<p>La classe <code>System</code> fournit également de quoi lire une entrée par le clavier : <code>System.in</code>. C’est un objet de la classe <code>InputStream</code> qui a des méthodes qui ne sont pas très aisées à utiliser, mais Java fournit d’autres classes pour rendre les choses plus faciles.</p>
<p>Par exemple, <code>Scanner</code> est une classe qui fournit des méthodes pour lire des mots, nombres et autres au clavier. <code>Scanner</code> appartient au package <code>java.util</code>. Pour pouvoir l’utiliser, vous devez d’abord <strong>importer</strong> ce package dans votre fichier.</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">import</span> java<span class="token punctuation">.</span>util<span class="token punctuation">.</span>Scanner<span class="token punctuation">;</span>
</code></pre>
<p>Cette instruction <code>import</code> prévient le compilateur que lorsqu’on se réfère à <code>Scanner</code>, on parle de celui qui est défini dans <code>java.util</code>. C’est la principale raison d’être des packages : une classe <code>Scanner</code> pourrait très bien être définie dans un autre package, et même pourquoi pas par votre propre code. Les packages permettent de supprimer toute ambiguïté quant au noms de classes.</p>
<blockquote>
<p>Les instructions <code>import</code> doivent se situer au début du fichier, avant la déclaration de toute classe.</p>
</blockquote>
<p>Voici comment déclarer et initialiser une variable <code>in</code> de type <code>Scanner</code> qui lit ses entrées depuis <code>System.in</code> (le clavier) :</p>
<pre class=" language-java"><code class="prism  language-java">Scanner in <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Scanner</span><span class="token punctuation">(</span>System<span class="token punctuation">.</span>in<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p>On peut ensuite utiliser par exemple la méthode <code>nextLine</code> qui lit une ligne tapée au clavier et retourne la <code>String</code> correspondante. Voici un programme complet :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">import</span> java<span class="token punctuation">.</span>util<span class="token punctuation">.</span>Scanner<span class="token punctuation">;</span>

<span class="token keyword">public</span> <span class="token keyword">class</span> <span class="token class-name">Echo</span> <span class="token punctuation">{</span>
  <span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">void</span> <span class="token function">main</span><span class="token punctuation">(</span>String<span class="token punctuation">[</span><span class="token punctuation">]</span> args<span class="token punctuation">)</span> <span class="token punctuation">{</span>
    String line<span class="token punctuation">;</span>
    Scanner in <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Scanner</span><span class="token punctuation">(</span>System<span class="token punctuation">.</span>in<span class="token punctuation">)</span><span class="token punctuation">;</span>

    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span><span class="token string">"Écrivez quelque chose : "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    line <span class="token operator">=</span> in<span class="token punctuation">.</span><span class="token function">nextLine</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"Vous avez écrit :"</span> <span class="token operator">+</span> line<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<blockquote>
<p>Les instructions <code>import</code> ne sont pas absolument nécessaire. On pourrait se référer à la classe Scanner dans le code en indiquant à Java explicitement dans quel package elle se trouve : <code>java.util.Scanner in = new java.util.Scanner(System.in);</code> Mais c’est moins lisible et plus fastidieux, et les importations sont tellement pratiques qu’il est assez rare de rencontrer du code où l’on indique le chemin complet d’une classe qui se trouve dans un autre package.</p>
</blockquote>
<blockquote>
<p>Pourquoi peut-on utiliser la classe <code>System</code> alors qu’elle se trouve dans un autre package ? C’est parce que le package <code>java.lang</code> en question est importé automatiquement par la JVM. Les classes de ce package sont considérées comme quasi-indispensables à l’écriture de tout programme Java (<code>String</code> s’y trouve également).</p>
</blockquote>
<h2 id="un-point-sur-la-terminologie">Un point sur la terminologie</h2>
<p>A ce stade, nous connaissons presque toutes les « unités d’organisation » qui constituent un programme Java. Les voici récapitulées, du plus « englobant » au plus « englobé » :</p>
<ul>
<li>Package					(<code>java.util</code>)</li>
<li>Classe		(<em>class</em>)			(<code>Scanner</code>)</li>
<li>Méthode	(<em>method</em>)		(<code>nextLine</code>)</li>
<li>Instruction	(<em>statement</em>)		(<code>line = in.nextLine();</code>)</li>
<li>Expression					(<code>hour * 60 + minute</code>)</li>
<li>Token						(les « mots » : <code>hour</code>, <code>*</code>, <code>60</code>…)</li>
</ul>
<p>Les applications Java sont typiquement organisées en <strong>packages</strong> qui incluent un certain nombre de <strong>classes</strong>. Chaque classe définit des <strong>méthodes</strong>, et chaque méthode est une séquence d’<strong>instructions</strong>. Chaque instruction exécute une ou plusieurs opérations, en fonction du nombre d’<strong>expressions</strong> qu’elle contient. Chaque expression représente une valeur unique à calculer. Par exemple, l’instruction <code>hours = minutes / 60.0;</code> est une instruction d’affectation qui contient une seule expression : <code>minutes / 60.0</code>.</p>
<p>Les <strong>tokens</strong> sont les éléments les plus basiques d’un programme, lexicalement parlant. Nombre, noms de variables, opérateurs, mots clés du langage, parenthèses, accolades, point-virgules… Tous sont des tokens.</p>
<p>Connaître cette terminologie (et le vocabulaire du code source en général) peut vous aider pour plusieurs raisons :</p>
<ul>
<li>cela vous aide à différencier les entités et les structures du code ;</li>
<li>cela vous aide à comprendre plus facilement la documentation ainsi que les messages d’erreurs du compilateur (ex : “<code>unexpected token</code>”, “<code>illegal start of expression</code>”, “<code>not a statement</code>”) ;</li>
<li>cela permet de bien comprendre de quoi on parle lorsqu’on discute avec un autre développeur, lorsque pose une question sur internet ou qu’un lit une documentation, lorsqu’un formateur vous parle… Bref, cela nous donne un langage de communication sans ambiguïté.</li>
</ul>
<p>J’insiste enfin sur le fait qu’il y a une différence claire entre le <em>langage</em> Java (qui définit les « unités d’organisation » récapitulées plus haut) et la <em>bibliothèque de classes</em> de Java (JCL, qui fournit des classes que vous pouvez importer). Par exemple, <code>public</code> et <code>class</code> appartiennent au <em>langage</em>, mais pas <code>PrintStream</code> ou <code>Scanner</code> (classes de la JCL).</p>
<p>Java SE (<em>Standard Edition</em>) est livré avec plusieurs milliers de classes que vous pouvez directement importer. Vous pouvez prendre cinq minutes pour toutes les examiner ici : <a href="https://docs.oracle.com/en/java/javase/11/">https://docs.oracle.com/en/java/javase/11/</a></p>
<h2 id="littéraux-et-constantes">Littéraux et constantes</h2>
<p>Écrivons un programme de conversion de pouces en centimètres.</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span> pouces<span class="token punctuation">;</span>
<span class="token keyword">double</span> cm<span class="token punctuation">;</span>
Scanner in <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Scanner</span><span class="token punctuation">(</span>System<span class="token punctuation">.</span>in<span class="token punctuation">)</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span><span class="token string">"Entrez la mesure en pouces : "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
pouces <span class="token operator">=</span> in<span class="token punctuation">.</span><span class="token function">nextInt</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
cm <span class="token operator">=</span> pouces <span class="token operator">*</span> <span class="token number">2.54</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>pouces <span class="token operator">+</span> <span class="token string">" pouces = "</span> <span class="token operator">+</span> cm <span class="token operator">+</span> <span class="token string">" cm"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p>Ce code fonctionne, mais il contient un problème de lisibilité : un nombre magique (<em>magic number</em>). Le nombre 2.54 semble issu de nulle part et peut rendre la lecture plus compliqué à quelqu’un qui ne sait pas du tout ce que c’est.</p>
<p>Une valeur apparaissant explicitement dans le code est appelée un <strong>littéral</strong>. Par exemple, <code>"Jean", 123L, 3.4</code> sont des littéraux. En général, il n’y a rien de mal avec les littéraux. Mais quand un nombre comme 2.54 apparaît dans une expression et qu’il semble « magiquement » tombé de nulle part, il rend le code plus difficile à <em>comprendre</em>. Et quand cette valeur apparaît plusieurs fois dans le code et qu’<em>elle pourrait éventuellement changer dans le futur</em>, c’est encore pire : ça rend le code plus compliqué à <em>maintenir</em>.</p>
<p>Dans notre exemple, on déduit assez facilement la nature du nombre 2.54 en lisant le code mais ce n’est pas toujours aussi évident. De plus, le nombre de centimètres pour un pouce ne risque pas de changer demain, mais ce n’est pas toujours aussi évident non plus. La bonne pratique est d’affecter le nombre magique à une variable avec un nom significatif :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">double</span> nbCentimetresParPouce <span class="token operator">=</span> <span class="token number">2.54</span><span class="token punctuation">;</span>
<span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">.</span>
cm <span class="token operator">=</span> pouces <span class="token operator">*</span> nbCentimetresParPouce<span class="token punctuation">;</span>
</code></pre>
<p>Plus facile à lire, et plus facile à maintenir si jamais cette valeur venait à changer (un seul endroit dans le code où elle devra alors être modifiée). Mais cette solution est incomplète ; elle renferme un problème potentiel. Les variables, par définition, varient. Or <code>nbCentimetresParPouce</code> devrait être affecté une fois et une seule, lors de sa définition, et on ne devrait plus jamais y toucher. Pour l’instant, un développeur de l’équipe n’ayant pas bien compris sa fonction pourrait n’importe où dans le code réaffecter cette valeur supposée intouchable. Java offre une construction qui permet de s’assurer que cela est impossible : le mot clé <code>final</code> appliqué à une variable signifie que celle-ci ne pourra pas être réaffectée après son initialisation. On appelle cela une <strong>constante</strong> :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">final</span> <span class="token keyword">double</span> NB_CENTIMETRES_PAR_POUCE <span class="token operator">=</span> <span class="token number">2.54</span><span class="token punctuation">;</span>
<span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">.</span>
NB_CENTIMETRES_PAR_POUCE <span class="token operator">=</span> <span class="token number">3.0</span><span class="token punctuation">;</span>    <span class="token comment">// Erreur de compilation : on ne touche pas aux constantes</span>
cm <span class="token operator">=</span> pouces <span class="token operator">*</span> NB_CENTIMETRES_PAR_POUCE<span class="token punctuation">;</span>
</code></pre>
<p>Par convention, les noms de constantes sont en majuscules, un <em>underscore</em> (<code>_</code>) séparant les mots. Comme d’habitude, respectez la convention dans votre code.</p>
<h2 id="formatage-des-sorties">Formatage des sorties</h2>
<p><code>System.out</code> dispose d’une méthode bien pratique pour contrôler le format des sorties : <code>printf</code> (<em>print formatted</em>).</p>
<p>Prenons l’expression <code>1.0 / 3.0</code>.  Le résultat est un <code>double</code>, et son affichage par un simple <code>print</code> donnera : <code>0.3333333333333333</code>. Si on veut une valeur arrondie, le plus simple est de laisser faire <code>printf</code> :</p>
<pre class=" language-java"><code class="prism  language-java">System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">printf</span><span class="token punctuation">(</span><span class="token string">"Un tiers = %.2f"</span><span class="token punctuation">,</span> <span class="token number">1.0</span> <span class="token operator">/</span> <span class="token number">3.0</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span> Un tiers <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">,</span><span class="token number">33</span>
</code></pre>
<p>La première partie entre parenthèses (avant la virgule) s’appelle une <em>format string</em> et spécifie comment la sortie sera affichée. Elle contient du texte « normal » et une chaîne spéciale appelée spécificateur de format (<em>format specifier</em>), qui commence par <code>%</code>. Le spécificateur <code>%.2f</code> indique que la valeur doit être affichée en flottant (<code>f</code>), et arrondie à 2 chiffres décimaux (<code>.2</code>). La valeur en question sera la valeur de l’expression indiquée en deuxième paramètre, après la virgule (<code>1.0 / 3.0</code>).</p>
<p>La <em>format string</em> n’est pas limitée à un seul <em>format specifier</em>. Chaque fois qu’elle aura besoin d’une valeur, elle ira chercher la suivante dans la liste spécifée après elle. Ici, on utilise deux valeurs (<code>%d</code> représente un entier) :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span> pouces <span class="token operator">=</span> <span class="token number">2</span><span class="token punctuation">;</span>
<span class="token keyword">double</span> cm <span class="token operator">=</span> pouces <span class="token operator">*</span> NB_CENTIMETRES_PAR_POUCE<span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">printf</span><span class="token punctuation">(</span><span class="token string">"%d pouces = %f cm\n"</span><span class="token punctuation">,</span> pouces<span class="token punctuation">,</span> cm<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span> <span class="token number">2</span> pouces <span class="token operator">=</span> <span class="token number">5.080000</span> cm
</code></pre>
<p>Comme <code>print</code>, <code>printf</code> n’ajoute pas de passage à la ligne. Notre instruction passe néanmoins à la ligne grâce à l’ajout de <code>\n</code> à la fin de la <em>format string</em>. C’est ce qu’on appelle une <strong>séquence d’échappement</strong>. Ce sont deux caractères (le premier étant un <em>antislash</em>, c’est à ça qu’on reconnaît une séquence d’échappement) qui vont insérer à l’endroit indiqué le caractère spécial qui correspond à cette séquence d’échappement (on dit que l’<em>antislash</em> « s’échappe » de la chaîne normale pour afficher un caractère spécial). Voici les quatre séquences d’échappement les plus usitées en Java. Notez que ça fonctionnera aussi avec  <code>print</code>/<code>println</code> et pas uniquement avec <code>printf</code> :</p>

<table>
<thead>
<tr>
<th></th>
<th align="center"></th>
</tr>
</thead>
<tbody>
<tr>
<td><code>\n</code></td>
<td align="center">nouvelle ligne</td>
</tr>
<tr>
<td><code>\t</code></td>
<td align="center">tabulation</td>
</tr>
<tr>
<td><code>\"</code></td>
<td align="center">guillemet</td>
</tr>
<tr>
<td><code>\\</code></td>
<td align="center">antislash</td>
</tr>
</tbody>
</table><pre class=" language-java"><code class="prism  language-java">System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"\\n\t\"nouvelle ligne\"\n\\t\t\\tabulation\\"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span> \n		<span class="token string">"nouvelle ligne"</span>
<span class="token operator">&gt;</span> \t		\tabulation\
</code></pre>
<p>Les <em>format strings</em> forment un « petit langage » à elles toutes seules, il y a pas mal d’options différentes. Voici quelques exemples, pour vous donner une idée :</p>

<table>
<thead>
<tr>
<th align="center"></th>
<th></th>
<th align="right"></th>
</tr>
</thead>
<tbody>
<tr>
<td align="center"><code>%d</code></td>
<td>nombre entier</td>
<td align="right"><code>12345</code></td>
</tr>
<tr>
<td align="center"><code>%08d</code></td>
<td>idem avec au moins 8 chiffres, remplir avec zéros si nécessaire</td>
<td align="right"><code>00012345</code></td>
</tr>
<tr>
<td align="center"><code>%f</code></td>
<td>nombre flottant</td>
<td align="right"><code>6.789000</code></td>
</tr>
<tr>
<td align="center"><code>%.2f</code></td>
<td>idem arrondi à 2 décimales</td>
<td align="right"><code>6.79</code></td>
</tr>
<tr>
<td align="center"><code>%s</code></td>
<td>chaîne de caractères</td>
<td align="right"><code>"Jean"</code></td>
</tr>
</tbody>
</table><blockquote>
<p>Erreur courante : utiliser des <code>+</code> au lieu de virgules dans <code>printf</code> pour séparer les valeurs qui seront affichées (comme on le fait couramment avec <code>print/println</code>). Cela provoquera une erreur d’exécution.</p>
</blockquote>
<h2 id="opérateurs-cast">Opérateurs <code>cast</code></h2>
<p>Supposons que nous avons une mesure en centimètres et que l’on veut cette valeur en pouces, mais arrondie.</p>
<pre class=" language-java"><code class="prism  language-java">pouces <span class="token operator">=</span> cm <span class="token operator">/</span> NB_CENTIMETRES_PAR_POUCE<span class="token punctuation">;</span>
</code></pre>
<p>Cela vous donnera une erreur de compilation : <code>impossible de convertir du type double vers les type int</code>. Java convertira sans rien dire de <code>int</code> vers <code>double</code> car il n’y a pas de perte d’informations. Mais si vous voulez faire la conversion inverse,  vous devez lui dire explicitement que vous savez ce que vous faites (que vous être au courant qu’il y aura potentiellement une perte d’informations), en utilisant une <strong>conversion de type explicite</strong> (<em><strong>type cast</strong></em>). La syntaxe est la suivante :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">double</span> pi <span class="token operator">=</span> <span class="token number">3.14159</span><span class="token punctuation">;</span>
<span class="token keyword">int</span> roundedPi <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token keyword">int</span><span class="token punctuation">)</span> pi<span class="token punctuation">;</span>
</code></pre>
<p>On entoure le type de destination de parenthèses et la valeur qui suit sera automatiquement convertie vers ce type. Ici <code>roundedPI</code> aura pour valeur <code>3</code>. Notez que l’arrondi se fait toujours vers zéro (<code>2.9999999</code> sera arrondi à <code>2</code> et non <code>3</code>). Le <em>cast</em> se débarrasse juste de la décimale (nous verrons par la suite comment arrondir au plus près).</p>
<p>Pour utiliser un <em>cast</em>, les types doivent être compatibles. On ne peut pas par exemple caster une <code>String</code> vers un <code>int</code>.</p>
<p>Un <em>cast</em> est en fait un opérateur comme un autre, et il a donc une précédence par rapport aux autres opérateurs. Notamment, le <em>cast</em> est prioritaire par rapport aux opérateurs arithmétiques :</p>
<pre class=" language-java"><code class="prism  language-java">pouces <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token keyword">int</span><span class="token punctuation">)</span> cm <span class="token operator">/</span> NB_CENTIMETRES_PAR_POUCE<span class="token punctuation">;</span>
</code></pre>
<p>ne fonctionne pas non plus car le <em>cast</em>  va être appliqué à la variable <code>cm</code> et non à l’expression complète. Or <code>int * double</code> donne un <code>double</code>, et l’affectation <code>double-&gt;int</code> est de nouveau illégale. Il faut casser la précédence :</p>
<pre class=" language-java"><code class="prism  language-java">pouces <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token keyword">int</span><span class="token punctuation">)</span> <span class="token punctuation">(</span>cm <span class="token operator">/</span> NB_CENTIMETRES_PAR_POUCE<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p>Ainsi Java calcule d’abord l’expression puis caste la valeur résultante (un <code>double</code>) vers <code>int</code>.</p>
<h2 id="un-point-sur-les-scores">Un point sur les scores</h2>
<p>Voici un petit programme de conversion qui récapitule pas mal des concepts que nous avons vus jusqu’ici :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">import</span> java<span class="token punctuation">.</span>util<span class="token punctuation">.</span>Scanner<span class="token punctuation">;</span>

<span class="token comment">/**
* Convertit des centimètres en pieds et pouces.
*/</span>
<span class="token keyword">public</span> <span class="token keyword">class</span> <span class="token class-name">Convert</span> <span class="token punctuation">{</span>
  <span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">void</span> <span class="token function">main</span><span class="token punctuation">(</span>String<span class="token punctuation">[</span><span class="token punctuation">]</span> args<span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">double</span> cm<span class="token punctuation">;</span>
    <span class="token keyword">int</span> pieds<span class="token punctuation">,</span> pouces<span class="token punctuation">,</span> reste<span class="token punctuation">;</span>
    <span class="token keyword">final</span> <span class="token keyword">double</span> NB_CM_PAR_POUCE <span class="token operator">=</span> <span class="token number">2.54</span><span class="token punctuation">;</span>
    <span class="token keyword">final</span> <span class="token keyword">int</span> NB_POUCES_PAR_PIED <span class="token operator">=</span> <span class="token number">12</span><span class="token punctuation">;</span>
    
    <span class="token comment">// Demande à l'utilisateur la valeur en cm</span>
    Scanner in <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Scanner</span><span class="token punctuation">(</span>System<span class="token punctuation">.</span>in<span class="token punctuation">)</span><span class="token punctuation">;</span>
    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span><span class="token string">"Combien de centimètres exactement ? "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    cm <span class="token operator">=</span> in<span class="token punctuation">.</span><span class="token function">nextDouble</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    
    <span class="token comment">// Conversion et affichage du résultat</span>
    <span class="token comment">// Notez l'utilisation de l'opérateur % (reste)</span>
    pouces <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token keyword">int</span><span class="token punctuation">)</span> <span class="token punctuation">(</span>cm <span class="token operator">/</span> NB_CM_PAR_POUCE<span class="token punctuation">)</span><span class="token punctuation">;</span>
    pieds <span class="token operator">=</span> pouces <span class="token operator">/</span> NB_POUCES_PAR_PIED<span class="token punctuation">;</span>
    reste <span class="token operator">=</span> pouces <span class="token operator">%</span> NB_POUCES_PAR_PIED<span class="token punctuation">;</span>
    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">printf</span><span class="token punctuation">(</span><span class="token string">"%.2f cm = %d pieds, %d pouces\n"</span><span class="token punctuation">,</span>
                         cm<span class="token punctuation">,</span> pieds<span class="token punctuation">,</span> reste<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<p>Quelques remarques de lisibilité :</p>
<ul>
<li>Ici on adopte un style qui déclare toutes les variables en début de fonction et qui permet de voir d’emblée toutes les variables qui seront utilisées. On peut aussi choisir de déclarer les variables au fur et à mesure de leur utilisation dans l’algorithme.</li>
<li>Les étapes majeures de l’algorithme sont séparées par une ligne blanche.</li>
<li>La classe est documentée grâce à un commentaire javadoc (<code>/** ... */</code>). javadoc permet la génération automatique de documentation de code source à partir de ces commentaires. Nous n’aurons sûrement pas le temps de l’aborder en détails, donc cf internet pour en savoir plus.</li>
<li>Quand les instructions deviennent trop longues pour tenir confortablement sur une ligne, il est d’usage de couper la ligne pour éviter un scroll horizontal (80/100 caractères max. sur une ligne, c’est bien).</li>
</ul>
<h2 id="le-«-bug-»-de-scanner">Le « bug » de <code>Scanner</code></h2>
<pre class=" language-java"><code class="prism  language-java">System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span><span class="token string">"Quel est votre nom ? "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
String nom <span class="token operator">=</span> in<span class="token punctuation">.</span><span class="token function">nextLine</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span><span class="token string">"Quel est votre âge ? "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">int</span> age <span class="token operator">=</span> in<span class="token punctuation">.</span><span class="token function">nextInt</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">printf</span><span class="token punctuation">(</span><span class="token string">"Bonjour %s, âgé(e) de %d ans.\n"</span><span class="token punctuation">,</span> nom<span class="token punctuation">,</span> age<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span> Quel est votre nom <span class="token operator">?</span> Francis
<span class="token operator">&gt;</span> Quel est votre âge <span class="token operator">?</span> <span class="token number">58</span>
<span class="token operator">&gt;</span> Bonjour Francis<span class="token punctuation">,</span> âgé<span class="token punctuation">(</span>e<span class="token punctuation">)</span> de <span class="token number">58</span> ans<span class="token punctuation">.</span>
</code></pre>
<p>Ce programme fonctionne comme vous vous y attendez. Le suivant, non :</p>
<pre class=" language-java"><code class="prism  language-java">System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span><span class="token string">"Quel est votre âge ? "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">int</span> age <span class="token operator">=</span> in<span class="token punctuation">.</span><span class="token function">nextInt</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span><span class="token string">"Quel est votre nom ? "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
String nom <span class="token operator">=</span> in<span class="token punctuation">.</span><span class="token function">nextLine</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">printf</span><span class="token punctuation">(</span><span class="token string">"Bonjour %s, âgé(e) de %d ans.\n"</span><span class="token punctuation">,</span> nom<span class="token punctuation">,</span> age<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span> Quel est votre âge <span class="token operator">?</span> <span class="token number">58</span>
<span class="token operator">&gt;</span> Quel est votre nom <span class="token operator">?</span>
<span class="token operator">&gt;</span> Bonjour <span class="token punctuation">,</span> âgé<span class="token punctuation">(</span>e<span class="token punctuation">)</span> de <span class="token number">58</span> ans<span class="token punctuation">.</span>
</code></pre>
<p>Vous n’avez pas le temps d’entrer votre nom que le programme se termine. Que se passe-t-il ? <code>Scanner</code> lit un <em>flux de caractères</em>, et il ne « consomme » dans ce flux que ce dont il a besoin. Quand l’utilisateur écrit <code>58</code> et valide par <code>entrée</code>, voici ce qui se passe :</p>
<pre><code>5 8 \n		5 8 \n		5 8 \n
↑             ↑             ↑
</code></pre>
<p>Le <code>Scanner</code> doit récupérer un entier (<code>nextInt</code>). Le curseur du <code>Scanner</code>, représenté par la flèche, lit les caractères jusqu’à ce qu’il en rencontre un qui n’est plus un chiffre. Il retourne <code>58</code> et l’exécution continue. Le programme affiche « Quel est votre nom ? » et arrive à l’instruction contenant <code>in.nextLine()</code>. <code>nextLine</code> lit dans le flux une chaîne de caractère jusqu’à ce qu’il rencontre un passage à la ligne (<code>\n</code>). Or le curseur est déjà sur un caractère <code>\n</code> qui n’a pas encore été consommé. La méthode retourne immédiatement sans même donner le temps à l’utilisateur d’écrire quoi que ce soit.</p>
<p>Comment résoudre ce problème ? Il suffit de forcer le <code>Scanner</code> à « consommer » le <code>\n</code> avant la deuxième question. Cela peut se faire en appelant <code>nextLine()</code>, sans même stocker le résultat dans une variable, pour forcer le curseur à avancer après le <code>\n</code> :</p>
<pre class=" language-java"><code class="prism  language-java">System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span><span class="token string">"Quel est votre âge ? "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">int</span> age <span class="token operator">=</span> in<span class="token punctuation">.</span><span class="token function">nextInt</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
in<span class="token punctuation">.</span><span class="token function">nextLine</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span><span class="token string">"Quel est votre nom ? "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
String nom <span class="token operator">=</span> in<span class="token punctuation">.</span><span class="token function">nextLine</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">printf</span><span class="token punctuation">(</span><span class="token string">"Bonjour %s, âgé(e) de %d ans.\n"</span><span class="token punctuation">,</span> nom<span class="token punctuation">,</span> age<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span> Quel est votre âge <span class="token operator">?</span> <span class="token number">58</span>
<span class="token operator">&gt;</span> Quel est votre nom <span class="token operator">?</span> Francis
<span class="token operator">&gt;</span> Bonjour Francis<span class="token punctuation">,</span> âgé<span class="token punctuation">(</span>e<span class="token punctuation">)</span> de <span class="token number">58</span> ans<span class="token punctuation">.</span>
</code></pre>

