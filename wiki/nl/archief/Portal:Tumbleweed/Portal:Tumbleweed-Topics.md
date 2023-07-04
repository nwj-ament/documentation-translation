{{Point here|[[Image:Icon-info.png|48px|link=]]|
'''Voor wie is Tumbleweed bedoeld?'''

Elke gebruiker die nieuwere pakketten wenst dan diegenen die in beschikbaar zijn in de [[Portal:Leap|openSUSE Leap]] opslagruimten.  Dit omvat onder andere een geüpdate Linux Kernel, SAMBA, git, desktops, office applicaties en vele andere pakketten.

Tumbleweed zal voornamelijk bij Power Users, Software Ontwikkelaars (zij hebben de laatste software stacks en IDEs nodig) en openSUSE bijdragers (zij hebben een betrouwbaar platform nodig dat zo dicht als mogelijk tegen [[Portal:Factory|openSUSE Factory]] aan zit maar wel bruikbaar is).

Doordat de Linux kernel vaak wordt geupdatet, is het verstandig voor gebruikers die afhankelijk zijn van 3e partij kernel driver modules (inclusief grafische drivers) om Tumbleweed niet te gebruiken tenzij men bekend is met het zelf updaten van deze drivers vanaf de broncode of wanneer ze ondersteunde hardware hebben. Voor meer details kijk in de paragraaf "Derde partij drivers" hieronder.
}}
{{Point here|[[Image:Icon-info.png|48px|link=]]|
'''Wie zou openSUSE Leap moeten gebruiken in plaats van Tumbleweed?'''

Hoewel we alles doen om zoveel mogelijk modules te beschikbaar te maken, kunnen we niet garanderen dat ze allemaal beschikbaar zijn in openSUSE Tumbleweed. Denk hierbij aan modules van VMware of VirtualBox. Packman Tumbleweed Essential opslagruimte probeert ze te leveren maar er is geen garantie dat het altijd lukt omdat er incompatibiliteiten kunnen zijn met de snel voortschrijdende Linux kernel. De problemen met propietary grafische drivers zijn hiermee vergelijkbaar en er is geen garantie dat ze morgen no werken ook al werken ze vandaag. Als je niet weet hoe je aanvullende kernel modules compileert en wil je dit ook niet leren of wilt u een kritisch oog houden op wat er geüpdatet wordt, dan is het niet raadzaam om Tumbleweed te installeren.
}}

