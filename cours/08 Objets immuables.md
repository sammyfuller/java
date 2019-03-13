---


---

<h1 id="chapitre-8">Chapitre 8</h1>
<h1 id="objets-immuables">Objets immuables</h1>
<p>Java est un langage « orienté objets » : il utilise des objets pour représenter des données et fournir des services (méthodes) en relation. C’est un puissant paradigme de conception de programmes, et nous allons maintenant graduellement introduire les concepts qui y sont liés.</p>
<p>Un <strong>objet</strong> est une collection de données qui fournit un ensemble de méthodes. Par exemple, les <em>strings</em> sont des objets. Elles contiennent des caractères et fournissent des méthodes pour les manipuler. Un objet est créé à partir d’une <strong>classe</strong>, c’est elle qui décrit <strong>l’état</strong> (les données, les valeurs internes) des objets créés et les <strong>méthodes</strong> (services) qu’il va exposer. C’est dans la définition de la classe <code>String</code> qu’on trouvera le tableau qui contient effectivement les caractères de la string (son état) et toutes les méthodes qui permettent de manipuler celles-ci.</p>
<h2 id="types-primitifs-vs.-classes">Types primitifs vs. classes</h2>
<p>Vous le savez, toutes les valeurs ne sont pas forcément des objets : Java possède aussi huit types primitifs. Quand vous déclarez une variable de type primitif, Java réserve une petite partie de mémoire pour stocker sa valeur.</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span> number <span class="token operator">=</span> <span class="token operator">-</span><span class="token number">2</span><span class="token punctuation">;</span>
</code></pre>
<p><img src="https://lh3.googleusercontent.com/Bt0R4VSRtbNs1fNay7mSseFqbVKTvQd2s9Ltm6dIsWiik4PF9XpGkkPWrktWGj5ydCbBf_wk34dm" alt="enter image description here"><br>
Ce type de diagramme s’appelle un <em>diagramme de mémoire</em>. Il indique le nom des variables et la façon dont les données sont stockées. Ici la variable <code>nombre</code> est « intrinsèquement accolée » à sa valeur <code>-2</code>.</p>
<p>Quand vous déclarez et instanciez un objet, en revanche, la variable stocke uniquement la <em>référence</em> de cet objet. Nous avons déjà vu cela avec les tableaux (qui, rappelons-le, sont des objets). L’objet lui-même et ses données sont stockés à l’emplacement mémoire pointé par cette référence.</p>
<p>Les tableaux sont spécialisés pour stocker des éléments multiples de même type, mais les objets en général peuvent être utilisés pour <strong>encapsuler</strong> n’importe quels types de données.</p>
<p>Par exemple, un objet de type <code>String</code> encapsule en fait un tableau de caractères :</p>
<pre class=" language-java"><code class="prism  language-java">String mot <span class="token operator">=</span> <span class="token string">"coq"</span><span class="token punctuation">;</span>
</code></pre>
<p><img src="https://lh3.googleusercontent.com/CGpZvIBk-gq1l35NFcZQgHJqhYzNELSMSOmDZVutilpOKp0or3GhpshBhlJHyYoVAODFR5aBXXq0" alt="enter image description here"><br>
La variable <code>mot</code> est une <em>référence</em> à une <code>String</code> (un emplacement mémoire qui pointe sur un objet de type <code>String</code>). Cela se traduit par une flèche dans le diagramme de mémoire, qui pointe vers l’objet référencé, à un endroit complètement différent en mémoire. En interne, l’objet de type <code>String</code> contient lui-même une référence à un tableau de caractères (deuxième flèche), qui va contenir les lettres qui composent la chaîne.</p>
<p>Quand on veut tester si deux valeurs de type primitif sont égales, on utilise simplement l’opérateur de comparaison <code>==</code>. Vous êtes maintenant en mesure de comprendre pourquoi il ne faut pas comparer des strings avec <code>==</code>, mais avec la méthode dédiée <code>equals()</code> : dans <code>(str1 == str2)</code>, <code>==</code> va tester si les deux valeurs sont égales. Mais ces deux valeurs ne sont que des références, pas les strings elles-mêmes. Si les deux strings ont la même référence, alors leur contenu (chaîne) sera effectivement le même, puisque c’est le même objet (<code>==</code> est évalué à <code>true</code> et tout va bien). Mais il est tout à fait possible que deux strings n’aient pas la même référence alors qu’elles contiennent des chaînes de caractères identiques. Dans ce cas, <code>==</code> est évalué à <code>false</code>…</p>
<p>La méthode <code>equals()</code> de la classe <code>String</code>, en revanche, va aller vérifier les <em>contenus</em> des objets de type <code>String</code> (les chaînes de caractères en interne), même si les références ne sont pas les mêmes, pour renvoyer le résultat attendu : <code>if (str1.equals(str2)) { ... }</code></p>
<h2 id="la-valeur-null">La valeur <code>null</code></h2>
<p>En Java, le mot-clé <code>null</code> est une valeur spéciale qui signifie « pas d’objet ». Elle est valide pour n’importe quel type d’objet. Vous pouvez déclarer une variable de type objet et l’initialiser à <code>null</code> : <code>String rien = null;</code></p>
<p>Si vous utilisez une variable <code>null</code> en tentant d’invoquer une méthode, par exemple, Java lancera une exception de type <code>NullPointerException</code> :</p>
<pre class=" language-java"><code class="prism  language-java">String nom <span class="token operator">=</span> null<span class="token punctuation">;</span>
<span class="token keyword">int</span><span class="token punctuation">[</span><span class="token punctuation">]</span> nombres <span class="token operator">=</span> null<span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span>nom<span class="token punctuation">.</span>length<span class="token punctuation">)</span><span class="token punctuation">;</span> <span class="token comment">// NullPointerException</span>
<span class="token keyword">int</span> n <span class="token operator">=</span> nombres<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">]</span> <span class="token operator">+</span> <span class="token number">1</span><span class="token punctuation">;</span> <span class="token comment">// NullPointerException</span>
</code></pre>
<p>Mais on peut tout à fait passer des références <code>null</code> en argument de méthode, ou retourner <code>null</code> depuis une méthode (du moment que le type de retour est un type objet). Il faut juste penser à vérifier les références potentiellement nulles avant d’utiliser l’objet :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">if</span> <span class="token punctuation">(</span>nombre <span class="token operator">!=</span> null<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  n <span class="token operator">=</span> nombre<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">]</span> <span class="token operator">+</span> <span class="token number">1</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>L’erreur <code>NullPointerException</code> est l’une des plus fréquente en Java, et dans les langages qui autorisent les références <code>null</code> en général. C’est pourquoi certains langages plus récents ont banni complètement cette possibilité.</p>
<h2 id="les-strings--des-objets-immuables">Les strings : des objets immuables</h2>
<p>Nous avons vu que les méthodes <code>toLowerCase()</code> et <code>toUpperCase()</code> de la classe <code>String</code> convertissent des chaînes de caractères en minuscules ou majuscules. De telles méthodes sont souvent source de confusion parce qu’on a l’impression qu’elle vont modifier la string concernée. Mais ces méthodes (pas plus que d’autres) ne peuvent pas modifier une string, car les strings sont <strong>immuables</strong> (<em><strong>immutable</strong></em>).</p>
<p>Comment agissent-elles alors ? Elles <em>retournent une nouvelle string</em> :</p>
<pre class=" language-java"><code class="prism  language-java">String nom <span class="token operator">=</span> <span class="token string">"Céline Kevin"</span><span class="token punctuation">;</span>
String nomEnMaj <span class="token operator">=</span> nom<span class="token punctuation">.</span><span class="token function">toUpperCase</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span> <span class="token comment">// "CÉLINE KEVIN"</span>
</code></pre>
<p>La string à laquelle se réfère la variable <code>nom</code> n’est pas modifiée dans ce code. Une nouvelle variable a été créée pour recevoir la string transformée. Si vous voulez vraiment changer <code>nom</code>, vous devez réaffecter la valeur retournée à la variable :</p>
<pre class=" language-java"><code class="prism  language-java">String nom <span class="token operator">=</span> <span class="token string">"Céline Kevin"</span><span class="token punctuation">;</span>
nom <span class="token operator">=</span> nom<span class="token punctuation">.</span><span class="token function">toUpperCase</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>  <span class="token comment">// OK, réaffectation</span>
</code></pre>
<p>Faire comme si <code>nom</code> était modifiée lors de l’appel de la méthode est une erreur <em>très</em> courante avec les objets immuables en général :</p>
<pre class=" language-java"><code class="prism  language-java">String nom <span class="token operator">=</span> <span class="token string">"Céline Kevin"</span><span class="token punctuation">;</span>
nom<span class="token punctuation">.</span><span class="token function">toUpperCase</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span> <span class="token comment">// ignore la valeur retournée !</span>
                   <span class="token comment">// 'nom' n'a pas été modifiée</span>
