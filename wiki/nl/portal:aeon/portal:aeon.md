= openSUSE Aeon =

{{Warning|Op 27 mei is de openSUSE MicroOS Desktop omgedoopt tot openSUSE Aeon en de Plasma Desktop variant is hernoemd naar [[Portal:Kalpa|openSUSE Kalpa]]. Pas op voor het neerdalende stof terwijl we alles migreren van MicroOS Desktop naar de nieuwe namen.}}

{{Info|openSUSE Aeon biedt ALLEEN een minimaal basissysteem met een GNOME Desktop Omgeving en basis configuratie tools.
Alle applicaties, Browsers, Codecs, etc worden aangeboden via FlatPaks van FlatHub.}}

{{Point here|[[Image:Icon-warning.png|48px|link=]]|
openSUSE Aeon is nog steeds in het '''Release Candidate''' stadium. Houd hier rekening mee!
}}
----
== Voor wie is openSUSE Aeon? ==
Het is NIET voor iedereen. Je hoogst aanpasbare Tumbleweed & Leap Desktops zijn veilig en blijven de beste keuze voor diegenen die willen knutselen met hun Desktop.

Aeon zal perfect zijn voor gemakkelijk aangelegde ontwikkelaars, die niets aan hun Desktop willen aanpassen alleen maar "hun ding doen", vooral wanneer ze containers ontwikkelen.

Het zal een hetzelfde publiek aantrekken dat gewend is aan iOS, Chromebook of Anrdoid-achtige ervaringen waarbij het OS statisch, geautomatiseerd & betrouwbaar is en de Apps de belangrijke zaken zijn voor de gebruiker.

Wil je in het diepe te duiken over het begin en de redenen waarom sommige gebruikers Aeon zouden moeten gebruiken, kijk naar de volgende workshop: 

https://www.youtube.com/watch?v=lKYLF1tA4Ik&t=1794s

----

== Ontwerp Doelen ==
Aeon zal betrouwbaar, voorspelbaar en onveranderlijk zijn, net zoals openSUSE MicroOS.

Aeon zal minder instelbaar zijn dan openSUSE Tumbleweed/Leap.

Aeon is klein, maar dat gaat niet ten koste van de functionaliteit. Printen, Gamen, Media Productie en
veel meer zal allemaal werken.

Aeon werkt gewoon “out of the box” zonder de noodzaak van extra configuratie om functionaliteit te krijgen zoals software installatie en web browsen. Alle features die standaard meegeleverd worden werken standaard. Features die niet werken worden niet meegeleverd, zijn onzichtbaar en niet beschikbaar voor gebruikers.
----

== Hoe te downloaden en installeren ==
# Installatie media is op dit moment alleen beschikbaar onder de oude projectnaam 'MicroOS Desktop'
# Download het openSUSE MicroOS basis ISO image via https://en.opensuse.org/Portal:MicroOS/Downloads
# Schrijf het ISO bestand op een USB drive en start het installatieproces.

----

== Manieren om applicaties te installeren in een bepaalde volgorde ==

Nu u Aeon heeft geinstalleerd, wilt u waarschijnlijk software installeren. 

Omdat Aeon alleen een minimaal basissysteem met een desktop omgeving, is het ontworpen om standaard alleen de basis configuratiemiddelen te hebben. 

Hierdoor worden alle applicaties, browsers, codecs die nodig zijn voor specifieke apps worden voorzien door FlatPaks via FlatHub.

Om dit proces voor gebruikers makkelijker te maken, is de Flathub opslagruimte van alle beschikbare flatpaks geïntegreerd in de GNOME software. Op deze manier kun je eenvoudigweg zoeken naar al je favoriete apps op een naadloze en geïntegreerde manier.

Hoewel er andere manieren zijn om software te installeren, is het belangrijk om te onthouden dat het STERK aanbovelen is om software te installeren in de volgorde zoals deze hieronder staat:

# Flatpaks van je software center naar keuze of [https://flathub.org/home Flathub]
# RPM's in een gebruikers distrobox ''distrobox-enter''  
# RPM's in een root distrobox ''distrobox-enter -r''
# RPM's via transactional-update -- voor drivers, kernel modules, puur voor wat je nodig hebt om het host besturingssysteem te laten werken.

'''Samenvattend: ALLES moet gedaan worden via Flatpaks of geïnstalleerd worden in een Distrobox wanneer een pakket niet beschikbaar is als flatpak. Gebruik maken van transactional-update is puur voor wat je nodig hebt om het host systeem werkend te houden (exotische drivers, gespecialiseerde vpn services).'''

