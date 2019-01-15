---


---

<h1 id="chapitre-1">Chapitre 1</h1>
<h1 id="lart-de-la-programmation">L’Art de la programmation</h1>
<p>Le but de ce module est d’abord de vous apprendre à penser comme un programmeur. « L’art » du développement logiciel est jeune, très complexe et en constant et rapide mouvement. Il fait appel à des concepts mathématiques comme des <strong>langages formels</strong> (ex: Java) pour exprimer des idées, des calculs. C’est aussi une ingénierie : il faut <strong>concevoir et assembler</strong> des composants dans un système et <strong>évaluer</strong> les différentes alternatives. C’est enfin une science : on <strong>observe</strong> le comportement de systèmes complexes, on forme des hypothèses et on les teste.</p>
<p>Dans ce cours, vous apprendrez à programmer à l’aide du langage Java. Mais pour devenir un vrai développeur, la connaissance de langages de programmation n’est pas suffisante : vous devrez acquérir les bases d’une autre compétence importante : la <strong>résolution de problèmes</strong> de programmation.</p>
<h2 id="un-ordinateur-quest-ce-que-cest-">Un ordinateur, qu’est-ce que c’est ?</h2>
<p>Dans le sens général, un ordinateur est un appareil qui stocke et traite des données. Chaque ordinateur (de bureau, portable, tablette, smartphones…) a ses propres caractéristiques mais ils partagent tous des composants matériels essentiels. Les deux plus importants sont le <strong>processeur (CPU)</strong> capable d’exécuter des calculs simples et la <strong>mémoire (RAM)</strong> qui stocke temporairement des informations.</p>
<p>Les utilisateurs interagissent avec l’ordinateur grâce à souris, claviers et autres écrans tactiles mais c’est toujours côté processeur/mémoire que se fait le travail de calcul.</p>
<h2 id="programmer-quest-ce-que-cest-">Programmer, qu’est-ce que c’est ?</h2>
<p>Un <strong>programme</strong> est une <strong>séquence d’instructions</strong> qui spécifie comment exécuter un calcul donné (potentiellement très complexe) sur un ordinateur. Le calcul en question peut être d’ordre mathématique (la trajectoire de ce missile passe-t-elle par l’œil droit de cet ennemi ?), ou un traitement sur des données (recherche et remplacement de chaînes de caractères), ou bien encore une procédure de transformation d’un programme en langage machine (compilation).</p>
<p>Les détails diffèrent plus ou moins drastiquement dans différents langages, mais quelques constructions sont communes à tous :</p>
<ul>
<li><strong>entrée (input)</strong> : données reçues par l’intermédiaire du clavier, d’un fichier, d’un capteur, d’internet, etc.</li>
<li><strong>sortie (output)</strong> : afficher des données sur l’écran, les écrire dans un fichier, etc.</li>
<li><strong>calculs</strong> : exécuter des opérations mathématiques basiques (addition…)</li>
<li><strong>décisions</strong> : exécuter certaines parties de code différentes en fonction de certaines conditions évaluées</li>
<li><strong>répétitions</strong> : exécuter une action de manière répétée, avec en général des variations</li>
</ul>
<p>La programmation se résume peu ou prou à cela. Toutes les applications que vous utilisez, aussi complexes soient-elles, sont construites à partir d’assemblages de ces simples éléments. Vous pouvez donc considérer que <strong>la programmation est un processus de découpage de larges et complexes tâches en tâches de plus en plus petites</strong>. Le processus continue jusqu’à ce que les sous-tâches deviennent suffisamment simples pour être exécutées par les circuits électroniques de la machine. L’utilisation d’un langage de programmation évolué permet d’arrêter le découpage à un niveau bien plus élevé que si l’on avait à écrire le programme en langage machine.</p>
<h2 id="hello-java">Hello Java!</h2>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">class</span> <span class="token class-name">Hello</span>
<span class="token punctuation">{</span>
  <span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">void</span> <span class="token function">main</span><span class="token punctuation">(</span>String<span class="token punctuation">[</span><span class="token punctuation">]</span> args<span class="token punctuation">)</span>
  <span class="token punctuation">{</span>
    <span class="token comment">// Salutations</span>
    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"Hello Java!"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<p>Ce programme Java, une fois exécuté, affiche « <strong>Hello Java!</strong> » à l’écran.</p>
<p>Un programme Java est écrit en définissant des <strong>classes</strong> et des <strong>méthodes</strong>. Les méthodes sont formées par une suite d’<strong>instructions</strong>. Une instruction est une ligne de code qui exécute une action basique. Ici, c’est la ligne l’instruction <code>println</code>  qui produit la <strong>sortie</strong> observée.</p>
<p><code>System.out.println</code> affiche un texte à l’écran et passe à la ligne (<em>print line</em>). Il existe une autre méthode appelée <code>System.out.print</code> qui n’effectue pas le passage à la ligne. Comme la plupart des instructions, un appel de méthode se termine par un point-virgule.</p>
<p>Java est sensible à la casse (majuscules/minuscules) :</p>
<ul>
<li><code>System</code> : OK, reconnu</li>
<li><code>system</code> ou <code>SYSTEM</code> : ne fonctionneront pas (erreur de compilation)</li>
</ul>
<p>Une <strong>méthode</strong> est une <strong>séquence d’instructions</strong> à laquelle on donne un nom (pour pouvoir indiquer clairement son objet et pour facilement la réutiliser autant de fois qu’on le souhaite). Notre programme définit une seule méthode : <code>main</code>. Cette méthode est spéciale : quand le programme se lance, c’est elle qui va être automatiquement recherchée et exécutée. La méthode démarre avec la première instruction et elle se termine (et donc ici le programme aussi) après l’exécution de la dernière instruction. Nous verrons comment définir des programmes qui possèdent plus d’une méthode.</p>
<p>Une <strong>classe</strong> peut être vue comme une <strong>collection de méthodes</strong>. Notre programme définit une classe appelée <code>Hello</code>. En Java, le nom d’une classe doit coïncider avec le nom du fichier, donc ici cette classe devra être définie dans un fichier qu’on appellera <code>Hello.java</code>.</p>
<p>Java utilise des accolades (<code>{</code> et <code>}</code>) pour grouper les choses. Dans notre programme, on peut aisément localiser la définition de la classe (accolades extérieures) et celle de la méthode <code>main</code> (accolades intérieures).</p>
<p>La ligne commençant par <code>//</code> est un <strong>commentaire</strong> (jusqu’en fin de ligne). Les commentaires sont destinés aux développeurs qui lisent votre code (et à vous-même), pour expliquer quelque chose de peu évident sur le code. N’utilisez des commentaires que lorsque cela semble vraiment essentiel à la compréhension du code. Un commentaire explicite du code doit être vu comme un “échec” : le code que vous avez écrit n’est pas assez expressif pour se faire comprendre de lui-même. Java, quant à lui, ignore complètement les commentaires quand il analyse le code.</p>
<h2 id="compilation">Compilation</h2>
<p>Java est un langage dit “de haut niveau”, c’est-à-dire qu’il offre des abstractions puissantes qui permettent de coder sans être trop proches du “langage machine”. Dans le même panier, on trouvera des langages comme C#, Python, PHP, JavaScript et beaucoup d’autres.</p>
<p>Les langages de bas niveau sont plus proches de la machine, ils sont indispensables en informatique embarquée, ou pour écrire des pilotes de matériel ou encore des systèmes d’exploitation (Windows). Le langage machine est le langage de plus bas niveau ; directement au-dessus on trouve le langage d’assemblage (ou assembleur) qui est une traduction plus ou moins directe des instructions processeurs. En remontant encore d’un niveau, on commence à trouver des abstractions qui permettent d’écrire un code lisible par la plupart des développeurs.</p>
<pre><code>; Langage machine, directement interprétable par le processeur
11000011 00001111
00110011 10001000
11100101 00001011
00110000 00011001
00101000 01110010
10001100 10000010
00000001 10010000
11010001 00010100
00110010 01111100
11000001 01001001
10011111 00011001
00000010 01110001
10000001 00101000
01000111 00001100
00111001 00000001
11111000 01001000
</code></pre>
<pre class=" language-nasm"><code class="prism  language-nasm"><span class="token comment">; En langage assembleur</span>
mov <span class="token register variable">r3</span>, #<span class="token number">15</span>
str <span class="token register variable">r3</span>, <span class="token operator">[</span><span class="token register variable">r11</span>, #<span class="token number">-8</span><span class="token operator">]</span>

mov <span class="token register variable">r3</span>, #<span class="token number">25</span>
str <span class="token register variable">r3</span>, <span class="token operator">[</span><span class="token register variable">r11</span>, #<span class="token number">-12</span><span class="token operator">]</span>

ldr <span class="token register variable">r2</span>, <span class="token operator">[</span><span class="token register variable">r11</span>, #<span class="token number">-8</span><span class="token operator">]</span>
ldr <span class="token register variable">r3</span>, <span class="token operator">[</span><span class="token register variable">r11</span>, #<span class="token number">-12</span><span class="token operator">]</span>
add <span class="token register variable">r3</span>, <span class="token register variable">r2</span>, <span class="token register variable">r3</span>
str <span class="token register variable">r3</span>, <span class="token operator">[</span><span class="token register variable">r11</span>, #<span class="token number">-8</span><span class="token operator">]</span>
</code></pre>
<pre class=" language-c"><code class="prism  language-c"><span class="token comment">// Equivalent en langage C</span>
i <span class="token operator">=</span> <span class="token number">15</span><span class="token punctuation">;</span>
j <span class="token operator">=</span> <span class="token number">25</span><span class="token punctuation">;</span>
i <span class="token operator">=</span> i <span class="token operator">+</span> j<span class="token punctuation">;</span>
</code></pre>
<p>Comme on peut le voir ici, il est beaucoup plus aisé d’écrire un programme dans un langage de haut niveau : l’écriture est plus rapide, les programmes moins longs, plus lisibles et plus faciles à corriger. De plus, les langages de haut niveau sont plus facilement portables d’une architecture de processeur à une autre (c’est notamment l’une des grandes forces de Java).</p>
<p>Avant de pouvoir être exécuté par la machine, un programme Java devra être “traduit” dans le langage de plus bas niveau : le langage machine. Il y a deux grandes familles de transformation : les interpréteurs et les compilateurs :</p>
<ul>
<li>
<p>Un <strong>interpréteur</strong> (ou <strong>interprète</strong>) lit un programme de haut niveau et l’exécute “à la volée”, c’est-à-dire qu’il lit chaque instruction du <strong>code source</strong> et l’exécute immédiatement avant de lire la suivante. À chaque exécution du programme, tout doit être de nouveau interprété.</p>
<ul>
<li>Avantages :
<ul>
<li>s’exécute directement (pas de phase de compilation) ;</li>
<li>facilement portable sur différentes architectures processeur (il suffit d’avoir un interpréteur fonctionnant sur cette architecture).</li>
</ul>
</li>
<li>Inconvénient :
<ul>
<li>à chaque exécution, tout doit être de nouveau interprété (lenteur potentielle)</li>
</ul>
</li>
</ul>
</li>
<li>
<p>Un <strong>compilateur</strong> lit le code source et le traduit entièrement <em>avant</em> exécution. La compilation d’un programme prend un certain temps mais, une fois compilé, le programme s’exécute en général plus rapidement qu’un programme interprété, parce que <strong>l’exécutable</strong> produit est en langage machine : il n’y a pas de “traduction à la volée” pendant l’exécution.</p>
<ul>
<li>Avantages :
<ul>
<li>s’exécute rapidement (langage machine) ;</li>
</ul>
</li>
<li>Inconvénients :
<ul>
<li>le moindre changement dans le code source nécessite de recommencer la phase de compilation ;</li>
<li>moins facilement portable (il faut relancer la compilation sur les différentes architectures, qui ne sont pas toujours 100 % compatibles sans modifications du code source)</li>
</ul>
</li>
</ul>
</li>
</ul>
<p>Java est <em>à la fois compilé et interprété</em>. Au lieu de transformer le code source directement en langage machine, le compilateur Java produit ce qu’on appelle du <em><strong>byte code</strong></em>. Le <em>byte code</em> est une représentation intermédiaire (phase compilation) qui est destinée à être exécutée par une <strong>machine virtuelle Java (JVM)</strong> (phase interprétation). La JVM peut donc être vue comme un interprète de code “compilé spécialement pour elle”, et **immédiatement portable et elle se charge de traduire ce code à la volée pour la machine sur laquelle elle tourne. Cette interprétation est beaucoup plus rapide que celle du code source original (le <em>byte code</em> est optimisé pour cela). Cela combine donc la rapidité du code “compilé” avec la facilité d’utilisation du code interprété.</p>
<p>Le compilateur (<code>javac</code>) transforme le code source (<code>.java</code>) en un fichier <code>.class</code> qui contient le <em>byte code</em> généré. . L’interpréteur Java est un programme nommé <code>java</code> (la JVM) qui va se charger de l’exécution sur la machine cible.</p>
<p><img src="https://lh3.googleusercontent.com/F_jJvAaOVgfym7iAHQPDdHiD7nkanj03iIMT535KeLgd8Vfti9bezv6jETDj2s8_bKBipVo2uq1_" alt="Compilation et exécution d'un programme Java" title="Compilation et exécution Java"><br>
Le développeur écrit le code source dans un fichier <code>.java</code> et utilise la compilateur <code>javac</code> pour le compiler en <em>byte code</em>. Le <em>byte code</em> est généré dans un fichier <code>.class</code> correspondant. Ce fichier est <strong>indépendant de toute architecture processeur</strong>. Le système d’exploitation seul ne peut pas exécuter directement le <em>byte code</em>, il a besoin de la JVM pour lui traduire le <em>byte code</em> dans le langage de la machine hôte.</p>
<p>En lignes de commandes, ça donne :</p>
<pre><code>D:\Dev\Java\src&gt;javac Hello.java
D:\Dev\Java\src&gt;java Hello
Hello world!
</code></pre>
<p>C’est un processus qui peut sembler fastidieux mais, en pratique, nous utiliserons un outil appelé IDE (<em>Integrated Development Environment</em>) qui va permettre d’automatiser tout cela. Mais il est important de savoir ce qui se passe en coulisses, pour être mieux préparé aux éventuels problèmes qui pourraient se poser.</p>
<h2 id="formatage-du-code-source">Formatage du code source</h2>
<p>Certains espaces sont requis dans un programme. Par exemple, on ne peut pas coller des mots clés consécutifs les uns aux autres (<code>publicstaticvoid main...</code> est illégal). Une fois qu’il y a suffisamment d’espaces pour délimiter les mots pour que le compilateur comprenne le programme, ce dernier se fiche complètement de savoir comment les espaces se présentent. Ainsi, dix espaces, deux tabulations ou bien trois passages à la ligne sont équivalents pour lui. Le programme <code>Hello</code> pourrait très bien s’écrire ainsi :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">class</span> <span class="token class-name">Hello</span> <span class="token punctuation">{</span> <span class="token keyword">public</span> <span class="token keyword">static</span>
                            <span class="token keyword">void</span> <span class="token function">main</span>
           <span class="token punctuation">(</span>String<span class="token punctuation">[</span><span class="token punctuation">]</span> args<span class="token punctuation">)</span>
  <span class="token punctuation">{</span><span class="token comment">// Salutations </span>
  System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span>
<span class="token punctuation">(</span><span class="token string">"Hello World!"</span><span class="token punctuation">)</span><span class="token punctuation">;</span> <span class="token punctuation">}</span><span class="token punctuation">}</span>
</code></pre>
<p>Le compilateur s’en accommoderait très bien mais le programme devient beaucoup plus difficile à lire et à comprendre pour un développeur. Les passage à la ligne et les espaces, bien placés, sont essentiels. Les équipes de développement ont en général des conventions de formatage que tous les développeur respectent au sein de la team. Ces conventions sont souvent basées des conventions largement admises par la communauté des développeurs dans un langage donné. Par exemple, en ce qui concerne les accolades, en Java, il est beaucoup plus fréquent de rencontrer ceci :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">class</span> <span class="token class-name">Hello</span> <span class="token punctuation">{</span>
  <span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">void</span> <span class="token function">main</span><span class="token punctuation">(</span>String<span class="token punctuation">[</span><span class="token punctuation">]</span> args<span class="token punctuation">)</span> <span class="token punctuation">{</span>
    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"Hello World!"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<p>que cela :</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">class</span> <span class="token class-name">Hello</span>
<span class="token punctuation">{</span>
  <span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">void</span> <span class="token function">main</span><span class="token punctuation">(</span>String<span class="token punctuation">[</span><span class="token punctuation">]</span> args<span class="token punctuation">)</span>
  <span class="token punctuation">{</span>
    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span><span class="token string">"Hello World!"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<p>Alors que les développeurs C# utiliseront plutôt le deuxième type de formatage. L’important c’est que, au sein d’une équipe ou d’une entreprise, tout le monde se conforme aux mêmes règles (<em>coding standards</em>) : la cohérence est essentielle à la facilité de lecture, et la facilité de lecture est essentielle à une équipe efficace.</p>
<p>Les environnements de développement intégrés (comme VS Code) disposent souvent de formateurs automatiques pour les langages qu’ils supportent.</p>
<h2 id="le-processus-basique-du-développement-logiciel">Le processus basique du développement logiciel</h2>
<p>Tout ce que vous écrirez comme code correspondra à ce qu’on appelle un algorithme. Un <strong>algorithme</strong> est une séquence d’étapes qui décrit comment résoudre un problème donné. Le problème lui-même peut être extrêmement simple (effectuer une addition) ou extrêmement compliqué (<code>amazon.com</code>). L’astuce, c’est qu’un problème compliqué peut être décomposé en problèmes (et donc en algorithmes) de plus en plus simples. Il est important d’avoir toujours cela à l’esprit lorsque l’on cherche à résoudre un problème, quel qu’il soit. C’est une approche appelée <strong>Top-Down</strong>.</p>
<p>Créer des algorithmes et écrire le code correspondant (même quelque chose d’apparemment simple) peut se révéler difficile et surtout source d’erreurs. Les erreurs de programmation sont appelées <strong>bugs</strong>, et le processus qui consiste à les traquer et à les corriger est appelé <strong>débogage (debugging)</strong>. Le débogage peut être lui-même vu comme un problème à résoudre et représente une part non négligeable du travail de développeur.</p>
<p>Plutôt que d’essayer de créer et d’<strong>implémenter</strong> (coder) un algorithme non trivial d’une seule traite, il est souvent souhaitable de partir d’un petit morceau qui fait quelque chose qui fonctionne et de faire des modifications petit à petit, en testant/déboguant à chaque fois, jusqu’à ce que l’algorithme soit complètement implémenté. Cela vous permet de repérer les sources d’erreurs plus facilement.</p>
<p>Finalement, vous vous rendrez compte que programmer est difficile. Parfois, un bug compliqué à traquer ou une incapacité à trouver un algorithme fonctionnel peut vous faire passer par tous les sentiments. Lorsque vous en arrivez à la colère (et même avant), n’oubliez pas que vous n’êtes pas seul. Tous les programmeurs ont les mêmes expériences et seront en général heureux de vous aider. Internet, notamment, regorge de ressources pour toutes les technologies et tous types de problèmes. L’anglais technique est une compétence qui vous facilitera la vie : les sites de référence de questions/réponses, dont le plus célèbre est <a href="http://stackoverflow.com">stackoverflow.com</a>, sont anglophones. Même si la communauté de développeurs francophones est aussi très active sur internet, il est souhaitable, à défaut de savoir <em>écrire</em> l’anglais, de le <em>lire</em> sans trop de difficultés.</p>

