---


---

<h1 id="chapitre-6">Chapitre 6</h1>
<h1 id="boucles-et-strings">Boucles et Strings</h1>
<p>Les ordinateurs sont très bons pour effectuer des tâches répétitives. Nous apprendrons comment écrire des algorithmes avec boucles pour introduire les répétitions automatiques dans notre code. Nous verrons aussi quelques méthodes utilitaires de la classe <code>String</code> qui résolvent des problèmes courants.</p>
<h2 id="linstruction-while">L’instruction <code>while</code></h2>
<p>L’instruction <code>while</code> permet de répéter un bloc de code :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span> n <span class="token operator">=</span> <span class="token number">3</span><span class="token punctuation">;</span>
<span class="token keyword">while</span> <span class="token punctuation">(</span>n <span class="token operator">&gt;</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span>n <span class="token operator">+</span> <span class="token string">" "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  n <span class="token operator">=</span> n <span class="token operator">-</span> <span class="token number">1</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"BOUM !!!"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span> <span class="token number">3</span> <span class="token number">2</span> <span class="token number">1</span> BOUM <span class="token operator">!</span><span class="token operator">!</span><span class="token operator">!</span>
</code></pre>
<p>Ça se lit très bien en français : « Commence avec <code>n</code> à <code>3</code>. <strong>Tant que</strong> (<em><strong>while</strong></em>) <code>n</code> est positif, affiche <code>n</code> et décrémente sa valeur de <code>1</code>. Puis affiche “BOUM !”.</p>
<p>Le flux d’exécution de l’instruction <code>while</code> est le suivant :</p>
<ol>
<li>Évaluer la condition entre parenthèses (<code>true</code> ou <code>false</code>).</li>
<li>Si la condition est <code>false</code>, sauter à la prochaine instruction (après les accolades).</li>
<li>Si elle est <code>true</code>, exécuter le bloc d’instructions puis retourner à l’étape 1.</li>
</ol>
<p>Ça s’appelle une <strong>boucle</strong>, parce qu’on répète en boucle la même chose tant que la condition est vraie.</p>
<p>Le <strong>corps</strong> de la boucle (le bloc entre accolades) devrait changer la valeur de la variable (ou des variables) testées dans la condition du <code>while</code> pour que cette condition devienne <code>false</code> à un certain moment. Sinon la boucle se répète sans fin, c’est ce qu’on appelle une <strong>boucle infinie</strong> (le programme « ne répond plus »).</p>
<h2 id="incrément-et-décrément">Incrément et décrément</h2>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">1</span><span class="token punctuation">;</span>
<span class="token keyword">while</span> <span class="token punctuation">(</span>i <span class="token operator">&lt;=</span> <span class="token number">5</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>i<span class="token punctuation">)</span><span class="token punctuation">;</span>
  i<span class="token operator">++</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>Augmenter la valeur d’une variable de <code>1</code> (<strong>incrémenter</strong>) est tellement courant que Java fournit un opérateur dédié : l’<strong>opérateur d’incrémentation <code>++</code></strong> (<em><strong>increment operator</strong></em>). L’instruction <code>i++</code> a le même effet que l’instruction <code>i = i + 1</code>.</p>
<p>L’<strong>opérateur de décrémentation <code>--</code></strong> (<em><strong>decrement operator</strong></em>) existe également : <code>i--</code> équivaut à <code>i = i - 1</code>.</p>
<p>Java offre également les opérateurs <code>+=</code> et <code>-=</code> qui permettent d’ajouter ou de soustraire de valeurs autres que 1 :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">2</span><span class="token punctuation">;</span>
<span class="token keyword">while</span> <span class="token punctuation">(</span>i <span class="token operator">&lt;</span> <span class="token number">20</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span>i <span class="token operator">+</span> <span class="token string">", "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  i <span class="token operator">+=</span> <span class="token number">2</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">" et 20."</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token number">12</span><span class="token punctuation">,</span> <span class="token number">14</span><span class="token punctuation">,</span> <span class="token number">16</span><span class="token punctuation">,</span> <span class="token number">18</span><span class="token punctuation">,</span> et <span class="token number">20</span><span class="token punctuation">.</span>
</code></pre>
<p>Mais les boucles <code>while</code> sont plus couramment utilisées lorsque l’on ne connaît pas à l’avance le nombre d’<strong>itérations</strong> (répétitions) qui seront exécutées :</p>
<pre class=" language-java"><code class="prism  language-java">Scanner in <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Scanner</span><span class="token punctuation">(</span>System<span class="token punctuation">.</span>in<span class="token punctuation">)</span><span class="token punctuation">;</span>
String reponse <span class="token operator">=</span> <span class="token string">"oui"</span><span class="token punctuation">;</span>
<span class="token keyword">while</span> <span class="token punctuation">(</span>reponse<span class="token punctuation">.</span><span class="token function">isEqual</span><span class="token punctuation">(</span><span class="token string">"oui"</span><span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span><span class="token string">"Entrez un nombre entier : "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token keyword">int</span> n <span class="token operator">=</span> in<span class="token punctuation">.</span><span class="token function">nextInt</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token keyword">if</span> <span class="token punctuation">(</span>n <span class="token operator">%</span> <span class="token number">2</span> <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"C'est un nombre pair !"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span> <span class="token keyword">else</span> <span class="token punctuation">{</span>
    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"C'est un nombre impair !"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span><span class="token string">"On joue encore (oui/non) ? "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  reponse <span class="token operator">=</span> in<span class="token punctuation">.</span><span class="token function">next</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span> 
</code></pre>
<p>Pour les boucles dont le nombre d’itérations est plus évident, on utilise plutôt l’instruction <code>for</code>.</p>
<h2 id="linstruction-for">L’instruction <code>for</code></h2>
<p>Voici une nouvelle version du « 2, 4, 6… » :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">2</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> <span class="token number">20</span><span class="token punctuation">;</span> i <span class="token operator">+=</span> <span class="token number">2</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span>i <span class="token operator">+</span> <span class="token string">", "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">" et 20."</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token number">12</span><span class="token punctuation">,</span> <span class="token number">14</span><span class="token punctuation">,</span> <span class="token number">16</span><span class="token punctuation">,</span> <span class="token number">18</span><span class="token punctuation">,</span> et <span class="token number">20</span><span class="token punctuation">.</span>
</code></pre>
<p>La boucle <code>for</code> a trois composantes entre parenthèses, séparées par des points-virgules, et suivies du bloc de code à répéter entre accolades.</p>
<ol>
<li><strong>Initialisation</strong> (<em><strong>Initializer</strong></em>) : exécuté une seule fois, au tout début de la boucle (équivalent à l’initialisation de la variable généralement juste au-dessus d’un <code>while</code>). Ici on initialise la variable <code>i</code> de type <code>int</code> à la valeur <code>2</code> (les variables utilisées dans un <code>for</code> sont presque toujours des <code>int</code>).</li>
<li><strong>Condition</strong> : vérifiée avant chaque itération, comme pour un <code>while</code>. Si elle est <code>false</code>, la boucle se termine. Sinon, on exécute le corps de la boucle. Ici la condition testée à chaque fois est : <code>i &lt; 20</code>.</li>
<li><strong>Mise à jour</strong> (<em><strong>update</strong></em>) : exécuté à la fin de chaque itération, avant de retourner à l’étape 2 pour le nouveau test. C’est ici que la variable de la phase initialisation est mise à jour. Ici on incrémente <code>i</code> de 2 en 2.</li>
</ol>
<p>Une fois que la construction est familière, l’instruction <code>for</code> est plus facile à lire qu’un <code>while</code> parce qu’elle place tout ce qui est relatif à la variable testée au même endroit.</p>
<p>Une autre différence est à noter par rapport à l’instruction <code>while</code> : une variable déclarée et initialisée dans l’<em>initializer</em> est locale à la boucle, c’est-à-dire qu’elle n’existe plus une fois le <code>for</code> terminé. Si vous avez besoin de cette variable en sortie de boucle, vous devez la déclarer avant l’instruction <code>for</code>.</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span> n<span class="token punctuation">;</span>
<span class="token keyword">for</span> <span class="token punctuation">(</span>n <span class="token operator">=</span> <span class="token number">3</span><span class="token punctuation">;</span> n <span class="token operator">&gt;</span> <span class="token number">0</span><span class="token punctuation">;</span> n<span class="token operator">--</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>n<span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"n vaut maintenant "</span> <span class="token operator">+</span> n<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span> n vaut maintenant <span class="token number">0</span>
</code></pre>
<h2 id="linstruction-do-...-while">L’instruction <code>do ... while</code></h2>
<p>Il existe une troisième forme de boucles en Java, c’est la boucle <strong>Répéter tant que</strong> (<em><strong>do while</strong></em>). C’est une forme très similaire à la boucle <em><strong>while</strong></em> ; la seule différence (hormis la syntaxe) est que, dans un <em><strong>do while</strong></em>, le corps de la boucle est exécuté <em>avant</em> le test de la condition. On a donc l’assurance que le bloc sera exécuté <em>au moins une fois</em>, même si la condition est <code>false</code> dès le départ.</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">6</span><span class="token punctuation">;</span>
<span class="token keyword">do</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>i<span class="token punctuation">)</span><span class="token punctuation">;</span>
  i<span class="token operator">++</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span> <span class="token keyword">while</span> <span class="token punctuation">(</span>i <span class="token operator">&lt;=</span> <span class="token number">5</span><span class="token punctuation">)</span>

<span class="token operator">&gt;</span> <span class="token number">6</span>
</code></pre>
<p>Ici, la condition n’est jamais à <code>true</code>. Pourtant, le corps est exécuté une fois avant le premier test négatif.</p>
<p>Le flux d’exécution de l’instruction <code>do while</code> est le suivant :</p>
<ol>
<li>Exécuter le corps de la boucle.</li>
<li>Évaluer la condition entre parenthèses (<code>true</code> ou <code>false</code>).</li>
<li>Si la condition est <code>false</code>, sortir de la boucle.</li>
<li>Si elle est <code>true</code>, retourner à l’étape 1.</li>
</ol>
<p>La boucle <em>do while</em> est utilisée quand on veut absolument que le corps soit exécuté au moins une fois. C’est souvent parce que la variable évaluée dans la condition est initialisée dans la boucle. Par exemple, elle est dépendante d’une entrée utilisateur : vous devez attendre d’avoir la première entrée avant de savoir si elle est correcte ou non, pour décider si vous devez recommencer la demande ou pas.</p>
<h2 id="quelle-boucle-choisir-">Quelle boucle choisir ?</h2>
<p>Il faut savoir qu’il est possible de transformer une des trois formes de boucles dans n’importe laquelle des deux autres. Vous devez choisir la boucle qui est la plus « naturelle » quand vous essayez d’exprimer ce que doit faire votre algorithme.</p>
<ul>
<li>Je dois exécuter <code>n</code>  fois ? <code>for (int i = 0; i &lt; n; i++) { ... }</code></li>
<li>Je dois exécuter jusqu’à <code>n</code>, mais seulement 1 index sur 2 ? <code>for (int i = 0; i &lt;= n; i += 2) { ... }</code></li>
<li>Je parcours un tableau ? <code>for(...)</code> (syntaxe spéciale, voir chapitre sur les tableaux)</li>
<li>C’est trop compliqué pour être lisible dans un <code>for</code> ? Alors : <code>while (...) { ... }</code></li>
<li>Sauf si le corps doit absolument être exécuté au moins une fois. Alors : <code>do { ... } while ( ... )</code></li>
</ul>
<p>La boucle <code>for</code> doit être votre premier choix. C’est souvent le plus naturel parce qu’on sait combien d’itérations seront nécessaires. Si ce n’est pas le cas, c’est souvent parce que la mise à jour de la variable de condition (ou des variables) est complexe. Le choix entre les deux boucles restantes se résume alors à répondre à la question : le corps doit-il être exécuté au moins une fois ?</p>
<h2 id="boucles-imbriquées">Boucles imbriquées</h2>
<p>Comme les instructions conditionnelles, les boucles peuvent être imbriquées (<em><strong>nested loops</strong></em>);</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> x <span class="token operator">=</span> <span class="token number">1</span><span class="token punctuation">;</span> x <span class="token operator">&lt;=</span> <span class="token number">10</span><span class="token punctuation">;</span> x<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> y <span class="token operator">=</span> <span class="token number">1</span><span class="token punctuation">;</span> y <span class="token operator">&lt;=</span> <span class="token number">10</span><span class="token punctuation">;</span> y<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">printf</span><span class="token punctuation">(</span><span class="token string">"%4d"</span><span class="token punctuation">,</span> x <span class="token operator">*</span> y<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>

<span class="token operator">&gt;</span>    <span class="token number">1</span>   <span class="token number">2</span>   <span class="token number">3</span>   <span class="token number">4</span>   <span class="token number">5</span>   <span class="token number">6</span>   <span class="token number">7</span>   <span class="token number">8</span>   <span class="token number">9</span>  <span class="token number">10</span>
<span class="token operator">&gt;</span>    <span class="token number">2</span>   <span class="token number">4</span>   <span class="token number">6</span>   <span class="token number">8</span>  <span class="token number">10</span>  <span class="token number">12</span>  <span class="token number">14</span>  <span class="token number">16</span>  <span class="token number">18</span>  <span class="token number">20</span>
<span class="token operator">&gt;</span>    <span class="token number">3</span>   <span class="token number">6</span>   <span class="token number">9</span>  <span class="token number">12</span>  <span class="token number">15</span>  <span class="token number">18</span>  <span class="token number">21</span>  <span class="token number">24</span>  <span class="token number">27</span>  <span class="token number">30</span>
<span class="token operator">&gt;</span>    <span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">.</span>
<span class="token operator">&gt;</span>   <span class="token number">10</span>  <span class="token number">20</span>  <span class="token number">30</span>  <span class="token number">40</span>  <span class="token number">50</span>  <span class="token number">60</span>  <span class="token number">70</span>  <span class="token number">80</span>  <span class="token number">90</span> <span class="token number">100</span>
</code></pre>
<p>Des variables comme <code>x</code> et <code>y</code> sont appelées <strong>variables de boucles</strong> (<em><strong>loop variables</strong></em>) : ce sont elles qui vont contrôler l’exécution de la boucle. La première boucle (<code>for x</code>) s’appelle la <strong>boucle extérieure</strong> (<em><strong>outer loop</strong></em>) et la seconde (<code>for y</code>) est la <strong>boucle intérieure</strong> (<em><strong>inner loop</strong></em>).</p>
<p>Chaque boucle répète son bloc 10 fois. La boucle extérieure itère de 1 à 10 seulement une fois, tandis que la boucle intérieure (étant donc dans le bloc itéré 10 fois) va itérer 10 fois pour chacun de ces 10 cycles. Le <code>printf</code> va donc être invoqué 10 x 10 = 100 fois en tout.</p>
<p>Le spécificateur de format <code>%4d</code> affiche un entier (<code>d</code>) sur 4 caractères, en remplissant avec des espaces si nécessaire. Cela permet d’aligner les nombres verticalement.</p>
<p>Prenez bien le temps de comprendre pourquoi chaque table de multiplication est affichée sur sa propre ligne : la boucle intérieure se charge de l’affichage de cette ligne et, quand elle a terminé, la dernière instruction de la boucle extérieure est un passage à la ligne, préparant ainsi l’affichage de la ligne suivante.</p>
<h2 id="strings">Strings</h2>
<p>Le type <code>String</code> étant très utilisé, il est important d’en connaître un peu plus sur cette classe.</p>
<p><code>String</code> est une classe fournie dans le package <code>java.lang</code>, donc pas besoin d’importer quoi que ce soit pour l’utiliser. Tout littéral de la forme <code>"ceci est une string"</code> dans le code sera interprété par Java comme un objet de cette classe.  Une <em>string</em> Java représente une chaîne de caractères UTF-16 (un <em>code point</em> - caractère - étant encodé sur 1 ou 2 <em>code units</em>), et en conséquence <strong>certains caractères seront encodés avec deux <code>char</code> de Java</strong>.</p>
<p>La classe <code>String</code> fournit une bonne cinquantaine de méthodes, dont un bon nombre se révèlent régulièrement utiles. Voici le top 20 :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token comment">// Retourne le code unit (et donc pas forcément le caractère !) à l'index spécifié.</span>
<span class="token keyword">char</span> <span class="token function">charAt</span><span class="token punctuation">(</span><span class="token keyword">int</span> index<span class="token punctuation">)</span>

<span class="token comment">// Retourne le code point à cet index</span>
<span class="token keyword">int</span> <span class="token function">codePointAt</span><span class="token punctuation">(</span><span class="token keyword">int</span> index<span class="token punctuation">)</span>

<span class="token comment">// retourne negatif si la string est avant other dans l'ordre alphabétique</span>
<span class="token comment">// positif si après</span>
<span class="token comment">// 0 si égales </span>
<span class="token keyword">int</span> <span class="token function">compareTo</span><span class="token punctuation">(</span>String other<span class="token punctuation">)</span>

<span class="token comment">// true si vide</span>
<span class="token keyword">boolean</span> <span class="token function">empty</span><span class="token punctuation">(</span><span class="token punctuation">)</span>

<span class="token comment">// true si que des espaces (Java 11)</span>
<span class="token keyword">boolean</span> <span class="token function">blank</span><span class="token punctuation">(</span><span class="token punctuation">)</span>

<span class="token comment">// true si égales</span>
<span class="token keyword">boolean</span> <span class="token function">equals</span><span class="token punctuation">(</span>Object other<span class="token punctuation">)</span>

<span class="token comment">// true si égales (en ignorant la casse)</span>
<span class="token keyword">boolean</span> <span class="token function">equalsIgnoreCase</span><span class="token punctuation">(</span>String other<span class="token punctuation">)</span>

<span class="token comment">// true si commence par "prefix"</span>
<span class="token keyword">boolean</span> <span class="token function">startsWith</span><span class="token punctuation">(</span>String prefix<span class="token punctuation">)</span>

<span class="token comment">// true si finit par "suffix"</span>
<span class="token keyword">boolean</span> <span class="token function">endsWith</span><span class="token punctuation">(</span>String suffix<span class="token punctuation">)</span>

<span class="token comment">// Retourne le départ de la première occurrence de str (ou du code point cp)</span>
<span class="token comment">// en démarrant à l'index 0 (ou à fromIndex)</span>
<span class="token comment">// -1 si pas trouvé</span>
<span class="token keyword">int</span> <span class="token function">indexOf</span><span class="token punctuation">(</span>String str<span class="token punctuation">)</span>
<span class="token keyword">int</span> <span class="token function">indexOf</span><span class="token punctuation">(</span>String str<span class="token punctuation">,</span> <span class="token keyword">int</span> fromIndex<span class="token punctuation">)</span>
<span class="token keyword">int</span> <span class="token function">indexOf</span><span class="token punctuation">(</span><span class="token keyword">int</span> cp<span class="token punctuation">)</span>
<span class="token keyword">int</span> <span class="token function">indexOf</span><span class="token punctuation">(</span><span class="token keyword">int</span> cp<span class="token punctuation">,</span> <span class="token keyword">int</span> fromIndex<span class="token punctuation">)</span>

<span class="token comment">// Retourne le départ de la dernière occurrence de str (ou du code point cp)</span>
<span class="token comment">// en démarrant à 0 (ou à fromIndex)</span>
<span class="token comment">// -1 si pas trouvé</span>
<span class="token keyword">int</span> <span class="token function">lastIndexOf</span><span class="token punctuation">(</span>String str<span class="token punctuation">)</span>
<span class="token keyword">int</span> <span class="token function">lastIndexOf</span><span class="token punctuation">(</span>String str<span class="token punctuation">,</span> <span class="token keyword">int</span> fromIndex<span class="token punctuation">)</span>
<span class="token keyword">int</span> <span class="token function">lastindexOf</span><span class="token punctuation">(</span><span class="token keyword">int</span> cp<span class="token punctuation">)</span>
<span class="token keyword">int</span> <span class="token function">lastindexOf</span><span class="token punctuation">(</span><span class="token keyword">int</span> cp<span class="token punctuation">,</span> <span class="token keyword">int</span> fromIndex<span class="token punctuation">)</span>

<span class="token comment">// Retourne le nombre de code units</span>
<span class="token keyword">int</span> <span class="token function">length</span><span class="token punctuation">(</span><span class="token punctuation">)</span>

<span class="token comment">// Retourne le nombre de code points entre les deux</span>
<span class="token keyword">int</span> <span class="token function">codePointCount</span><span class="token punctuation">(</span><span class="token keyword">int</span> startIndex<span class="token punctuation">,</span> <span class="token keyword">int</span> endIndex<span class="token punctuation">)</span>

<span class="token comment">// Retourne une nouvelle String remplaçant toutes les occurrences</span>
<span class="token comment">// de oldString par newString</span>
String <span class="token function">replace</span><span class="token punctuation">(</span>CharSequence oldString<span class="token punctuation">,</span> CharSequence newString<span class="token punctuation">)</span>

<span class="token comment">// Retourne la sous-chaine spécifiée par les index</span>
String <span class="token function">substring</span><span class="token punctuation">(</span><span class="token keyword">int</span> beginIndex<span class="token punctuation">)</span>
String <span class="token function">substring</span><span class="token punctuation">(</span><span class="token keyword">int</span> beginIndex<span class="token punctuation">,</span> <span class="token keyword">int</span> endIndex<span class="token punctuation">)</span>

<span class="token comment">// Retourne une nouvelle String en passant tout en minuscules ou majuscules</span>
String <span class="token function">toLowerCase</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
String <span class="token function">toUpperCase</span><span class="token punctuation">(</span><span class="token punctuation">)</span>

<span class="token comment">// Retourne une nouvelle String en éliminant les espaces de début et de fin</span>
String <span class="token function">trim</span><span class="token punctuation">(</span><span class="token punctuation">)</span>

<span class="token comment">// évolution de trim() qui prend en compte des espaces auparavant ignorés (Java 11)</span>
String <span class="token function">strip</span><span class="token punctuation">(</span><span class="token punctuation">)</span>

<span class="token comment">// Retourne une nouvelle String joignant les elements en les séparant par delimiter</span>
String <span class="token function">join</span><span class="token punctuation">(</span>CharSequence delimiter<span class="token punctuation">,</span> CharSequence<span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">.</span> elements<span class="token punctuation">)</span>

<span class="token comment">// Retourne une nouvelle String qui se répète count fois (Java 11)</span>
String <span class="token function">repeat</span><span class="token punctuation">(</span><span class="token keyword">int</span> count<span class="token punctuation">)</span>
</code></pre>
<blockquote>
<p><code>CharSequence</code> est une <em>interface</em>. Pour l’instant, considérez que toute <code>String</code> est une <code>CharSequence</code>.</p>
</blockquote>
<blockquote>
<p>Ne jamais utiliser <code>==</code> pour comparer des strings. <code>==</code> vérifie si deux variables se réfèrent au même <em>objet</em> en comparant les <em>références</em> (~ adresses mémoire). Or deux strings identiques peuvent très bien avoir des références différentes. À retenir, donc : <code>if (str1.equals(str2)) { ... }</code> et surtout pas <code>if (str1 == str2) { ... }</code></p>
</blockquote>
<p>On appelle ça l’<strong>API</strong> de la classe <code>String</code> (interface de programmation ou <em><strong>Application Programming Interface</strong></em>). Une API est l’ensemble des services (classes, méthodes…) que fournit un programme (ou un service web, ou une classe Java, ou une bibliothèque de classe spécialisées dans le graphisme 3D, etc.). La définition est donc très large. En gros c’est tout ce qu’il est possible d’utiliser dans l’entité concernée de manière programmatique. Par exemple, Google fournit une API officielle pour Google Drive : cela permet à un développeur de manipuler des fichiers sur un compte GDrive directement depuis le code de son application, en utilisant des méthodes « invoquées directement sur le web ».</p>
<p>La plupart des langages de haut niveau fournissent un type du genre de <code>String</code> et ces méthodes se retrouvent sous une forme ou une autre dans leur bibliothèque. Il en va de même pour tous les types assez standards (fichiers, dates, gestion de la langue…). Il faut avoir une idée de ce qu’il est probable de trouver directement fourni dans la JCL (ou dans la bibliothèque standard d’un autre langage) avant de « réinventer la roue » en implémentant une fonctionnalité basique qui existe déjà (sauf si c’est à titre d’exercice bien sûr). Il faut toujours se poser la question lors de la manipulation d’un type standard : <em>est-ce que la bibliothèque standard ne disposerait pas d’une méthode qui fait ça ?</em></p>
<h2 id="surcharge-de-méthodes">Surcharge de méthodes</h2>
<p>En Java, les méthodes peuvent être <strong>surchargées</strong> (<em><strong>overloaded</strong></em>) : plusieurs « versions » d’une méthode peuvent coexister. On le voit dans l’extrait de l’API de <code>String</code> plus haut. Certaines méthodes ont le même nom, mais diffèrent par leurs paramètres. Par exemple, il y a plusieurs versions de la méthode <code>subString()</code>, qui retourne une sous-chaîne d’une chaîne de caractères :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token comment">// Rappel de l'API</span>
String <span class="token function">substring</span><span class="token punctuation">(</span><span class="token keyword">int</span> beginIndex<span class="token punctuation">)</span>
String <span class="token function">substring</span><span class="token punctuation">(</span><span class="token keyword">int</span> beginIndex<span class="token punctuation">,</span> <span class="token keyword">int</span> endIndex<span class="token punctuation">)</span>

<span class="token comment">// Exemples d'utilisation</span>
String str <span class="token operator">=</span> <span class="token string">"banane"</span><span class="token punctuation">;</span>
String substr1 <span class="token operator">=</span> str<span class="token punctuation">.</span><span class="token function">subString</span><span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">;</span>     <span class="token comment">// "banane"</span>
String substr2 <span class="token operator">=</span> str<span class="token punctuation">.</span><span class="token function">subString</span><span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">)</span><span class="token punctuation">;</span>     <span class="token comment">// "nane"</span>
String substr3 <span class="token operator">=</span> str<span class="token punctuation">.</span><span class="token function">subString</span><span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">)</span><span class="token punctuation">;</span>  <span class="token comment">// "na"</span>
</code></pre>
<p>La version à un seul paramètre commence à l’index fourni et va jusqu’à la fin de la string. La version à deux paramètres commence à l’index donné en premier paramètre et s’arrête juste avant l’index donné en deuxième.</p>
<p>Vous pouvez également écrire des méthodes surchargées. Il suffit juste d’écrire chaque méthode séparément, avec le même nom. Il faut bien sûr s’assurer que les paramètres sont différents en nombre et/ou en types, sinon le compilateur sera incapable de savoir laquelle choisir lors d’une invocation. Ne définissez des méthodes surchargées que lorsque la sémantique des méthodes est identique, sinon cela rendra votre code plus obscur.</p>