{{Point here|[[Image:Icon-usage.png|48px|link=]]|
'''Hoe Tumbleweed te proberen?'''

Om te beginnen met Tumbleweed volg de [[openSUSE:Tumbleweed_installatie|Tumbleweed Installatie Instructies]]

Volg de [http://lists.opensuse.org/opensuse-factory/ opensuse-factory] mailing lijst om bericht te krijgen wanneer er updates zijn. Nieuwe snapshots worden gereleased zo vaak als dat ze klaar zijn en door de automatische QA (kwaliteitscontrole) komt. Dit kan zo vaak zijn als dagelijk maar soms ook eens in de paar weken, zeker wanneer er grote wijzigingen worden geïntegreerd.  
}}

{{Point |[[Image:Icon-warning.png|48px|link=]]|
'''Rollende release betekent geen updates, welke urgente patches upgrades'''

Wanneer je Tumbleweed update, kun je YaST of de systeem update applet gebruiken, net zoals in Leap.

Om Tumbleweed up-to-date te houden bij met het laatste snapshot door middel van zypper, gebruik dan het volgende comando '''als root''' (idealiter in een screen of tmux sessie):

<pre>zypper dup</pre>

Let op de afstemming met updates, zeker wanneer er sprake is van meerdere opslagruimtes.  Zie bijvoorbeeld [https://lists.opensuse.org/opensuse-factory/2016-12/msg00326.html recent discussion about using zypper dup versus zypper up] en [https://forums.opensuse.org/showthread.php/531333-Zypper-dup-priorities zypper dup priorities].
}}

{{Point |[[Image:Icon-info.png|48px|link=]]|
'''Multimedia Codecs'''

In verband met licentie issues kan openSUSE bepaalde media codecs, zoals H.264 niet meeleveren. Zonder deze codecs kunnen video's van bepaalde websites, muziek bestanden, geluiden enz. niet afspelen. Gelukkig biedt de [http://packman.links2linux.org/ Packman] opslagruimte deze codecs (samen met een hoop andere pakketten) voor openSUSE. Meer details over Packman kun je vinden bij [[Additional_package_repositories#Packman|additionele pakket opslagruimtes]].

Om aleen de Packman Essentials opslagruimte (voorziet in codecs, audio en video speler applicaties) en de missende codecs te installeren voer het volgende commando '''als root''' uit:

<pre>zypper ar -cfp 999 http://ftp.gwdg.de/pub/linux/misc/packman/suse/\
openSUSE_Tumbleweed/Essentials packman-essentials
zypper dup --from packman-essentials --allow-vendor-change</pre>

Na het installeren van de codecs uit Packman, kan via [https://youtube.com/html5 YouTube's HTML5 Video Player] getest worden of H.264 goed werkt in een browser.

Om de volledige Packman opslagruimte toe te voegen en missende codecs te installeren, doe dit of via de YaST opslagruimten manager, klik "Toevoegen", selecteer "Community opslagruimtes", en tik "Packman"; of voer in de console het volgende commando '''als root''' uit:

<pre>zypper ar -cfp 999 http://ftp.gwdg.de/pub/linux/misc/packman/suse/\
openSUSE_Tumbleweed/ packman
zypper dup --from packman --allow-vendor-change</pre>

}}

{{Point here|[[Image:Icon-warning.png|48px|link=]]|
'''Drivers van derde partijen'''

Doordat de kernel upgrades van Tumbleweed snel op elkaar volgen kan het gebeurden dat bepaalde derde partij driver modules niet snel genoeg zijn bijgewerkt voor de nieuwste kernel versie. In het onwaarschijnlijke geval dat je kernel driver module niet werkt in Tumbleweed, kies in dat geval voor openSUSE Leap.

'''NVidia'''’s proprietary driver werkt in zijn algemeenheid zeer goed met Tumbleweed.

NVidia proprietary drivers voor GeForce 400 series and nieuwere GPUs kunnen eenvoudig worden geïnstalleerd in Tumbleweed door het volgende commando's '''als root''' te gebruiken:

<pre>zypper ar -f https://download.nvidia.com/opensuse/tumbleweed nvidia
zypper inr</pre>

In extreme gevallen, bijvoorbeeld wanneer je een beta versie avn een driver nodig hebt, kun je deze ook handmatig installeren. Lees [[SDB:NVIDIA the hard way|NVidia – The hard way]] voor details. Denk eraan om het hercompileren en herinstalleren van deze derde partij drivers bij elke kernel upgrade van Tumbleweed.

Als alternatief de [https://software.opensuse.org/package/dkms-nvidia dkms-nvidia] openSUSE Build Service opslagruimte may be used.  Deze opslagruimte bevats NVIDIA drivers die werken met dkms (NVIDIA's modules worde automatisch opnieuw gecompileerd bij elke nieuwe kernel update).  Het bevat tevens een aantal NVIDIA driver versions voor gebruik met kaarten die niet ondersteund worden of niet goed werken met de laatste drivers. Om gebruik te maken van deze opslagruimte, klik eenvoudig op de 1-klik-installeer link voor de driver versie die je wenst te installeren [https://software.opensuse.org/package/dkms-nvidia hier] of voer de volgende commando's '''als root''' uit voor de laatste NVIDIA drivers van dkms-nvidia:

<pre>zypper ar -f https://download.opensuse.org/\
repositories/home:/Bumblebee-Project:/nVidia:/latest/\
openSUSE_Tumbleweed/home:Bumblebee-Project:nVidia:latest.repo
zypper in dkms-nvidia</pre>

Houd er rekening mee dat de dkms-nvidia opslagruimte '''not officieel ondersteund wordt''' en iedereen wie dat wil gebruiken is waarschijnlijk aangewezen op het eigen onderzoek met het oplossen van problemen.

Voor '''AMD''', [[SDB:AMDGPU-PRO|AMDGPU-PRO]] geldt dat deze niet is ondersteund voor Tumbleweed. Tumbleweed is standaard uitgerust met een Radeon driver die sowieso vaak de betere keus is.
}}

{{Point here|[[Image:Icon-user.png|48px|link=]]|
'''Hoe kan ik bijdragen?'''

* Je kunt de Tumbleweed distributie testen en feedback geven, ervaring delen en deelnemen aan discussies aangaande de ontwikkeling. Om deel te nemen stuur je een e-mail naar het mailinglist adres [mailto:opensuse-factory@opensuse.org opensuse-factory@opensuse.org].
* Als je problemen ervaart met je Tumbleweed installatie kun je bugs rapporteren op de [https://bugzilla.opensuse.org openSUSE bugzilla].
* Wanneer je een packager bent, kun je nieuwe pakketten indienen bij het [[Portal:Factory|openSUSE:Factory]] project.
}}