</code></pre>
<p>Un autre exemple : la méthode <code>replace()</code>, qui recherche et remplace un pattern dans une string. Là encore, omettre la réaffectation est fréquent :</p>
<pre class=" language-java"><code class="prism  language-java">String declaration <span class="token operator">=</span> <span class="token string">"Céline aime Kevin"</span><span class="token punctuation">;</span>
declaration <span class="token operator">=</span> declaration<span class="token punctuation">.</span><span class="token function">replace</span><span class="token punctuation">(</span><span class="token string">"Kevin"</span><span class="token punctuation">,</span> <span class="token string">"Dominique"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<h2 id="classes-wrappers">Classes <em>wrappers</em></h2>
<p>Les types primitifs ne sont pas des classes, et donc une variable d’un type primitif ne peut pas être <code>null</code>. Ils ne fournissent pas non plus de méthodes. Par exemple : <code>entier.equals(5)</code> est illégal si <code>entier</code> est de type <code>int</code>.</p>
<p>Cependant, pour chaque type primitif, il existe une <strong>classe</strong> <em><strong>wrapper</strong></em> correspondante dans la JCL. Par exemple, la classe <em>wrapper</em> du type <code>int</code> s’appelle <code>Integer</code> (notez la majuscule) :</p>
<pre class=" language-java"><code class="prism  language-java">Integer entier <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Integer</span><span class="token punctuation">(</span><span class="token number">5</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>entier<span class="token punctuation">.</span><span class="token function">equals</span><span class="token punctuation">(</span><span class="token number">5</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>  <span class="token comment">// OK, true</span>
</code></pre>
<p>Les autres classes <em>wrappers</em> sont, naturellement : <code>Byte, Short, Long, Float, Double, Character, Boolean</code>. Elles sont dans le package <code>java.lang</code>, et donc automatiquement importées.</p>
<p>Comme une string, un objet d’une classe <em>wrapper</em> est immuable. Pour comparer les valeurs, il faudra également utiliser <code>equals</code> plutôt que <code>==</code>.</p>
<pre class=" language-java"><code class="prism  language-java">Integer x <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Integer</span><span class="token punctuation">(</span><span class="token number">123</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
Integer y <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Integer</span><span class="token punctuation">(</span><span class="token number">123</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">if</span> <span class="token punctuation">(</span>x <span class="token operator">==</span> y<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"x et y référencent le même objet"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
<span class="token keyword">if</span> <span class="token punctuation">(</span>x<span class="token punctuation">.</span><span class="token function">equals</span><span class="token punctuation">(</span>y<span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"x et y ont la même valeur"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>

<span class="token operator">&gt;</span> x et y ont la même valeur
</code></pre>
<p>Les deux variables ne référencent pas le même objet.</p>
<p>Une classe <em>wrapper</em> :</p>
<ul>
<li>définit les constantes <code>MIN_VALUE</code> et <code>MAX_VALUE</code>. Exemple : <code>Integer.MIN_VALUE</code> vaut <code>-2147483648</code></li>
<li>fournit des méthodes de conversion de string vers et depuis un type primitif :
<ul>
<li><code>Integer.parseInt("123")</code> convertit la string <code>"123"</code> et retourne un objet <code>Integer</code> correspondant (<code>NumberFormatException</code> si la conversion échoue)</li>
<li><code>Integer.toString(123)</code> convertit l’entier <code>123</code> et retourne la string correspondante <code>"123"</code></li>
</ul>
</li>
</ul>
<p>Mais à part ces fonctionnalités accessibles directement sur la classe, en règle générale, pourquoi s’embêterait-on avec des objets de type <em>wrapper</em> plutôt que d’utiliser le type primitif ?</p>
<ul>
<li>Vous avez besoin que la valeur puisse être <code>null</code></li>
<li>Vous voulez une collection de ces valeurs : les classes permettant de stocker des collections sont une alternative aux tableaux et elles n’acceptent de stocker que des objets, pas des valeurs primitives</li>
</ul>
<h2 id="la-classe-biginteger">La classe <code>BigInteger</code></h2>
<p>Il existe d’autres types dans la JCL qui peuvent représenter des objets. Quand vous avez besoin d’entiers très grands (plus grands que Long.MAX_VALUE), vous pouvez avoir recours à la classe spécialisée <code>BigInteger</code>. Un objet de cette classe peut représenter des entiers arbitrairement longs (il n’y a pas de limite, excepté bien sûr la taille de la mémoire disponible) :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">import</span> java<span class="token punctuation">.</span>math<span class="token punctuation">.</span>BigInteger<span class="token punctuation">;</span>
<span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">.</span>
<span class="token keyword">long</span> n <span class="token operator">=</span> <span class="token number">17</span><span class="token punctuation">;</span>
BigInteger big <span class="token operator">=</span> BigInteger<span class="token punctuation">.</span><span class="token function">valueOf</span><span class="token punctuation">(</span>n<span class="token punctuation">)</span><span class="token punctuation">;</span>
String s <span class="token operator">=</span> <span class="token string">"12345678901234567890"</span><span class="token punctuation">;</span>
BigInteger bigger <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">BigInteger</span><span class="token punctuation">(</span>s<span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token comment">// Les opérateurs usuels ne fonctionnent pas</span>
BigInteger marchePas <span class="token operator">=</span> big <span class="token operator">+</span> bigger<span class="token punctuation">;</span> <span class="token comment">// Erreur de compilation</span>
BigInteger ok <span class="token operator">=</span> big<span class="token punctuation">.</span><span class="token function">add</span><span class="token punctuation">(</span>bigger<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p>Les objets de type <code>BigInteger</code> sont immuables : les méthodes arithmétiques retournent la nouvelle valeur mais ne changent ni l’objet traité (<code>big</code> dans l’appel de <code>add()</code> ) ni les paramètres (ici <code>bigger</code>).</p>
<p>En interne (dans la classe), <code>BigInteger</code> encapsule un tableau de <code>int</code> (tout comme <code>String</code> encapsule un tableau de <code>char</code>). Chaque <code>int</code> représente une portion de l’entier. Les méthodes de <code>BigInteger</code> doivent travailler avec cette représentation complexe pour calculer les valeurs demandées mais <em>rien de tout cela ne transparaît à l’utilisateur de la classe</em>.</p>
<p>Sachez qu’il existe une classe équivalente pour traiter de très grands nombres flottants : <code>BigDecimal</code> (qui d’ailleurs, en interne, encapsule un <code>BigInteger</code> pour stocker le nombre).</p>
<h2 id="encapsulation-et-généralisation">Encapsulation et généralisation</h2>
<p>Ce chapitre a introduit deux concepts très importants, qui aident à gérer la complexité des programmes de grande taille :</p>
<ul>
<li>l’<strong>encapsulation</strong> permet à des objets d’utiliser en interne d’autres types de données, de manière transparente pour l’utilisateur de la classe, et d’englober les fonctionnalités (méthodes) de la classe</li>
<li>L’<strong>immuabilité</strong> permet de ne travailler qu’avec des objets dont on est certain qu’ils ne changent pas</li>
</ul>
<p>L’une des difficultés du développement, tout particulièrement pour le débutant, est de savoir de quelle manière il faudrait diviser un programme en méthodes. Le « <strong>procédé d’encapsulation/généralisation</strong> » vous suggère de concevoir le programme au fur et à mesure. Ici l’encapsulation est vue d’abord du point de vue des fonctionnalités (méthodes) plutôt que des données internes.</p>
<ol>
<li>On écrit les quelques lignes de code qui « font » quelque chose, et on teste</li>
<li>Quand ça fonctionne, on <strong>encapsule</strong> le service dans une nouvelle méthode, et on teste</li>
<li>Quand c’est possible, on <strong>généralise</strong> le code de la méthode en utilisant variables et paramètres</li>
</ol>
<p>C’est assez similaire au « développement incrémental » que l’on a abordé précédemment (écrire, tester, répéter) mais ici, la « signature » de la méthode (paramètres) est « découverte » <em>a posteriori</em>.</p>
<p>Écrivons un programme d’affichage de tables de multiplications :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">1</span><span class="token punctuation">;</span> i <span class="token operator">&lt;=</span> <span class="token number">10</span><span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">printf</span><span class="token punctuation">(</span><span class="token string">"%4d"</span><span class="token punctuation">,</span> <span class="token number">2</span> <span class="token operator">*</span> i<span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span>    <span class="token number">2</span>   <span class="token number">4</span>   <span class="token number">6</span>   <span class="token number">8</span>  <span class="token number">10</span>  <span class="token number">12</span>  <span class="token number">14</span>  <span class="token number">16</span>  <span class="token number">18</span>  <span class="token number">20</span> 
</code></pre>
<p>Ça fonctionne. Encapsulons ça dans une méthode :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">void</span> <span class="token function">afficherLigne</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">1</span><span class="token punctuation">;</span> i <span class="token operator">&lt;=</span> <span class="token number">10</span><span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">printf</span><span class="token punctuation">(</span><span class="token string">"%4d"</span><span class="token punctuation">,</span> <span class="token number">2</span> <span class="token operator">*</span> i<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>Généralisons maintenant la méthode pour lui permettre d’afficher autre chose que la table de 2 :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">void</span> <span class="token function">afficherTable</span><span class="token punctuation">(</span><span class="token keyword">int</span> n<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">1</span><span class="token punctuation">;</span> i <span class="token operator">&lt;=</span> <span class="token number">10</span><span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">printf</span><span class="token punctuation">(</span><span class="token string">"%4d"</span><span class="token punctuation">,</span> n <span class="token operator">*</span> i<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
<span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">.</span>
<span class="token function">afficherTable</span><span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span>    <span class="token number">3</span>   <span class="token number">6</span>   <span class="token number">9</span>  <span class="token number">12</span>  <span class="token number">15</span>  <span class="token number">18</span>  <span class="token number">21</span>  <span class="token number">24</span>  <span class="token number">27</span>  <span class="token number">30</span> 
</code></pre>
<p>On peut alors afficher les tables de multiplication de 1 à 10 en itérant sur le paramètre :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">1</span><span class="token punctuation">;</span> i <span class="token operator">&lt;=</span> <span class="token number">10</span><span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token function">afficherTable</span><span class="token punctuation">(</span>i<span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>

<span class="token operator">&gt;</span>    <span class="token number">1</span>   <span class="token number">2</span>   <span class="token number">3</span>   <span class="token number">4</span>   <span class="token number">5</span>   <span class="token number">6</span>   <span class="token number">7</span>   <span class="token number">8</span>   <span class="token number">9</span>  <span class="token number">10</span>
<span class="token operator">&gt;</span>    <span class="token number">2</span>   <span class="token number">4</span>   <span class="token number">6</span>   <span class="token number">8</span>  <span class="token number">10</span>  <span class="token number">12</span>  <span class="token number">14</span>  <span class="token number">16</span>  <span class="token number">18</span>  <span class="token number">20</span>
<span class="token operator">&gt;</span>    <span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">.</span>
<span class="token operator">&gt;</span>   <span class="token number">10</span>  <span class="token number">20</span>  <span class="token number">30</span>  <span class="token number">40</span>  <span class="token number">50</span>  <span class="token number">60</span>  <span class="token number">70</span>  <span class="token number">80</span>  <span class="token number">90</span> <span class="token number">100</span>
</code></pre>
<p>Cela est similaire au loops imbriqués que nous avons déjà vus, excepté qu’ici, la boucle intérieure est encapsulée dans la méthode <code>afficherTable()</code>. Nous pouvons encore encapsuler la boucle restante dans sa propre méthode :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">void</span> <span class="token function">afficherTables</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">1</span><span class="token punctuation">;</span> i <span class="token operator">&lt;=</span> <span class="token number">10</span><span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token function">afficherTable</span><span class="token punctuation">(</span>i<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<p>Pour l’instant, cela affiche toujours les tables de 1 à 10. On peut également la généraliser en donnant par exemple un intervalle de tables à afficher :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">void</span> <span class="token function">afficherTables</span><span class="token punctuation">(</span><span class="token keyword">int</span> debut<span class="token punctuation">,</span> <span class="token keyword">int</span> fin<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> debut<span class="token punctuation">;</span> i <span class="token operator">&lt;=</span> fin<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token function">afficherTable</span><span class="token punctuation">(</span>i<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<p>Et on pourrait enfin généraliser <code>afficherTable()</code> en lui donnant un paramètre supplémentaire : le nombre de colonnes à afficher. On généralise au passage <code>afficherTables()</code> de la même façon :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">void</span> <span class="token function">afficherTable</span><span class="token punctuation">(</span><span class="token keyword">int</span> n<span class="token punctuation">,</span> <span class="token keyword">int</span> colonnes<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">1</span><span class="token punctuation">,</span> i <span class="token operator">&lt;=</span> colonnes<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">printf</span><span class="token punctuation">(</span><span class="token string">"%4d"</span><span class="token punctuation">,</span> n <span class="token operator">*</span> i<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>

<span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">void</span> <span class="token function">afficherTables</span><span class="token punctuation">(</span><span class="token keyword">int</span> debut<span class="token punctuation">,</span> <span class="token keyword">int</span> fin<span class="token punctuation">,</span> <span class="token keyword">int</span> colonnes<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> debut<span class="token punctuation">;</span> i <span class="token operator">&lt;=</span> fin<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token function">afficherTable</span><span class="token punctuation">(</span>i<span class="token punctuation">,</span> colonnes<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span>
<span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">.</span>
<span class="token function">afficherTables</span><span class="token punctuation">(</span><span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token number">12</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span>    <span class="token number">4</span>   <span class="token number">8</span>  <span class="token number">12</span>  <span class="token number">16</span>  <span class="token number">20</span>  <span class="token number">24</span>  <span class="token number">28</span>  <span class="token number">32</span>  <span class="token number">36</span>  <span class="token number">40</span>  <span class="token number">44</span>  <span class="token number">48</span>
<span class="token operator">&gt;</span>    <span class="token number">5</span>  <span class="token number">10</span>  <span class="token number">15</span>  <span class="token number">20</span>  <span class="token number">25</span>  <span class="token number">30</span>  <span class="token number">35</span>  <span class="token number">40</span>  <span class="token number">45</span>  <span class="token number">50</span>  <span class="token number">55</span>  <span class="token number">60</span> 
</code></pre>
<p>Le procédé d’encapsulation/généralisation peut rendre le code plus facile à écrire, plus polyvalent, plus réutilisable, et plus facile à maintenir.</p>

