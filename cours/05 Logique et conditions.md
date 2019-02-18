---


---

<h1 id="chapitre-5">Chapitre 5</h1>
<h1 id="logique-et-conditions">Logique et conditions</h1>
<p>Les programmes doivent être capables de réagir différemment en fonction des entrées qu’ils reçoivent. Ce n’était pas le cas jusqu’à présent. Ce chapitre introduit les fonctionnalités de Java concernant l’expression de la logique et la prise de décisions.</p>
<h2 id="opérateurs-relationnels">Opérateurs relationnels</h2>
<p>Java a six <strong>opérateurs relationnels</strong> (<em><strong>relational operators</strong></em>) qui testent la relation entre deux valeurs :</p>
<pre class=" language-java"><code class="prism  language-java">x <span class="token operator">==</span> y		<span class="token comment">// x égal à y ?</span>
x <span class="token operator">!=</span> y		<span class="token comment">// x non égal à y ?</span>
x <span class="token operator">&gt;</span> y
x <span class="token operator">&lt;</span> y
x <span class="token operator">&gt;=</span> y
x <span class="token operator">&lt;=</span> y
</code></pre>
<p>Le résultat donné par un opérateur relationnel est ce qu’on appelle un <strong>booléen</strong> (<em><strong>boolean</strong></em>), c’est-à-dire <strong>vrai</strong> ou <strong>faux</strong> (<em><strong>true</strong></em> / <em><strong>false</strong></em>). George Boole a développé une algèbre capable de représenter la logique.</p>
<blockquote>
<p>Une erreur TRÈS courante est d’utiliser l’opérateur d’affectation <code>=</code> au lieu de l’opérateur d’égalité (<code>==</code>) pour comparer deux valeurs. Autre erreur : <code>=&lt;</code> et <code>=&gt;</code> n’existent pas.</p>
</blockquote>
<p>Pour comparer deux valeurs, elles doivent être compatibles. Java applique les mêmes conversions que d’habitude lorsque cela est nécessaire :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token number">5</span> <span class="token operator">&lt;</span> <span class="token number">6</span>		<span class="token comment">// true</span>
<span class="token number">5</span> <span class="token operator">&lt;</span> <span class="token number">6.0</span>		<span class="token comment">// true (conversion implicite de 5-&gt;5.0)</span>
<span class="token number">5</span> <span class="token operator">&lt;</span> <span class="token string">"6"</span>		<span class="token comment">// erreur de compilation</span>
</code></pre>
<h2 id="les-instructions-conditionnelles">Les instructions conditionnelles</h2>
<p>Les <strong>instructions conditionnelles</strong> nous permettent de réagir différemment en fonction de conditions logiques. L’instruction <code>if</code> est la plus simple :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">if</span> <span class="token punctuation">(</span>x <span class="token operator">&gt;</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>x <span class="token operator">+</span> <span class="token string">" est positif"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>L’expression entre parenthèses <code>x &gt; 0</code> s’appelle une condition. Si le résultat de cette expression logique est <code>true</code>, alors le bloc de code entre accolades est exécuté. Si le résultat est <code>false</code>, ce bloc est esquivé. La condition peut être n’importe quelle <strong>expression booléenne</strong>.</p>
<p>Une deuxième forme d’instruction conditionnelle offre la possibilité d’exécuter des blocs différents en fonction du résultat. C’est le « si… alors… sinon… » (<code>if-else</code>). Les possibilités sont appelées des <strong>branches</strong>, la condition détermine quelle branche est exécutée :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">if</span> <span class="token punctuation">(</span>n <span class="token operator">%</span> <span class="token number">2</span> <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>n <span class="token operator">+</span> <span class="token string">" est pair"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
<span class="token keyword">else</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>n <span class="token operator">+</span> <span class="token string">" est impair"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>Il n’y a que deux résultats possibles pour une condition, donc <strong>une instruction <code>if-else</code> exécute toujours exactement une branche</strong>.</p>
<p>Les accolades sont optionnelles pour les branches qui n’ont qu’une seule instruction :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">if</span> <span class="token punctuation">(</span>n <span class="token operator">%</span> <span class="token number">2</span> <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">)</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>n <span class="token operator">+</span> <span class="token string">" est pair"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">else</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>n <span class="token operator">+</span> <span class="token string">" est impair"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p>Il est souvent préférable d’utiliser les accolades quand même, cela permet d’éviter une erreur fréquente quand on ajoute du code à une branche existante :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">if</span> <span class="token punctuation">(</span>x <span class="token operator">&gt;</span> <span class="token number">0</span><span class="token punctuation">)</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>x <span class="token operator">+</span> <span class="token string">" est positif"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>x <span class="token operator">+</span> <span class="token string">" et non-nul"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p>La deuxième instruction <code>println</code> a été ajoutée à la branche. Ou du moins c’est ce que voudrait le codeur. Car seule la première instruction <code>println</code> fait partie de la branche du <code>if</code>, puisqu’il n’y a pas d’accolades. L’autre <code>println</code> (la suite de l’instruction <code>if</code>) sera exécuté dans tous les cas, que <code>x</code> soit positif ou pas. C’est la cause d’un célèbre bug dans le système d’exploitation iOS d’Apple en 2014, causant une faille de sécurité qui permettait à un hacker de lancer des attaques de type <em>Man in the Middle</em> :</p>
<pre class=" language-c"><code class="prism  language-c"><span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">.</span>
<span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token punctuation">(</span>err <span class="token operator">=</span> SSLHashSHA1<span class="token punctuation">.</span><span class="token function">update</span><span class="token punctuation">(</span><span class="token operator">&amp;</span>hashCtx<span class="token punctuation">,</span> <span class="token operator">&amp;</span>clientRandom<span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token operator">!=</span> <span class="token number">0</span><span class="token punctuation">)</span>
  <span class="token keyword">goto</span> fail<span class="token punctuation">;</span>
