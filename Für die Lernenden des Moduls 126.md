---


---

<p>Peripheriegeräte im Netzwerkbetrieb einsetzen</p>
<hr>
<h2 id="modul-126-webmin">Modul 126 Webmin</h2>
<h2 id="für-die-lernenden-des-moduls-126"><em>Für die Lernenden des Moduls 126:</em></h2>
<p><img src="https://thebroodle.com/wp-content/uploads/2017/06/Webmin-in-Raspberry-Pi.jpg" alt="enter image description here"></p>
<pre><code>					Sarankan Mahendran
						22.10.2019
						Herr Calisto
						BI17, TBZ
</code></pre>
<h1 id="inhaltsverzeichnis">Inhaltsverzeichnis</h1>
<ol>
<li><a href="#example">Webmin Konfiguration</a></li>
<li><a href="#example2">Einführung und Auftrag</a></li>
<li><a href="#example3">Materialiste</a></li>
<li><a href="#example4">Installation Webmin auf Raspberry PI:</a></li>
<li><a href="#example5">Erwitterter Auftrag: User Asministration</a></li>
<li><a href="example6">Qualitätskontrolle</a></li>
</ol>
<h2 id="webmin-konfiguration">Webmin Konfiguration</h2>
<p>So sieht die Localhost Webseite des Webmines aus:<br>
<img src="https://cdn.instructables.com/F8G/938I/IBAAKZK3/F8G938IIBAAKZK3.LARGE.jpg?auto=webp&amp;&amp;frame=1&amp;width=1024&amp;fit=bounds" alt="Image result for webmin raspberry pi"></p>
<h2 id="einführung-und-auftrag">Einführung und Auftrag</h2>
<p>Hallo lieber Benutzer</p>
<p>Wenn Peripheriegeräte von Benutzern administriert werden sollen, reicht ein SSH Zugang oft<br>
nicht, es braucht ein Webinterface. Sie benutzen deshalb in diesem Werkstatt Auftrag den Webmin.<br>
Webmin ist eine <strong>Software für Administratoren</strong> um einen Server zu administrieren. Die Software bietet jede Menge Funktionen an damit man einen Rechner über ein Webinterface administrieren kann und nicht über die Kommandozeile. Raspberry Pi Webmin kann man auch für seinen Raspberry Pi einsetzen. Das ist keine eigene Software, man kann die selbe Software wie für Server auch für den kleinen Rechner verwenden, ich zeige euch wie man das macht.<br>
Mehr dazu unter: <a href="http://www.webmin.com/">http://www.webmin.com/</a></p>
<h2 id="los-geht´s-viel-spass-und-viel-erfolg-">Los geht´s! Viel Spass und viel Erfolg! :)</h2>
<h2 id="materialiste">Materialiste</h2>
<p><strong>Hardware:</strong></p>
<ul>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" disabled=""> Raspberry Pi (inkl. Stromkabel</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" disabled=""> Zwei LAN Kabel</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" disabled=""> Monitor, Maus und Tastatur</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" disabled=""> HDMI-, Display-Port-, oder VGA kabel</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" disabled=""> Speicherkarte</li>
</ul>
<p><strong>Software:</strong></p>
<ul>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" disabled=""> OS-Image (auf der Speicherkarte)</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" disabled=""> VNC - Viewer</li>
<li class="task-list-item"><input type="checkbox" class="task-list-item-checkbox" disabled=""> Webmin (Localhost)</li>
</ul>
<h2 id="installation-webmin-auf-raspberry-pi">Installation Webmin auf Raspberry PI:</h2>
<ol>
<li>Zuerst müssen Sie noch zwei Libraries für PERL (Skriptsprache) installieren, damit Webmin dann später per SSL auf seinen Server zugreifen kann</li>
</ol>
<blockquote>
<p>sudo apt-get install libnet-ssleay-perl libio-socket-ssl-perl</p>
</blockquote>
<ol start="2">
<li><strong>Neuste MINIMALE Version</strong> auf SourgeForge-Server evaluieren: <strong>1.930</strong><br>
[<a href="https://sourceforge.net/projects/webadmin/files/webmin/1.930">https://sourceforge.net/projects/webadmin/files/webmin/1.930</a><br>
<strong>Im Folgenden muss die Vereinsangabe auf 1.930 entsprechend ersetzt/aktualisiert werden!</strong><br>
Da Webmin modular aufgebaut ist und die meisten Module für den RasperryPi nicht benötigt<br>
werden, reicht es aus, die minimale Version von Webmin zu installieren. Als ersten Schritt kann<br>
man also das Webmin Archiv ins Home Verzeichnis laden. (Oder siehe BSCW falls download<br>
misslingt… Grösse ca. 2.8MB)</li>
</ol>
<blockquote>
<p><strong>cd</strong><br>
<strong>wget</strong> <a href="http://prdownloads.sourceforge.net/webadmin/webmin-1.930-minimal.tar.gz">http://prdownloads.sourceforge.net/webadmin/webmin-1.930-minimal.tar.gz</a></p>
</blockquote>
<ol start="3">
<li>Danach kann das Tar-Archiv entpackt werden:</li>
</ol>
<blockquote>
<p><strong>tar</strong> -zxvf webmin-1.930-minimal.tar.gz</p>
</blockquote>
<ol start="4">
<li>Nun in das neu erstellte Verzeichnis wechseln und die Installation ausführen:</li>
</ol>
<blockquote>
<p><strong>cd</strong> webmin-1.930<br>
<strong>sudo</strong> ./setup.sh</p>
</blockquote>
<ol start="5">
<li>
<p>Sämtliche Einstellungen können auf Default gelassen werden, da hier nur Pfade für<br>
Verzeichnisse angegeben werden.<br>
Ebenfalls kann der Anmeldenamen auf Default gelassen werden, da er dann einfach <strong>«admin»</strong><br>
lautet.<br>
[BILD]
</li>
<li>
<p>Zum Schluss muss noch ein Passwort gesetzt werden.<br>
[BILD]</p>
</li>
<li>
<p>Hier sieht man nochmals alle relevanten Daten für das Login:<br>
[BILD]</p>
</li>
<li>
<p>Als aller letztes kann noch die Option mit «Y» bestätigt werden, dass beim Start des Systems<br>
Webmin gestartet werden soll.<br>
Die Installation ist somit abgeschlossen und Webmin wird automatisch gestartet.</p>
<p>Nun kann von einem anderen Gerät heraus auf den RasPi zugegriffen werden. Wie bereits zu<br>
sehen ist, kann man dies über den Hostnamen (oder IP-Adresse) und den Port 10000:<br>
«<a href="http://hostname:10000/%C2%BB">http://hostname:10000/»</a><br>
[BILD]</p>
</li>
<li>
<p>Das Webmin Interface erscheint nun im Browserfenster. Hier kann man unter «Webmin<br>
Configuration» und dann «Webmin Modules» zusätzliche Module installieren …<br>
[BILD]</p>
</li>
<li>
<p>Punkt (.) «Standart module from <a href="http://www.webmin.com">www.webmin.com</a>» angewählen!<br>
Mit […] kann die Moduldatenbank von Webmin durchstöbert werden, oder direkt ein Link<br>
angegeben werden. Hier können Sie alle in der Kann-Liste geforderten Module auswählen und<br>
mit [Install Module] installieren!</p>
<p>Die nötigen Dateien werden dann heruntergeladen und oft gibt’s gleich eine Möglichkeit das<br>
Modul zu testen via Button!</p>
</li>
</ol>
<h2 id="erwitterter-auftrag-user-administration">Erwitterter Auftrag: User Administration</h2>
<ol>
<li>
<p>Um weitere User verwalten zu können, wollen wir das «useradmin» Modul installieren. Zum<br>
Schluss auf [Install Module] klickten und die Installation wird durchgeführt.<br>
[BILD]<br>
[BILD]</p>
</li>
<li>
<p>Nach abgeschlossener Installation kann direkt ins Modul gesprungen werden oder via<br>
System&gt;User and Groups<br>
[BILD]</p>
</li>
<li>
<p>Hier kann nun ein neuer User erstellt werden. Man gibt nun den Namen sowie das Passwort an.<br>
Es soll immer ein Passwort gesetzt werden, auch wenn keines nötig wäre.<br>
[BILD]</p>
</li>
<li>
<p>Da dieser User kein Administrator werden soll, kann er in der primären Gruppe «users» gelassen<br>
werden und brauch keine sekundären Gruppen. Sobald alle Einstellungen gemacht sind, kann<br>
mit [Create] der User erstellt werden:<br>
[BILD]<br>
Nun sollte auf der Liste bereits der neue User ersichtlich sein.<br>
Ein Admin-User disablen:</p>
<p>Erstellen Sie nun einen zweiten Account “admin” mit Adminrechten und aktivieren Sie ihn!<br>
Nun kann dieser User «admin» angewählt und auf «Disable Selected Users» geklickt werden.<br>
Anschliessend sollte der User «admin» kursiv geschrieben sein. Dadurch kann man sehen, dass<br>
dieser deaktiviert wurde.</p>
</li>
</ol>
<h2 id="qualitätskontrolle">Qualitätskontrolle</h2>
<p>Mit dem folgenden Befehl kann man kontrollieren, ob der Webmin Service funktioniert.</p>
<blockquote>
<p>sudo service webmin status</p>
</blockquote>

