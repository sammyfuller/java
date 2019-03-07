---


---

<h1 id="chapitre-7">Chapitre 7</h1>
<h1 id="tableaux-et-références">Tableaux et références</h1>
<p>Jusqu’à présent, les seules variables que nous utilisons contenaient des valeurs uniques, comme un nombre ou une string, voire un objet (par exemple la variable <code>in</code> quand on écrit <code>Scanner in = new Scanner(...);</code>. Nous allons apprendre comment stocker des valeurs multiples du même type dans une variable unique : un tableau. C’est grâce à cela que vous pourrez manipuler de grandes quantités de données.</p>
<h2 id="créer-des-tableaux-arrays">Créer des tableaux (<em>arrays</em>)</h2>
<p>Un <strong>tableau</strong> (<em><strong>array</strong></em>) est une séquence de valeurs. Les valeurs d’un tableau sont appelées <strong>éléments</strong>. Vous pouvez créer un tableau de n’importe quel type primitif (<code>int, double</code>…) ou de n’importe quelle classe (<code>String</code> par exemple), mais <strong>tous les éléments du tableau doivent avoir le même type</strong>.</p>
<p>Pour créer un tableau, vous devez d’abord déclarer une variable du type de tableau souhaité. La syntaxe ressemble à ce que vous connaissez, on ajoute juste des crochets <code>[]</code> au type souhaité des éléments du tableau :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span><span class="token punctuation">[</span><span class="token punctuation">]</span> compteurs<span class="token punctuation">;</span>
<span class="token keyword">double</span><span class="token punctuation">[</span><span class="token punctuation">]</span> valeurs<span class="token punctuation">;</span>
</code></pre>
<p>Vous le savez, ceci ne fait que <em>déclarer</em> la variable. Pour l’utiliser, il faut l’<em>initialiser</em>. Les tableaux sont des objets, on doit les <em>instancier</em>, exactement comme on le ferait pour un type <code>Scanner</code> ou <code>Random</code>, avec le mot clé <code>new</code>. <code>new</code> <strong>alloue</strong> la mémoire nécessaire pour stocker les éléments du tableau. À l’allocation, tous <strong>les éléments sont initialisés à zéro</strong> (ou à <strong><code>null</code> si ce sont des objets</strong>).</p>
<pre class=" language-java"><code class="prism  language-java">compteurs <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">int</span><span class="token punctuation">[</span><span class="token number">4</span><span class="token punctuation">]</span><span class="token punctuation">;</span>
valeurs <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">double</span><span class="token punctuation">[</span>taille<span class="token punctuation">]</span><span class="token punctuation">;</span>
</code></pre>
<p><code>compteurs</code> se réfère alors à un tableau de 4 entiers. Le nombre d’éléments est nécessaire pour que le <em>runtime</em> sache combien d’espace mémoire il doit allouer. Ce nombre doit être d’un type entier, et positif.</p>
<p><code>valeurs</code> se réfère à un tableau de <code>double</code>. Cette fois, le nombre d’éléments est transmis dynamiquement (inconnu à la compilation) : ce sera la valeur de la variable <code>taille</code> au moment de l’allocation.</p>
<p>Bien sûr, vous pouvez déclarer et initialiser des tableaux en une fois :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span> <span class="token punctuation">[</span><span class="token punctuation">]</span> compteurs <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">int</span> <span class="token punctuation">[</span><span class="token number">4</span><span class="token punctuation">]</span><span class="token punctuation">;</span>
<span class="token keyword">double</span><span class="token punctuation">[</span><span class="token punctuation">]</span> valeurs <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">double</span><span class="token punctuation">[</span>taille<span class="token punctuation">]</span><span class="token punctuation">;</span>
</code></pre>
<p>Une syntaxe spéciale permet également d’allouer le tableau et d’initialiser ses valeurs en même temps :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span> <span class="token punctuation">[</span><span class="token punctuation">]</span> compteurs <span class="token operator">=</span> <span class="token punctuation">{</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">8</span> <span class="token punctuation">}</span><span class="token punctuation">;</span>
</code></pre>
<h2 id="accéder-aux-éléments">Accéder aux éléments</h2>
<p>En mémoire, la variable <code>compteurs</code> elle-même <strong>ne représente qu’une référence</strong> au tableau.</p>
<p><img src="https://lh3.googleusercontent.com/Kj8NO9uVYfD_-KJgLSOHV4gfZHg2dPkGWJztAbwyfH_mM9ZTJRg_37x4OBGfx4mJM04-ULBZ56kR" alt="enter image description here"><br>
Vous devez penser au tableau et à la variable qui s’y réfère comme à deux différentes entités. Comme on le verra, on peut affecter une variable différente au même tableau, tout comme on peut changer la valeur de <code>compteurs</code> pour qu’elle se réfère à un tout autre tableau.</p>
<p>Les nombres dans les cases sont les éléments du tableau, ce qu’il contient. Les nombres en dessous sont les <strong>indices</strong> (<em><strong>indexes</strong></em>) utilisés pour identifier chaque élément dans le tableau. Comme pour les strings, l’index du premier élément est 0, pas 1.</p>
<p>L’opérateur <code>[]</code> permet de sélectionner un élément. Il peut être utilisé dans n’importe quel expression :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span><span class="token punctuation">[</span><span class="token punctuation">]</span> compteurs <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">int</span><span class="token punctuation">[</span><span class="token number">4</span><span class="token punctuation">]</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"Premier élément : "</span> <span class="token operator">+</span> compteurs<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">]</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
compteurs<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">]</span> <span class="token operator">=</span> <span class="token number">7</span><span class="token punctuation">;</span>
compteurs<span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">]</span> <span class="token operator">=</span> compteurs<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">]</span> <span class="token operator">*</span> <span class="token number">2</span><span class="token punctuation">;</span>
compteurs<span class="token punctuation">[</span><span class="token number">2</span><span class="token punctuation">]</span><span class="token operator">++</span><span class="token punctuation">;</span>
compteurs<span class="token punctuation">[</span><span class="token number">3</span><span class="token punctuation">]</span> <span class="token operator">-=</span> <span class="token number">60</span><span class="token punctuation">;</span>
compteurs<span class="token punctuation">[</span><span class="token number">4</span><span class="token punctuation">]</span> <span class="token operator">=</span> <span class="token number">2</span><span class="token punctuation">;</span>  <span class="token comment">// Erreur fréquente : ArrayIndexOutOfBoundsException</span>
</code></pre>
<p>Comme on peut s’y attendre, l’index lui-même peut être n’importe quelle expression, du moment qu’elle s’évalue à un <code>int</code>. Pour parcourir un tableau, il est très fréquent d’utiliser une variable de <em>loop</em> :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">4</span><span class="token punctuation">;</span>
<span class="token keyword">while</span> <span class="token punctuation">(</span>i <span class="token operator">&lt;</span> <span class="token number">4</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  compteurs<span class="token punctuation">[</span>i<span class="token punctuation">]</span> <span class="token operator">+=</span> <span class="token number">10</span><span class="token punctuation">;</span>
  i<span class="token operator">++</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>Ici, <code>i</code> est un diminutif pour <code>index</code>. Les noms de variables à une lettre sont rarement une bonne idée (lisibilité douteuse), mais les variables de <em>loop</em> d’indexage sont tellement fréquentes que tous les programmeurs du monde comprennent immédiatement à quoi <code>i</code> se réfère. De même, il est d’usage d’utiliser les index <code>j</code> et <code>k</code> lorsque l’on doit imbriquer l’indexage sur deux ou trois boucles (souvent pour parcourir des tableaux à deux ou trois dimensions).</p>
<p>Notez qu’ici, c’est un cas typique où le <code>while</code> sera avantageusement remplacé par un <code>for</code> (on connaît à l’avance le nombre d’itérations) :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> <span class="token number">4</span><span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  compteurs<span class="token punctuation">[</span>i<span class="token punctuation">]</span> <span class="token operator">+=</span> <span class="token number">10</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<h2 id="affichage">Affichage</h2>
<p>Si vous essayez d’afficher les valeurs d’un tableau avec une simple instruction <code>print</code> sur la variable, cela ne fonctionnera pas :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span><span class="token punctuation">[</span><span class="token punctuation">]</span> arr <span class="token operator">=</span> <span class="token punctuation">{</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">8</span> <span class="token punctuation">}</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span><span class="token string">"Sortie : "</span> <span class="token operator">+</span> arr<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span> Sortie <span class="token operator">:</span> <span class="token punctuation">[</span>I<span class="token annotation punctuation">@bf7e8e0</span>
</code></pre>
<p><code>print</code> affiche la valeur de la variable <code>arr</code> (formatée comme toute variable d’un type objet) : le <code>[</code> indique que c’est un tableau, le <code>I</code> indique le type <code>int</code> des éléments, et la partie après le <code>@</code> indique l’adresse du tableau en mémoire.</p>
<p>Si on veut effectivement afficher les valeurs du tableau, on peut le faire soi-même :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">void</span> <span class="token function">afficherTableau</span><span class="token punctuation">(</span><span class="token keyword">int</span><span class="token punctuation">[</span><span class="token punctuation">]</span> arr<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> arr<span class="token punctuation">.</span>length<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">printf</span><span class="token punctuation">(</span><span class="token string">"%3d"</span><span class="token punctuation">,</span> arr<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>

<span class="token operator">&gt;</span>   <span class="token number">2</span>  <span class="token number">4</span>  <span class="token number">6</span>  <span class="token number">8</span>
</code></pre>
<p>Tous les tableaux possèdent une constante initialisée lors de leur création : <code>length</code> (longueur), qui stocke le nombre d’éléments. Il est préférable de l’utiliser même quand on connaît la taille du tableau (évitez les <em>magic numbers</em>). Notez qu’il faut donc s’arrêter <em>avant</em> l’index <code>arr.length</code>.</p>
<p>La bibliothèque de classes de Java possède une classe utilitaire <code>java.util.Arrays</code> qui fournit des méthodes pour travailler avec des tableaux. La méthode <code>toString()</code> retourne une représentation du tableau sous forme de string :</p>
<pre class=" language-java"><code class="prism  language-java">System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>Arrays<span class="token punctuation">.</span><span class="token function">toString</span><span class="token punctuation">(</span>arr<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span> <span class="token punctuation">[</span><span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">6</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">]</span>
</code></pre>
<h2 id="copier-un-tableau">Copier un tableau</h2>
<p>Rappel : une variables de type tableau est une <em>référence</em> à un tableau. Quand on lui affecte un tableau (fraîchement créé ou non), elle <strong>copie simplement la référence</strong>, mais <strong>pas le tableau lui-même</strong>.</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">double</span><span class="token punctuation">[</span><span class="token punctuation">]</span> a <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">double</span><span class="token punctuation">[</span><span class="token number">3</span><span class="token punctuation">]</span><span class="token punctuation">;</span>
<span class="token keyword">double</span><span class="token punctuation">[</span><span class="token punctuation">]</span> b <span class="token operator">=</span> a<span class="token punctuation">;</span>
</code></pre>
<p><img src="https://lh3.googleusercontent.com/vfvuFHqcyK2RtgfswWJ_JLLbPusRXnS-W5QEmadRl2RDhIrldtq4OqePyBQVKvXf7fU-j4ocdiNH" alt="enter image description here"><br>
Les deux variables se réfèrent au même tableau. Tout changement fait au tableau par l’intermédiaire de l’une des deux variables sera « vu » par l’autre :</p>
<pre class=" language-java"><code class="prism  language-java">a<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">]</span> <span class="token operator">=</span> <span class="token number">12.3</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">print</span><span class="token punctuation">(</span>b<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">]</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span> <span class="token number">12.3</span>
</code></pre>
<p>Si vous voulez effectivement créer une <em>copie</em> du tableau, il faut allouer un nouveau tableau et copier les éléments un par un :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">double</span><span class="token punctuation">[</span><span class="token punctuation">]</span> c <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">double</span><span class="token punctuation">[</span>a<span class="token punctuation">.</span>length<span class="token punctuation">]</span><span class="token punctuation">;</span>
<span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> a<span class="token punctuation">.</span>length<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  c<span class="token punctuation">[</span>i<span class="token punctuation">]</span> <span class="token operator">=</span> a<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>De nouveau, <code>java.util.Arrays</code> possède une méthode qui exécute cette opération commune :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">double</span><span class="token punctuation">[</span><span class="token punctuation">]</span> c <span class="token operator">=</span> Arrays<span class="token punctuation">.</span><span class="token function">copyOf</span><span class="token punctuation">(</span>a<span class="token punctuation">,</span> a<span class="token punctuation">.</span>length<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p>Le second paramètre est le nombre d’éléments que vous voulez copier, donc <code>copyOf</code> peut aussi être utilisé pour copier une portion d’un tableau.</p>
<h2 id="parcourir-un-tableau">Parcourir un tableau</h2>
<p>Une opération extrêmement fréquente est le <strong>parcours</strong> s’un tableau à l’aide d’une boucle dont chaque itération va effectuer une action sur l’élément courant.</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">int</span><span class="token punctuation">[</span><span class="token punctuation">]</span> arr <span class="token operator">=</span> <span class="token punctuation">{</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">4</span> <span class="token punctuation">}</span><span class="token punctuation">;</span>
<span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> arr<span class="token punctuation">.</span>length<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  arr<span class="token punctuation">[</span>i<span class="token punctuation">]</span> <span class="token operator">*=</span> arr<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>Arrays<span class="token punctuation">.</span><span class="token function">toString</span><span class="token punctuation">(</span>arr<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span> <span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">9</span><span class="token punctuation">,</span> <span class="token number">16</span><span class="token punctuation">]</span>
</code></pre>
<p>Un autre algorithme très courant est la <strong>recherche</strong> : on traverse un tableau en cherchant une (ou des) valeur(s) particulière(s).</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">int</span> <span class="token function">chercher</span><span class="token punctuation">(</span><span class="token keyword">double</span><span class="token punctuation">[</span><span class="token punctuation">]</span> arr<span class="token punctuation">,</span> <span class="token keyword">double</span> cible<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> arr<span class="token punctuation">.</span>length<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">if</span> <span class="token punctuation">(</span>arr<span class="token punctuation">[</span>i<span class="token punctuation">]</span> <span class="token operator">==</span> cible<span class="token punctuation">)</span> <span class="token punctuation">{</span>
      <span class="token keyword">return</span> i<span class="token punctuation">;</span>
    <span class="token punctuation">}</span>
  <span class="token punctuation">}</span>
  <span class="token keyword">return</span> <span class="token operator">-</span><span class="token number">1</span><span class="token punctuation">;</span>   <span class="token comment">// pas trouvé</span>
<span class="token punctuation">}</span>

<span class="token keyword">double</span><span class="token punctuation">[</span><span class="token punctuation">]</span> array <span class="token operator">=</span> <span class="token punctuation">{</span> <span class="token number">3.14</span><span class="token punctuation">,</span> <span class="token operator">-</span><span class="token number">34.0</span><span class="token punctuation">,</span> <span class="token number">1.234</span><span class="token punctuation">,</span> <span class="token operator">-</span><span class="token number">0.5</span> <span class="token punctuation">}</span><span class="token punctuation">;</span>
<span class="token keyword">int</span> index <span class="token operator">=</span> <span class="token function">chercher</span><span class="token punctuation">(</span>array<span class="token punctuation">,</span> <span class="token number">1.234</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"index : "</span> <span class="token operator">+</span> index<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token operator">&gt;</span> index <span class="token operator">:</span> <span class="token number">2</span>
</code></pre>
<p>On parcourt le tableau. Dès qu’on trouve la cible, on retourne immédiatement l’index, la méthode est terminée. Si on sort de la boucle, la valeur n’a pas été trouvée : on retourne <code>-1</code> au client (valeur spéciale choisie pour indiquer un échec ; voilà au passage typiquement le genre d’information que la documentation du code doit fournir).</p>
<p>Un autre parcours fréquent est appelé <strong>réduction</strong> : on « réduit » le tableau à une seule valeur. Par exemple, le calcul de la somme de tous les éléments est une réduction. Le produit, le minimum, la moyenne, etc. sont des réductions.</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">double</span> <span class="token function">calculerSomme</span><span class="token punctuation">(</span><span class="token keyword">double</span><span class="token punctuation">[</span><span class="token punctuation">]</span> arr<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">double</span> somme <span class="token operator">=</span> <span class="token number">0.0</span><span class="token punctuation">;</span>
  <span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> arr<span class="token punctuation">.</span>length<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    somme <span class="token operator">+=</span> arr<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
  <span class="token keyword">return</span> somme<span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>On retrouve ici un <em>pattern</em> fréquent pour l’écriture de méthodes retournant une valeur résultat :</p>
<ol>
<li>initialisation de la variable dont la valeur sera retournée ;</li>
<li>boucle ou autre traitement qui calcule / met à jour cette variable ;</li>
<li><code>return</code> de la valeur calculée.</li>
</ol>
<h2 id="for-amélioré-pour-tableaux"><code>for</code> amélioré pour tableaux</h2>
<p>Traverser un tableau est si fréquent que Jave fournit une syntaxe spéciale qui simplifie le code. Voici un algorithme de parcours classique et la version avec la <strong>boucle <code>for</code> améliorée</strong> (<em><strong>enhanced for loop</strong></em>), plus communément appelé <strong><code>foreach</code></strong> (« pour chaque ») :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> array<span class="token punctuation">.</span>length<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">int</span> elt <span class="token operator">=</span> array<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token punctuation">;</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>elt<span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>

<span class="token comment">// idem avec for amélioré</span>
<span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">int</span> elt <span class="token operator">:</span> array<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>elt<span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>On lit le code en disant « <em>pour chaque <code>elt</code> de <code>array</code>, faire…</em> » On n’est plus contraint d’accéder au tableau avec une variable index. En général, utilisez cette notation, sauf si vous avez réellement besoin de l’index courant dans votre algorithme (par exemple, dans une recherche, si vous devez retourner l’index).</p>

