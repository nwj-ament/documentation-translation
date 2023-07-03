{{Point here|[[Image:Icon-info.png|48px|link=]]|
'''Voor wie is Tumbleweed bedoeld?'''

Elke gebruiker die nieuwere pakketten wenst dan diegenen die in beschikbaar zijn in de [[Portal:Leap|openSUSE Leap]] repositories.  Dit omvat onder andere een geüpdate Linux Kernel, SAMBA, git, desktops, office applicaties en vele andere pakketten

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

{{Point here|[[Image:Icon-warning.png|48px|link=]]|
'''Rollende release betekent geen updates, welke urgente patches upgrades'''

Wanneer je Tumbleweed update, kun je YaST of de systeem update applet gebruiken, net zoals in Leap.

Om Tumbleweed up-to-date te houden bij met het laatste snapshot door middel van zypper, gebruik dan het volgende comando '''als root''' (idealiter in een screen of tmux sessie):

<pre>zypper dup</pre>

Let op de afstemming met updates, zeker wanneer er sprake is van meerdere opslagruimtes.  Zie bijvoorbeeld [https://lists.opensuse.org/opensuse-factory/2016-12/msg00326.html recent discussion about using zypper dup versus zypper up] en [https://forums.opensuse.org/showthread.php/531333-Zypper-dup-priorities zypper dup priorities].
}}

{{Point here|[[Image:Icon-info.png|48px|link=]]|
'''Multimedia Codecs'''

In verband met licentie issues kan openSUSE bepaalde media codecs, zoals H.264 niet meeleveren. Zonder deze codecs kunnen video's van bepaalde websites, muziek bestanden, geluiden enz. niet afspelen. Fortunately, the [http://packman.links2linux.org/ Packman] repository provides these codecs (along with many other things) for openSUSE. More details about Packman can be found at [[Additional_package_repositories#Packman|additional package repositories]].

To add only the Packman Essentials repository (provides codecs, audio, and video player applications) and install missing codecs, run the following commands '''as root''':

<pre>zypper ar -cfp 999 http://ftp.gwdg.de/pub/linux/misc/packman/suse/\
openSUSE_Tumbleweed/Essentials packman-essentials
zypper dup --from packman-essentials --allow-vendor-change</pre>

After installing the codecs from Packman, [https://youtube.com/html5 YouTube's HTML5 Video Player] test may be ran to see if H.264 is working properly in a browser.

To add the entire Packman repository and install missing codecs, you can either start the YaST repository manager, click "Add", select "Community repositories", and check "Packman"; or, on the console, run the following commands '''as root''':

<pre>zypper ar -cfp 999 http://ftp.gwdg.de/pub/linux/misc/packman/suse/\
openSUSE_Tumbleweed/ packman
zypper dup --from packman --allow-vendor-change</pre>

}}

{{Point here|[[Image:Icon-warning.png|48px|link=]]|
'''Third Party Drivers'''

Due to the fast pace of kernel upgrades on Tumbleweed, 3rd party kernel driver modules may not be fast enough to catch up with the latest kernel version. In the unlikely case that your kernel driver module does not work on Tumbleweed, please consider using openSUSE Leap instead.

'''NVidia'''’s proprietary driver generally works very well with Tumbleweed.

NVidia proprietary drivers for GeForce 400 series and newer GPUs can be easily installed in Tumbleweed using the following commands '''as root''':

<pre>zypper ar -f https://download.nvidia.com/opensuse/tumbleweed nvidia
zypper inr</pre>

In extremely rare cases, for example if you require a beta version of the driver, you can also manually install the driver. Read [[SDB:NVIDIA the hard way|NVidia – The hard way]] for details. Please remember to also re-compile and re-install these third party drivers with every kernel upgrade on Tumbleweed.

Alternatively, the [https://software.opensuse.org/package/dkms-nvidia dkms-nvidia] openSUSE Build Service repository may be used.  This repository provides NVIDIA drivers that work with dkms (NVIDIA's modules will be automatically recompiled for each new kernel update).  It also contains a variety of NVIDIA driver versions for use with cards that are not supported with or do not behave well with the latest drivers.  To make use of this repository, simply click the 1 Click Install link for the driver version you wish to install [https://software.opensuse.org/package/dkms-nvidia here] or run the following commands '''as root''' for the latest NVIDIA driver from dkms-nvidia:

<pre>zypper ar -f https://download.opensuse.org/\
repositories/home:/Bumblebee-Project:/nVidia:/latest/\
openSUSE_Tumbleweed/home:Bumblebee-Project:nVidia:latest.repo
zypper in dkms-nvidia</pre>

Please note that the dkms-nvidia repository is '''not officially supported''' and anyone who wishes to use it will most likely be on their own for troubleshooting problems.

As for '''AMD''', [[SDB:AMDGPU-PRO|AMDGPU-PRO]] is not supported for Tumbleweed. Tumbleweed comes with a Radeon driver installed out of the box that is usually the superior choice anyway.
}}

{{Point here|[[Image:Icon-user.png|48px|link=]]|
'''How can I contribute?'''

* You can test the Tumbleweed distribution and give feedback, share experience and participate in the development discussions. To do so, send your mail to the list address, [mailto:opensuse-factory@opensuse.org opensuse-factory@opensuse.org].
* If you encounter trouble with your Tumbleweed instance you can report issues to [https://bugzilla.opensuse.org openSUSE bugzilla].
* If you are a packager, you can submit new packages to the [[Portal:Factory|openSUSE:Factory]] project.
}}