<span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token punctuation">(</span>err <span class="token operator">=</span> SSLHashSHA1<span class="token punctuation">.</span><span class="token function">update</span><span class="token punctuation">(</span><span class="token operator">&amp;</span>hashCtx<span class="token punctuation">,</span> <span class="token operator">&amp;</span>serverRandom<span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token operator">!=</span> <span class="token number">0</span><span class="token punctuation">)</span>
  <span class="token keyword">goto</span> fail<span class="token punctuation">;</span>
<span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token punctuation">(</span>err <span class="token operator">=</span> SSLHashSHA1<span class="token punctuation">.</span><span class="token function">update</span><span class="token punctuation">(</span><span class="token operator">&amp;</span>hashCtx<span class="token punctuation">,</span> <span class="token operator">&amp;</span>signedParams<span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token operator">!=</span> <span class="token number">0</span><span class="token punctuation">)</span>
  <span class="token keyword">goto</span> fail<span class="token punctuation">;</span>
  <span class="token keyword">goto</span> fail<span class="token punctuation">;</span>   <span class="token comment">// comment perdre son job chez Apple</span>
<span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token punctuation">(</span>err <span class="token operator">=</span> SSLHashSHA1<span class="token punctuation">.</span><span class="token function">final</span><span class="token punctuation">(</span><span class="token operator">&amp;</span>hashCtx<span class="token punctuation">,</span> <span class="token operator">&amp;</span>hashOut<span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token operator">!=</span> <span class="token number">0</span><span class="token punctuation">)</span>
  <span class="token keyword">goto</span> fail<span class="token punctuation">;</span>

