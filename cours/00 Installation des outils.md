---


---

<h1 id="installation-des-outils">Installation des outils</h1>
<h2 id="installation-du-jdk">Installation du JDK</h2>
<p><a href="https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html">https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html</a></p>
<ul>
<li>“<em>JDK oracle download</em>” sur Google, sélectionnez le JDK 11</li>
<li>Cochez “<em>Accept License Agreement</em>”</li>
<li>Téléchargez “<em>jdk-NNN_windows-x64_bin.exe</em>”</li>
<li>Installez en acceptant tout</li>
</ul>
<h2 id="mise-à-jour-de-la-variable-path-de-windows">Mise à jour de la variable PATH de Windows</h2>
<ul>
<li>Cliquez sur “<em>Démarrer</em>”, tapez “<em>environ</em>”, cliquez sur “<em>Éditer les variables d’environnement</em>”</li>
<li>Dans la fenêtre qui s’ouvre, cliquez sur le bouton “<em>Variables d’environnement</em>”</li>
<li>Ajoutez l’emplacement du répertoire “<em>bin</em>” du JDK en éditant la variable “PATH” dans “<em>Variables utilisateur</em>”. La liste devra ressembler à :<br>
<code>C:\WINDOWS\system32;C:\WINDOWS;...;</code><strong><code>C:\Program Files\Java\jdk-11\bin</code></strong></li>
<li>Pour vérifier : ouvrez un terminal (clic-droit sur démarrer, ou alors lancez <code>cmd.exe</code>)</li>
<li>Tapez <code>javac -version</code> (devrait afficher la version de Java installée)</li>
</ul>
<h2 id="configuration-java-sous-vs-code">Configuration Java sous VS Code</h2>
<ul>
<li>Dans le panneau “<em>Extensions</em>”, recherchez “<em>java</em>”</li>
<li>Localisez et installer “<em>Java Extension Pack</em>”</li>
<li>Redémarrez VS Code</li>
<li>Allez dans les options de VS Code (<code>Ctrl+,</code> ou bien utilisez la palette de commande)</li>
<li>Rechercher “<em>java.home</em>”</li>
<li>Ouvrez <code>settings.json</code> comme proposé pour éditer la valeur</li>
<li>À gauche, tous les paramètres par défaut de VS Code (fichier en lecture seule) ; à droite, les paramètres utilisateur, qui écrasent les valeurs par défaut lorsqu’elles sont redéfinies. L’idée est donc d’éditer ce fichier utilisateur chaque fois que vous voulez changer une valeur de paramètre par défaut.</li>
<li>Cliquez sur la petite icône à côté de l’entrée <em>java.home</em> sur le fichier de gauche. Cela va créer une entée dans le fichier de droite que vous pourrez redéfinir.</li>
<li>Éditez la valeur nouvellement définie dans le fichier options utilisateur pour pointer sur le répertoire du JDK (sans le <code>\bin</code>) :<br>
ex : <code>"java.home": "C:\\Program Files\\Java\\jdk-11"</code></li>
<li>Notez qu’il faut doubler les antislash (<code>\\</code>) sous Windows</li>
</ul>
<h2 id="installation-de-apache-maven">Installation de Apache Maven</h2>
<p><em>Maven</em> : “gestionnaire de projets” essentiellement utilisé pour Java</p>
<p><a href="http://mirrors.ircam.fr/pub/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip">http://mirrors.ircam.fr/pub/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip</a></p>
<ul>
<li>Dézippez dans votre répertoire <em>Programmes</em> ou <em>Program Files</em> (selon système)</li>
<li>Éventuellement dézippez d’abord ailleurs et copiez/collez si problèmes de droits</li>
<li>Éditez la variable PATH de Windows (procédez comme plus haut) pour ajouter le répertoire <code>\bin</code> de Maven<br>
ex: <code>C:\Program Files\apache-maven-3.5.4\bin\</code></li>
</ul>
<h2 id="création-dun-nouveau-projet-java-avec-maven">Création d’un nouveau projet Java avec Maven</h2>
<ul>
<li>Tapez “maven” dans la palette de commandes VS Code (<code>Ctrl+Shift+P</code>)</li>
<li>Sélectionnez <em>Maven: Generate from Maven Archetype</em></li>
<li>Sélectionnez <em>archetype-quickstart-jdk8</em></li>
<li>Indiquez le répertoire de destination de tous vos projets Java (par exemple : <code>c:\valarep\java\</code>)</li>
<li>Maven lance la génération interactive de projet et va vous demander quelques précisions</li>
<li>S’il ne trouve pas la commande <code>mvn</code> : problème d’installation de Maven. Relancez VS Code, vérifiez l’installation, vérifiez le PATH…</li>
<li><code>Define value for property 'groupId':</code> (indiquez le nom de votre répertoire de projets, dans une forme similaire aux <em>packages</em> Java, par exemple <em>fr.valarep.java</em>)</li>
<li><code>Define value for property 'artifactId':</code> (indiquez le nom du projet lui-même, par exemple <em>Hello</em>)</li>
<li><code>Define value for property 'version' 1.0-SNAPSHOT:</code> version initiale du projet ; appuyez juste sur Entrée pour valider la valeur par défaut</li>
<li><code>Define value for property 'package':</code> nom du <em>package</em> ; laissez la valeur par défaut (c’est la valeur du <code>groupId</code> précédemment indiquée)</li>
<li>Maven vous résume le tout :</li>
</ul>
<pre><code>Confirm properties configuration:
groupId: fr.valarep.java
artifactId: Hello
version: 1.0-SNAPSHOT
package: fr.valarep.java
Y: :
</code></pre>
<ul>
<li>Confirmez en tapant <em>Y</em></li>
<li>L’arborescence du projet est maintenant créée</li>
<li>Dans l’explorer VS Code, cliquez sur “<em>Open Folder</em>”</li>
<li>Trouvez et sélectionnez le répertoire que vous venez de créer (<em>Hello</em>)</li>
<li>Le projet s’ouvre dans VS Code, avec tous les répertoires et fichiers générés par Maven</li>
<li>Dans VS Code, localisez et ouvrez <em>src\main\java\fr\valarep\java\App.java</em> (selon ce que vous aurez entré auparavant)</li>
<li><code>App.java</code> contient la base d’un programme Java sur laquelle vous allez pouvoir créer vos propres programmes</li>
</ul>
<h2 id="création-dun-compte-github">Création d’un compte Github</h2>
<ul>
<li><strong>Git</strong> : logiciel gestion de versions</li>
<li><strong>Github</strong> : service web d’hébergement et de gestion de développement de logiciels basé sur Git</li>
<li>Github offre un hébergement gratuit pour des projets publics</li>
<li><a href="http://github.com">github.com</a> : remplir <em>username, email, password</em></li>
<li>Résolvez le puzzle s’il y en a un et cliquez sur <em>done</em></li>
<li>Restez sur l’option <em>Free</em> et cliquez sur <em>Continue</em></li>
<li>Cliquez sur <em>Skip this step</em></li>
<li>Terminé !</li>
<li>Par la suite, nous essaierons de voir brièvement comment utiliser Github pour héberger et gérer vos projets</li>
<li>Mais le compte ne va dans un premier temps nous servir que pour nous connecter à <em>VS Live Share</em></li>
</ul>
<h2 id="installation-de-vs-live-share-sous-vs-code">Installation de <em>VS Live Share</em> sous VS Code</h2>
<ul>
<li><em>VS Live Share</em> permet la collaboration en temps réel sous plusieurs instances distantes de VS Code, c’est-à-dire que chacun pourra voir et éditer le même fichier source</li>
<li>Dans le panneau “<em>Extensions</em>” de VS Code, recherchez “<em>live share</em>”</li>
<li>Localisez et installer <em>VS Live Share</em></li>
<li>Redémarrez VS Code</li>
</ul>
<h2 id="rejoindre-une-session-collaborative-sous-vs-code">Rejoindre une session collaborative sous VS Code</h2>
<ul>
<li>La session collaborative doit être lancée au préalable sur l’ordinateur-maître</li>
<li>L’utilisation de <em>Live Share</em> requiert un compte Github</li>
<li>Lancez la commande <em>Join Collaboration Session</em> sous VS Code (via la sidebar <em>Live Share</em> ou la palette de commandes)</li>
<li>Cliquez sur <em>Sign in</em> dans la notification qui s’affiche</li>
<li>Cliquez sur <em>Sign in with Github</em> dans la page internet qui s’affiche</li>
<li>Si vous n’étiez pas connecté à Github, on vous demande votre login/mot de passe</li>
<li><em>Ready to collaborate!</em> : fermez l’onglet</li>
<li>Copiez le lien de session collaborative de la séance donné entre-temps sur Slack</li>
<li>Sous VS Code, collez le lien dans la boîte qui s’est affichée (<em>Enter URL…</em>) et pressez Entrée</li>
<li>Vous devriez avoir rejoint la session collaborative</li>
</ul>