Note: Distrobox wordt standaard meegeleverd met Aeon. Het stelt gebruikers in staat elke linux distributie in terminal te installeren. Voor diegenen die GUI-apps willen draaien via Distrobox dan kan dat door gebruik te maken van een spciaal export commando zodat apps meer direct en als geïntegreerd in het systeem aanvoelen. Kijk op [[https://en.opensuse.org/Portal:Aeon#DistroBox Distrobox section]] om meer te leren over deze gemakkelijk manier om Distrobox apps te starten vanuit je host menu launcher. 

==== Een kennismaking met transactional-update ====

openSUSE Aeon gebruikt ''zypper niet''' zoals openSUSE Tumbleweed of Leap om RPM pakketten te installeren en hen direct te gebuiken. openSUSE Aeon gebruikt '''transactional-update''' met zypper onder de motorkap.
In het merendeel van de gevallen hoef je deze commando's niet interactief te gebruiken, omdat Aeon een automatisch update systeem via de ''transactional-update.service'' systemd service.

==== transactional-update - voorbeeld commando's ==== 

Commando's voor tansactional-update staan hieronder. LET OP: Denk eraan om opnieuw op te starten nadat het commando klaar is om de wijzigingen af te ronden!
* ''sudo transactional-update pkg install package_name'' installeert een rpm pakket
* ''sudo transactional-update pkg remove package_name'' verwijdert een rpm pakket
* ''sudo transactional-update dup'' een systeem upgrade uitvoeren naar de volgende release
* ''sudo transactional-update shell'' open een shell van de volgende snapshot (je kunt hier zypper commando's gebruiken). '''Dit moet alleen gebruikt worden voor het debuggen'''. Elk bug rapport dat alleen waarbij de reproductie alleen kan via transactional-update shell wordt vrijwel zeker gesloten als een WONTFIX.
* ''sudo transactional-update rollback snapshot_nummer'' rol het systeem terug naar het snapshot nummer. Gebruik 'last' in plaats van het snapshot nummer om terug te gaan naar het laatst werkende snapshot. '''Gebruik snapper niet voor rollbacks.'''

==== transactional-update - Automatische Update ====

Standaard zal ''transactional-update.timer'' zorgen voor geautomatiseerde systeem updates. Deze is ingesteld op ''dagelijks'' wat betekent dat de taak uitgevoerd zal worden elke dag om 00:00:00.

In het geval dat deze tijd verstrijkt omdat de computer uitstaat, zal de timer omdat deze is ingesteld met persistance=true de update uitvoeren bij de eerste mogelijkheid. 

Enkele redenen waarom het niet mogelijk is om een update te triggeren: 

* de computer was uit
* de internet verbinding was verstoord - wanneer de taak startte.

Dit zal geen problemen veroorzaken vanwege de manier waarop ''transactional-update'' werkt omdat de nieuwe pakketten geïnstalleerd worden in een nieuw snapshot waarvoor het nodig is om opnieuw op te starten zodat de wijzigingen effect hebben.

Om te zien of ''transactional-update'' in staat is om te upgrade en ook correct werkt kun je gebruik maken van ''journalctl'':

  $ sudo journalctl -u transactional-update.service 

Je kunt ook ''journalctl'' met de ''-f'' vlag gebruiken om de logs in real time te volgen.

==== transactional-update - --Afsluitende opmerkingen over snapshots en opstart gedrag ====
Standaard zal elk ''transactional-update'' commando een apart, zelf begrensde, snapshot maken dat de wijzigingen bevat van het ''transactional-update'' commando.

Dit snapshot is '''GEBASEERD OP HET LAATSTE BEKEND GOEDE/OPGESTARTE SNAPSHOT'''. Het laatste van meerdere snapshots ontstaan door meerdere ''transactional-update'' commando's zal uiteindelijk gebruikt worden na een reboot.

Met andere woorden ''sudo transactional-update pkg install $pkg1'' gevolgd door ''sudo transactional-update pkg install $pkg2'' and dan herstarten resulteert in een systeem dat $pkg2 heeft geïnstalleerd, maar NIET $pkg1.

Dit is het verwachte en logische gedrag - Aeon zal altijd vertrekken vanuit het laatste bekend goede/opgestarte snapshot naar de nieuwste staat in de kortste, minst verstorende weg mogelijk.

Dit vooral begrijpelijk wanneer je er bij stil staat dat Aeon zichzelf update en dat de meeste gebruikers überhaupt ''transactional-update'' niet interactief zullen gebruiken. Omdat ''transactional-update dup'' op gezette tijden uitgevoerd wordt in de achtergrond, zorgt Aeon ervoor dat het de update gaat naar de laatste schone systeem update gaat, niet een of andere vreemde hybride van voorgaande niet opgestarte en niet gecontroleerde tussen vorm van ''transactional-update dup''.

Echter, wanneer je de best practice negeert en ''transactional-update'' interactief gebruikt, dan zijn er momenten dat je ''transactional-update'' wilt gebruiken met een bestaande nog niet opgestarte onbekend-of-goed snapshot.

Gebruik hiervoor ''transactional-update --continue''

Voorbeeld:

''sudo transactional-update pkg install $pkg1'' gevolgd door ''sudo transactional-update --continue pkg install $pkg2'' zal $pkg1 installeren en daarna $pkg2 in hetzelfde snapshot als $pkg1, en markeert het gecombineerde snapshot als volgende opstart doel.

Wanneer er problemen ontstaan is er echter geen extra complexiteit om uit te zoeken welk pakket het probleem veroorzaakte omdat gebruikers terug zullen moeten gaan naar het eerdere snaptshot voodat $pkg1 was geïnstalleerd. Dit om terug te keren naar de laatst bekend goede staat.
----

== GNOME Software + Flathub Integratie ==
Gnome is momenteel in het '''RC''' stadium.

* Bij eerste opstart worden flatpaks aangezet en sommige flatpaks standaard geïnstalleerd (Mozilla Firefox, Text Editor, Gnome Calculator en Extension Manager).

* Na het eindigen van het eerste opstart script kun je Gnome Software openen om meer software te installeren vanuit flathub. 

----

== DistroBox ==

''Distrobox'' kan gebruikt worden als toolbox (welke standaard inbegrepen is bij de server versie van MicroOSwhich), maar heeft enkele andere voordelen voor desktop gebruik.
Kijk op https://github.com/89luca89/distrobox voor alle opties.

[[Distrobox|Voor meer documentatie, zie de Distrobox pagina]]
----

== Troubleshooting ==

Deze paragraaf beschrijft de bekende issues met openSUSE Aeon en hun oplossing.

==== Hostnaam instellen ====

Het instellen van je hostnaam doe je met het volgende commando en niet vanuit Gnome Settings:

   # sudo hostnamectl set-hostname <nieuwe naam>

Herstart en de nieuwe hostnaam is ingesteld. 

==== transactional-update.timer Aanpassen ====

Afhankelijk van je dagelijkse routine kan de Timer soms het automatische update proces niet triggeren zelf met persistent=true omdat het een willekeurige vertraging toevoegt met ''RandomizedDelaySec'' 

Wilt u automatische ''dagelijkse'' updates op up systeem? Pas in dat geval de vertraging naar wens aan. 

transactional-update.timer Bewerken:

   # sudo systemctl edit transactional-update.timer

Voeg de volgende regels toe om een override.conf te maken (bevindt zich in /etc/systemd/system/transactional-update.timer.d/override.conf)

   [Timer]
   RandomizedDelaySec=5m

Het voorbeeld hierboven is voor een willekeurige vertraging van maximaal 5 minuten (standaard is 2 uur).

Pas de tijd aan naar je wensen. Gebruik [https://www.freedesktop.org/software/systemd/man/systemd.time.html dit als naslagwerk].

==== Steam Proton, Bottles, WINE, Lutris, Android Studio emulator werken mogelijk niet vanuit flatpaks ====

Wanneer je problemen ervaart bij het gebruik van WINE en op WINE gebaseerde programma's in flatpaks, dan is dit waarschijnlijk een SELinux issue en kan gecontroleerd worden door onderstaand commando uit te voeren:

   # sudo getsebool selinuxuser_execmod

For Android Studio:

   # sudo getsebool selinuxuser_execstack

Wanner de terugkoppeling 'selinuxuser_execmod --> disabled' en 'selinuxuser_execstack --> disabled' dan zul je deze moeten aanzetten.  Dit kan tijdelijk gedaan worden (reset na herstart)

Voor WINE:
   # sudo setsebool selinuxuser_execmod 1

Voor Android Studio:
   # sudo setsebool selinuxuser_execstack 1

Of kan permanent ingesteld worden:

   # sudo setsebool -P selinuxuser_execmod 1
   # sudo setsebool -P selinuxuser_execstack 1

Het openSUSE Security team bekijkt deze standaard beleidsregels, en je zet deze aan op je eigen risico. Zie https://bugzilla.opensuse.org/show_bug.cgi?id=1206292 & https://bugzilla.opensuse.org/show_bug.cgi?id=1206789 voor meer informatie.

----

== Bugs rapporteren ==

Volg onderstaande link bugs te rapporteren: [https://bugzilla.opensuse.org/enter_bug.cgi?product=openSUSE+Aeon&format=guided Rapporteer een bug voor openSUSE Aeon]

Kijk op [[openSUSE:Submitting_bug_reports|Bug rapporten indienen]] voor meer information hoe het beste een bug in te dienen.

== Plek voor vragen ==
openSUSE Aeon heeft diverse plekken om  te praten over het project:

* ''Telegram'': https://t.me/openSUSE_Aeon
* ''Matrix'': https://matrix.to/#/#aeon:opensuse.org
* ''Discord'': https://discord.gg/opensuse #aeon-kalpa channel

Al deze kanalen zijn met elkaar verbonden via Matrix, dus opmerkingen in een kanaal is vanzelf te zien in de andere twee.


[[Categorie:Aeon]]
[[Categorie:Kalpa]]