err <span class="token operator">=</span> <span class="token function">sslRawVerify</span><span class="token punctuation">(</span><span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">.</span>
</code></pre>
<p>Notez qu’aucun <code>;</code> n’est placé sur les lignes <code>if/else</code> (comme lorsqu’on définit une méthode ou une classe).  C’est souvent source d’une autre erreur très sournoise car non signalée par le compilateur :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span> n <span class="token operator">=</span> <span class="token number">1</span><span class="token punctuation">;</span>
<span class="token keyword">if</span> <span class="token punctuation">(</span>n <span class="token operator">%</span> <span class="token number">2</span> <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">;</span>   <span class="token comment">// instruction vide !!!</span>
<span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>n <span class="token operator">+</span> <span class="token string">" est pair"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>Le compilateur laissera passer, car c’est légal : si la condition est vraie, la branche du <code>if</code> est exécutée, mais cette branche n’est pas ce qui est entre accolades. C’est l’instruction vide terminée par le fameux point-virgule. Et donc, le bloc suivant est toujours exécuté.</p>
<h2 id="chaînage-et-imbrication-dinstructions-conditionnelles">Chaînage et imbrication d’instructions conditionnelles</h2>
<p>Parfois vous avez besoin de vérifier plusieurs conditions en relation et choisir une action possible. Le <strong>chaînage</strong> d’instructions <code>if-else</code> est une solution :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">if</span> <span class="token punctuation">(</span>x <span class="token operator">&gt;</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"x est positif"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span> <span class="token keyword">else</span> <span class="token keyword">if</span> <span class="token punctuation">(</span>x <span class="token operator">&lt;</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"x est négatif"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span> <span class="token keyword">else</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"x est nul"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>Ces chaînes peuvent être aussi longues que souhaitées (attention à la lisibilité néanmoins). Notez que la dernière branche est un simple <code>else</code> (et non un <code>else if</code>). Si on arrive à ce point, on sait déjà que <code>x</code> ne peut être que nul.</p>
<p>Sur ce type de chaînage (terminant par un simple <code>else</code>), il y a toujours exactement une branche exécutée (comme pour un <code>if-else</code> classique). Parfois vous aurez besoin de terminer par un <code>else if</code>, ce qui est tout à fait légal ; n’oubliez pas néanmoins que, dans ce type de chaînage, il n’est pas garanti qu’une des branches sera exécutée (toutes les conditions pourraient être fausses, et il n’y a pas de <code>else</code> final pour faire office de branche « par défaut »).</p>
<p>Vous pouvez également <strong>imbriquer</strong> des instructions conditionnelles (<em><strong>nesting</strong></em>) :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">if</span> <span class="token punctuation">(</span>x <span class="token operator">&gt;</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"x est positif"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span> <span class="token keyword">else</span> <span class="token punctuation">{</span>
  <span class="token keyword">if</span> <span class="token punctuation">(</span>x <span class="token operator">&lt;</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"x est négatif"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span> <span class="token keyword">else</span> <span class="token punctuation">{</span>
    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"x is zero"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<p>C’est courant mais attention : trop de <em>nesting</em> rend vite le code difficile à suivre, même avec une bonne indentation.</p>
<h2 id="opérateurs-logiques">Opérateurs logiques</h2>
<p>En plus des opérateurs relationnels, Java a trois <strong>opérateurs logiques</strong> (<em><strong>logical operators</strong></em>) : <code>&amp;&amp;, ||</code> et <code>!</code>, qui signifient respectivement <em>et</em>, <em>ou</em> et <em>non</em>. Quelques exemples d’expression logiques utilisant ces opérateurs :</p>
<ul>
<li>L’expression <code>x &gt; 0 &amp;&amp; x &lt;= 10</code> est vraie lorsque <code>x</code> est dans l’intervalle <code>]0 ; 10]</code></li>
<li>L’expression <code>porteFermee || n % 3 == 0</code> est vraie si l’une des deux conditions est vraie, donc si <code>porteFermee</code> (un booléen) est vrai <em>ou</em> si le nombre <code>n</code> est divisible par <code>3</code>.</li>
<li><code>!porteFermee</code> utilise l’opérateur <code>!</code> (<code>non</code>), qui inverse le résultat de l’expression booléenne. Donc <code>!porteFermee</code> est vrai si <code>porteFermee</code> est faux.</li>
</ul>
<p>Récapitulons : pour qu’une expression en <code>&amp;&amp;</code> soit vraie, il faut que les valeurs des deux côtés de l’opérateur soient vraies. Et pour qu’une expression en <code>||</code> soit fausse, il faut que les deux valeurs soient fausses. Voici un tableau récapitulant toutes les valeurs possibles en fonction des valeurs booléennes des expressions <code>A</code> et <code>B</code> :</p>

<table>
<thead>
<tr>
<th align="center"><code>A</code></th>
<th align="center"><code>B</code></th>
<th align="center"><code>A &amp;&amp; B</code></th>
<th align="center"><code>A || B</code></th>
<th align="center"><code>!A</code></th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">F</td>
<td align="center">F</td>
<td align="center">F</td>
<td align="center">F</td>
<td align="center">T</td>
</tr>
<tr>
<td align="center">F</td>
<td align="center">T</td>
<td align="center">F</td>
<td align="center">T</td>
<td align="center">T</td>
</tr>
<tr>
<td align="center">T</td>
<td align="center">F</td>
<td align="center">F</td>
<td align="center">T</td>
<td align="center">F</td>
</tr>
<tr>
<td align="center">T</td>
<td align="center">T</td>
<td align="center">T</td>
<td align="center">T</td>
<td align="center">F</td>
</tr>
</tbody>
</table><p>Les opérateurs logiques ne sont jamais indispensables : on peut s’en sortir uniquement avec des chaînages et des imbrications. Cependant, elles sont énormément utilisées car elles allègent et simplifient le code grandement.</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">if</span> <span class="token punctuation">(</span>x <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">if</span> <span class="token punctuation">(</span>y <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"x et y sont nuls"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span>

<span class="token comment">// Équivalent avec un "et"</span>
<span class="token keyword">if</span> <span class="token punctuation">(</span>x <span class="token operator">==</span> <span class="token number">0</span> <span class="token operator">&amp;&amp;</span> y <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"x et y sont nuls"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>

<span class="token keyword">if</span> <span class="token punctuation">(</span>x <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"Au moins un des deux (x ou y) est nul"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span> <span class="token keyword">else</span> <span class="token keyword">if</span> <span class="token punctuation">(</span>y <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"Au moins un des deux (x ou y) est nul"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>

<span class="token comment">// Équivalent avec un "ou"</span>
<span class="token keyword">if</span> <span class="token punctuation">(</span>x <span class="token operator">==</span> <span class="token number">0</span> <span class="token operator">||</span> y <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"Au moins un des deux (x ou y) est nul"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p>Les opérateurs logiques <strong>n’évaluent la seconde expression que si nécessaire</strong> :</p>
<ul>
<li><code>true || nImporteQuoi</code> est <strong>toujours vrai</strong>, donc il est inutile d’évaluer <code>nImporteQuoi</code></li>
<li><code>false &amp;&amp; nImporteQuoi</code> est <strong>toujours faux</strong></li>
</ul>
<p>Cela s’appelle un <strong>court-circuit</strong> (<em><strong>short circuit</strong></em>), et peut-être intéressant par exemple lorsque la deuxième expression booléenne est potentiellement longue à évaluer.</p>
<p>Parfois on a besoin de « négationner » un mix d’expressions logiques. Ces deux règles sont à savoir pour simplifier ce type d’expressions :</p>
<ul>
<li><code>!(A &amp;&amp; B)</code> est équivalent à <code>!A || !B</code></li>
<li><code>!(A || B)</code> est équivalent à <code>!A &amp;&amp; !B</code></li>
</ul>
<p>La négation sur une expression logique s’applique aussi aux opérateur relationnels. Ainsi :</p>
<ul>
<li><code>!(x &lt; 5 &amp;&amp; y == 3)</code> donne <code>x &gt;= 5 || y != 3</code></li>
<li><code>!(x &gt;= 1 || y != 7)</code> donne <code>x &lt; 1 &amp;&amp; y == 7</code></li>
</ul>
<pre class=" language-java"><code class="prism  language-java"><span class="token comment">// "Difficile" à lire</span>
<span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token operator">!</span><span class="token punctuation">(</span>x <span class="token operator">==</span> <span class="token number">0</span> <span class="token operator">||</span> y <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"Ni x ni y n'est nul"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>

<span class="token comment">// Plus facile pour le cerveau (chez les gens normaux)</span>
<span class="token keyword">if</span> <span class="token punctuation">(</span>x <span class="token operator">!=</span> <span class="token number">0</span> <span class="token operator">&amp;&amp;</span> y <span class="token operator">!=</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"Ni x ni y n'est nul"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<h2 id="variables-booléennes">Variables booléennes</h2>
<p>Pour stocker une valeur <code>true/false</code>, on utilise une <strong>variable booléenne</strong> (rappelons que le type <code>boolean</code> est l’un des huit types primitifs de Java).</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">boolean</span> flag<span class="token punctuation">;</span>
flag <span class="token operator">=</span> <span class="token boolean">true</span><span class="token punctuation">;</span>
<span class="token keyword">boolean</span> testRes <span class="token operator">=</span> <span class="token boolean">false</span><span class="token punctuation">;</span>
<span class="token keyword">boolean</span> n1EstPair <span class="token operator">=</span> <span class="token punctuation">(</span>n1 <span class="token operator">%</span> <span class="token number">2</span> <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">boolean</span> xEstPositif <span class="token operator">=</span> <span class="token punctuation">(</span>x <span class="token operator">&gt;</span> <span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p>On appelle souvent ce type de variable un <em>flag</em> (drapeau) parce qu’elle signale la présence ou l’absence d’une condition (drapeau levé ou baissé). Ces <em>flags</em> peuvent ensuite être utilisés dans d’autres expressions booléennes :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">if</span> <span class="token punctuation">(</span>n1EstPair<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"n1 était pair quand j'ai vérifié."</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<blockquote>
<p>Il est important de comprendre que l’expression <code>(n1 % 2 == 0)</code> ne sera pas réévaluée au moment où le <code>if</code> va tester <code>n1EstPair</code>. Si la valeur de <code>n1</code> a entre temps changé de <code>2</code> vers <code>3</code>, <code>n1EstPair</code> restera vraie.</p>
</blockquote>
<p>Les <em>flags</em> peuvent permettre de simplifier des expressions booléennes complexes en les nommant (comme les méthodes simplifient le code en nommant des blocs de code). Chaque partie d’une condition complexe sera ainsi souvent stockée au préalable dans un <em>flag</em>.</p>
<p>Notez que l’on n’a pas à écrire <code>if (flag == true)</code>. Comme le <em>flag</em> est déjà un booléen, c’est aussi déjà une condition en lui-même. De même, pour tester si un <em>flag</em> est faux, on n’écrit pas en général <code>if (flag == false)</code> mais plutôt <code>if (!flag)</code>.</p>
<h2 id="méthodes-booléennes">Méthodes booléennes</h2>
<p>On utilise souvent des méthodes qui retournent un booléen, des « méthodes-test » :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">boolean</span> <span class="token function">estPair</span><span class="token punctuation">(</span><span class="token keyword">int</span> n<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">return</span> <span class="token punctuation">(</span>n <span class="token operator">%</span> <span class="token number">2</span> <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>

<span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">.</span>
<span class="token comment">// Dans une autre méthode</span>
<span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token function">estPair</span><span class="token punctuation">(</span>nombreEntier<span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">.</span>
<span class="token punctuation">}</span>
</code></pre>
<p>On donne à ces méthodes des noms qui sonnent comme des questions directes « oui/non ».</p>
<h2 id="validation-dentrées">Validation d’entrées</h2>
<p>Une tâche très importante d’un programme (mais régulièrement ignorée ou bâclée) est la <strong>validation des entrées utilisateur</strong> :</p>
<ul>
<li>Les utilisateurs font souvent des erreurs en tapant des choses incorrectes (ex : des lettres à la place de chiffres), parfois en toute bonne foi, parce qu’ils n’ont pas bien compris ce qui leur était demandé.</li>
<li>Pire encore, un hacker peut tenter de planter votre système en entrant volontairement des données incorrectes. Il peut aussi tenter de faire parler votre BDD ou de se connecter sans mot de passe (injection SQL).</li>
</ul>
<p>Vous ne devez jamais faire comme si tout allait se passer comme sur des rails. Toute entrée est potentiellement corrompue.</p>
<pre class=" language-java"><code class="prism  language-java">Scanner in <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Scanner</span><span class="token punctuation">(</span>System<span class="token punctuation">.</span>in<span class="token punctuation">)</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span><span class="token string">"Entrez un nombre : "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">double</span> x <span class="token operator">=</span> in<span class="token punctuation">.</span><span class="token function">nextDouble</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">double</span> y <span class="token operator">=</span> Math<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span>x<span class="token punctuation">)</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"Le logarithme est : "</span> <span class="token operator">+</span> y<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span> Entrez un nombre <span class="token operator">:</span> <span class="token operator">-</span><span class="token number">1</span>
<span class="token operator">&gt;</span> Le logarithme est <span class="token operator">:</span> Nan
</code></pre>
<p>Le logarithme népérien n’est pas défini quand <code>x</code> est négatif. <code>Math.log(-1)</code> ne provoquera pas d’erreur d’exécution mais retournera <code>NaN</code> (<em>Not a Number</em>), une valeur spéciale. Un affichage qui paraîtra bizarre aux yeux de l’utilisateur. Rendons-lui la chose plus compréhensible :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">if</span> <span class="token punctuation">(</span>x <span class="token operator">&gt;=</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">double</span> y <span class="token operator">=</span> Math<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span>x<span class="token punctuation">)</span><span class="token punctuation">;</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"Le logarithme est : "</span> <span class="token operator">+</span> y<span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span> <span class="token keyword">else</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"Le logarithme d'un nombre négatif n'est pas défini"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>C’est mieux, mais toujours potentiellement problématique. Et si l’utilisateur ne rentrait pas un nombre du tout ?</p>
<pre><code>&gt; Entrez un nombre : cinq
Exception in thread "main" java.util.InputMismatchException
        at java.base/java.util.Scanner.throwFor(Scanner.java:939)
        at java.base/java.util.Scanner.next(Scanner.java:1594)
        at java.base/java.util.Scanner.nextDouble(Scanner.java:2564)
        at simplecalendar.App.main(App.java:17)
</code></pre>
<p>Exception de type <code>Input Mismatch</code> : la valeur entrée (<code>String</code>) ne correspond pas au type attendu (<code>double</code>). Il faut tester l’entrée avant de la consommer (notez le subtil jeu de mots).</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token operator">!</span>in<span class="token punctuation">.</span><span class="token function">hasNextDouble</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  String entree <span class="token operator">=</span> in<span class="token punctuation">.</span><span class="token function">next</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  System<span class="token punctuation">.</span>err<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>entree <span class="token operator">+</span> <span class="token string">" n'est pas un nombre."</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token keyword">return</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>La méthode <code>Scanner.hasNextDouble()</code> teste si la prochaine entrée du flux peut être interprétée comme un <code>double</code>. La méthode <code>next()</code> retourne le prochain <em>token</em> du flux en tant que <code>String</code>. Le canal <code>System.err</code> (par défaut l’écran) est utilisé pour sortir un message d’erreur et la méthode retourne.</p>
<blockquote>
<p>On a ici une instruction <code>return</code> sans valeur de retour. Elle peut être utilisée à n’importe quel moment pour terminer une méthode. Elle ne peut être utilisée ainsi que dans une méthode dont le type de retour est <code>void</code>. Les autres méthodes sont obligées de retourner une valeur.</p>
</blockquote>
<h2 id="petit-programme-récapitulatif">Petit programme récapitulatif</h2>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">import</span> java<span class="token punctuation">.</span>util<span class="token punctuation">.</span>Scanner<span class="token punctuation">;</span>

<span class="token comment">/**
* Illustre la validation d'entrées avec instructions conditionnelles.
*/</span>
<span class="token keyword">public</span> <span class="token keyword">class</span> <span class="token class-name">Logarithme</span> <span class="token punctuation">{</span>
  <span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">void</span> <span class="token function">main</span><span class="token punctuation">(</span>String<span class="token punctuation">[</span><span class="token punctuation">]</span> args<span class="token punctuation">)</span> <span class="token punctuation">{</span>
    Scanner in <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Scanner</span><span class="token punctuation">(</span>System<span class="token punctuation">.</span>in<span class="token punctuation">)</span><span class="token punctuation">;</span>
    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span><span class="token string">"Entrez un nombre : "</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    
    <span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token operator">!</span>in<span class="token punctuation">.</span><span class="token function">hasNextDouble</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
      String word <span class="token operator">=</span> in<span class="token punctuation">.</span><span class="token function">next</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
      System<span class="token punctuation">.</span>err<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>word <span class="token operator">+</span> <span class="token string">" n'est pas un nombre"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
      <span class="token keyword">return</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span>
    
    <span class="token keyword">double</span> x <span class="token operator">=</span> in<span class="token punctuation">.</span><span class="token function">nextDouble</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token keyword">if</span> <span class="token punctuation">(</span>x <span class="token operator">&gt;=</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
      <span class="token keyword">double</span> y <span class="token operator">=</span> Math<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span>x<span class="token punctuation">)</span><span class="token punctuation">;</span>
      System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"Le logarithme est : "</span> <span class="token operator">+</span> y<span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span> <span class="token keyword">else</span> <span class="token punctuation">{</span>
      System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"Le logarithme d'un nombre négatif n'est pas défini."</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<p>30 lignes de code au lieu de 5, juste pour vérifier les entrées… Rendre les programmes robustes et sécurisés requiert un grand nombre de vérifications additionnelles.</p>

