<!--- this is the SHORT list of highlight features only --->
'''openSUSE Leap 15.5 is...'''

Is deze highlight te kort? Zie [[Features_15.5]] voor meer gedetailleerde informatie over komende veranderingen.

{{Point here|[[Image:Icon-network.png|48px|link=]]|'''Software vakmanschap'''
<p>Vorige versies van openSUSE Leap hebben geweldig werk geleverd om de bronbestanden gelijk te houden aan SUSE Linux Enterprise, maar [[openSUSE:Build_Service_cross_distribution_howto |andere opbouw configuratie]] resulteerde in veschillende feature sets aan beide zijden van deze kameleon distributies. Deze release van openSUSE Leap gaat verder dan de vorige bronnen en verenigt feature sets en het bouwen van openSUSE Leap bovenop binaire pakketten van SUSE Linux Enterprise 15 SP5. De release wordt volledig binair identiek met openSUSE Leap 15.5 en SUSE Linux Enterprise 15 SP5.</p>
}}

{{Point here|[[Image:Icon-network.png|48px|link=]]|'''Naadloze migratie'''
<p>De [[SDB:How_to_migrate_to_SLE|naadloze migratie]] ervaring van Leap naar SUSE Linux Enterprise Server is vrijwel onmiddellijk. De patroonwijzigingen om naar SUSE Linux Enterprise te migreren zijn moeiteloos. Mochten gebruikers van openSUSE Leap moeten migreren, dan is de optie beschikbaar en kunnen gebruikers vertrouwen op de mogelijkheid om te migreren naar enterprise ondersteuning. Meer informatie (in het engels) over hoe de distributies zijn opgebouwd, vindt u [https://www.suse.com/c/how-suse-builds-its-enterprise-linux-distribution-part-5/ hier].</p>
}}

{{Point here|[[Image:ai.png|48px|link=]]|'''Kunstmatige Intelligentie'''<br />
<p>Vele Kunstmatige Intelligentie pakketten zijn beschikbaar in Leap 15.5.</p>

<p>PyTorch: Gemaakt voor zowel server als reken bron, versnel deze machine learning bibliotheek de mogelijkheden voor power users om een prototype van een project te maken en deze in produktie uit te rollen.</p>

<p>ONNX: Een open formaat gebouwd om machine learning modellen weer te geven, biedt interoperabiliteit in de AI-toolruimte. Het laat Kunstmatige Intelligentie ontwikkelaars modellen gebruiken met een verscheidenheid aan frameworks, hulpmiddelen, runtimes en compilers.</p>
}}

{{Point here|[[Image:Icon-nvme.png|48px|link=]]|'''Opstarten van NVMe-oF™ over TCP'''<br />
<p>openSUSE Leap 15.5 heeft out-of-the-box ondersteuning voor installatie op en opstarten vanaf [[NVMExpress|NVM Express®]] over Fabrics (NVMe-oF™) via het TCP transport volgens de [https://nvmexpress.org/wp-content/uploads/NVM-Express-Boot-Specification-2022.11.15-Ratified.pdf NVMe-oF boot specification 1.0]. Dit maakt flexibele creatie en beheer van diskloze clients binnen SAN-omgevingen mogelijk door middel van de laatste NVMe-oF technologie.

Deze feature vereist ondersteuning in het UEFI BIOS van het systeem, waar het netwerk en NVMe-oF doelen worden geconfigureerd. De firmware gebruikt deze informatie om de kernel te starten. Het besturingssysteem krijgt de configuratie informatie van de firmware en gebruikt deze voor het koppelen van het root bestandssysteem via NVMe-oF.</p>
}}


===Voor Gebruikers===

{{Point here|[[Image:Logo-kde.png|48px|link=]]|'''KDE'''<br />
<p>
Plasma 5.27 LTS is een lange termijn ondersteunings release van het KDE Plasma team. Leap 15.5 bevat deze nieuwe LTS versie. In Plasma 5.27 zijn er grote verbeteringen aangebracht.

Een Konqi welkomst wizard verschijnt in deze release om nieuwkomers met de kracht van open source software.

Nu we het toch over features hebben, bekijk ook het nieuwe tegel systeem: Het maakt het mogelijk om je eigen tegel layouts te maken en tegelijkertijd ook de naastliggende getegelde vensters van grootte te veranderen. Je activeert dit in Systeeminstellingen > Gedrag van werkruimte > Bureaubladeffecten.  
</p>
}}

{{Point here|[[Image:Logo-gnome.png|48px|link=]]|'''GNOME'''<br />
<p>
Leap 15.5 biedt GNOME 41. GNOME 41 is het resultaat van zes maanden werk door het GNOME project. Het omvat een behoorlijk aantal verbeteringen en nieuwe features, alsook een grote collectie kleine verbeteringen.

De meest merkbare veranderingen in deze release zijn, een verbeterde Software app, nieuwe multitasking instellingen en een verbeterd power management. Met deze veranderingen is GNOME slimmer, flexibeler en biedt een rijkere en meer boeiende ervaring dan voorheen.

De nieuwe release komt ook met significante verbeteringen voor ontwikkelaars: een documentatie website voor ontwikkelaars, een nieuwe versie van de Human Interface Guidelines, nieuwe features in de Builder IDE, GTK 4 verbeteringen en veel meer.
</p>
}}

{{Point here|[[Image:Logo-xfce.png|48px|link=]]|'''Xfce'''<br />
<p>
De Xfce Desktop versie in Leap 15.5 is 4.18. Xfce 4.18 introduceert grote nieuwe features. Een prettige widget voor het invoeren van bestandsnamen, XfceFilenameInput, is toegevoegd om ongeldige bestandsnamen snel te voorkomen en gedetaillerde terugkoppeling te geven over concrete problemen. De Generic Shortcut Editor widget wordt op dit moment alleen gebruikt binnen Thunar, Xfce4-terminal en Mousepad, maar andere componenten kunnen volgen.
</p>
}}
{{Point here|[[Image:Sway_Tree.png|48px|link=]]|'''Sway'''<br />
<p>
openSUSE Leap 15.5 bevat een Wayland compositor met tegels [[Sway]], dit is een drop-in vervanging voor de i3 window manager for X11. Het werkt met je bestaande i3 configuratie en ondersteunt de meeste van i3's featuren plus een paar extra's.
</p>
}}


{{Point here|[[Image:Icon-desktop.png|48px|link=]]|'''Onderwijs, onderzoek en gezondheidszorg'''<br />
<p>De Leap distributie supports the gezondheidszorg, wetenschaps, onderzoeks en ontwikkelings communities met pakketten zoals GNU Health, welke kunnen helpen bijdragen aan de operationele kant van een ziekenhuis en vitale patientgegevens kan opslaan. Ook bieden we QGIS, welke onderzoekers instaat stelt om georuimtelijke informatie te maken, bewerken, visualiseren, analyzeren on publiceren. Grafana and Prometheus are two new maintained packages that open up new possibilities for analytical experts. Grafana provides end users the ability to create interactive visual analytics. Feature-rich data-modeling packages: Graphite, Elastic and Prometheus give openSUSE users greater latitude to construct, compute and decipher data more intelligibly.</p>
}}

{{Point here|[[Image:Icon-wiki.png|48px|link=]]|'''Internationalization'''<br />
<p>This openSUSE release use [https://l10n.opensuse.org/ Weblate] to coordinate the translation of openSUSE into more than 50 languages. openSUSE’s Weblate interface enables everyone (from dedicated translators to casual contributors) to take part in the process and makes it possible to coordinate the translations of openSUSE with the ones for SUSE Linux Enterprise, boosting collaboration between community and enterprise.</p>
}}

[[Category:15.5]]
