= openSUSE Aeon =

{{Warning|Op 27 mei, de openSUSE MicroOS Desktop omgedoopt tot openSUSE Aeon, en de Plasma Desktop variant is hernoemd naar [[Portal:Kalpa|openSUSE Kalpa]] . Pas op voor het neerdalende stof terwijl we alles migreren van MicroOS Desktop naar de nieuwe namen.}}

{{Info|openSUSE Aeon biedt ALLEEN een minimaal basissysteem met een GNOME Desktop Omgeving en basis configuratie tools.
Alle applicaties, Browsers, Codecs, etc worden aangeboden via FlatPaks van FlatHub.}}

{{Point here|[[Image:Icon-warning.png|48px|link=]]|
openSUSE Aeon is nog steeds in het '''Release Candidate''' stadium. Houd hier rekening mee!
}}
----
== Voor wie is openSUSE Aeon? ==
Het is NIET voor iedereen. Je hoogst aanpasbare Tumbleweed & Leap Desktops zijn veilig en blijven de beste keuze voor diegenen die willen knutselen met hun Desktop.

Aeon zal perfect zijn voor gemakkelijk aangelegde ontwikkelaars, Die niets aan hun Desktop willen aanpassen alleen maar "hun ding doen", vooral wanneer ze containers ontwikkelen.

Het zal een hetzelfde publiek aantrekken die gewend zijn aan iOS, Chromebook of Anrdoid-achtige ervaringen waarbij het OS statisch, geautomatiseerd & betrouwbaar is en de Apps de belangrijke zaken zijn voor de gebruiker.

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

'''To reiterate: EVERYTHING should be done via Flatpaks or be installed in a Distrobox if a package is not available as a flatpak. Using transactional-update is strictly what you need for your host operating system to work (exotic drivers, specialized vpn services).'''

Note: Distrobox is shipped by default w/ Aeon. It allows users to install any linux distribution inside your terminal. For those who want to run GUI apps via a Distrobox can do so with a special export command so that apps feel more native and integrated with the system. Check out the [[https://en.opensuse.org/Portal:Aeon#DistroBox Distrobox section]] to learn more about this convenient way to launch distrobox based apps from your host menu launcher. 

==== An Introduction to transactional-update ====

openSUSE Aeon does '''not''' use ''zypper'' like openSUSE Tumbleweed or openSUSE Leap to install RPM packages and use them directly. openSUSE Aeon uses '''transactional-update''' with zypper under the hood.

Most of the time, you should not need to use any of these commands interactively, as Aeon has automatic system updates via a the ''transactional-update.service'' systemd service.

==== transactional-update - Example Commands ==== 

Commands for transactional-update are listed below. NOTE: Remember to reboot after the command is finished to see the changes!
* ''sudo transactional-update pkg install package_name'' install a rpm package
* ''sudo transactional-update pkg remove package_name'' remove an rpm package
* ''sudo transactional-update dup'' perform a system upgrade to the next release
* ''sudo transactional-update shell'' open a shell of the next snapshot (you can use zypper commands there). '''This should only be used for debugging purposes'''. Any bug report that can only be reproduced by using transactional-update shell is almost certain to be closed as WONTFIX.
* ''sudo transactional-update rollback snapshot_number'' roll the system back to the numbered snapshot. Use 'last' instead of the snapshot number to roll back to the last working snapshot. '''Do not use snapper for rollbacks.'''

==== transactional-update - Automatic Update ====

By default ''transactional-update.timer'' handles automated system updates. This is set to ''daily'' which means that the task will be executed each day at 00:00:00.

In the event this might be at a time when the computer is off, as the timer is set to persistance=true, then the update will then take place the first chance it can. 

Some of the reasons why it may not be able to trigger an update could be: 

* the computer was off
* the internet connection was disturbed - at time it is scheduled to.

This should not cause issues due to the way ''transactional-update'' works since the new packages are installed on a new snapshot for which to take effect you must reboot.

To track if ''transactional-update'' is able to upgrade, and run correctly you can use ''journalctl'':

  $ sudo journalctl -u transactional-update.service 

You can also use ''journalctl'' with the ''-f'' flag to tail the logs in real time.

==== transactional-update - --Final Words About Snapshots and Boot Behavior ====
By default, each ''transactional-update'' command produces a seperate, self-contained, snapshot that includes the changes requested by the ''transactional-update'' command.

This snapshot is '''BASED ON THE LAST KNOWN GOOD/BOOTED SNAPSHOT'''. The last of the snapshots produced by multiple ''transactional-update'' commands then takes effect when rebooting.

In other words ''sudo transactional-update pkg install $pkg1'' followed by ''sudo transactional-update pkg install $pkg2'' and then rebooting results in a system that has $pkg2 installed, but NOT $pkg1.

This is the expected, and sensible default behaviour - Aeon always wants to move from the last known good/booted snapshot to it's new state in the smallest, least disruptive way possible.

This is especially sensible when you think the default/expected behaviour is that Aeon updates itself automatically and most users should not be using ''transactional-update'' interactively at all. With ''transactional-update dup'' happening regularly in the background automatically, Aeon wants to make sure it's updating only to the latest clean system update state, not some weird hybrid of previous unbooted, unchecked, intermediate ''transactional-update dup'' that never got booted.

However, when ignoring this best practice and using ''transactional-update'' interactively, there may be times where you wish to run ''transactional-update'' against an existing unbooted, unknown-if-good snapshot.

For this use ''transactional-update --continue''

Example:

''sudo transactional-update pkg install $pkg1'' followed by ''sudo transactional-update --continue pkg install $pkg2'' will install $pkg1, then $pkg2 in the same snapshot that included $pkg1, marking that combined snapshot as the next boot target.

If problems occur however, there is no additional complexity figuring out whether it was $pkg1 or $pkg2 that broke anything, as users will need to rollback to the snapshot before $pkg1 was installed to return to the last known good state.
----

== GNOME Software + Flathub Integration ==
Gnome is currently in a '''RC''' stage.

* At first boot flatpaks are enabled and some flatpaks are installed by default (Mozilla Firefox, Text Editor, Gnome Calculator and Extension Manager).

* After the first boot script finishes you can open Gnome Software to install more software from flathub. 

----

== DistroBox ==

''Distrobox'' can be used like toolbox (which is included on the server version of MicroOS by default), but has some other advantages for desktop usage.
Please refer to https://github.com/89luca89/distrobox for all options.

[[Distrobox|For more documentation, see the Distrobox Page]]
----

== Troubleshooting ==

This section describes known issues on openSUSE Aeon and their solutions.

==== Set hostname ====

Set your hostname with the following command, as currently it doesn't work from Gnome Settings yet:

   # sudo hostnamectl set-hostname <new name>

Reboot and hostname change will take effect. 

==== Adjust transactional-update.timer ====

Depending on your daily use case, the Timer may not trigger the automatic update process successfully even with persistent=true because it adds a randomized delay at each boot with ''RandomizedDelaySec'' 

If you want automatic ''daily'' updates to your system, you may find that you need to adjust that delay mentioned. 

Edit transactional-update.timer:

   # sudo systemctl edit transactional-update.timer

Add the following lines to create a override.conf (located in /etc/systemd/system/transactional-update.timer.d/override.conf)

   [Timer]
   RandomizedDelaySec=5m

The example above is for a randomized delay of max. 5 minutes. (Default value is 2h)

Change the time to your use case. You can use [https://www.freedesktop.org/software/systemd/man/systemd.time.html this as reference].

==== Steam Proton, Bottles, WINE, Lutris, Android Studio emulator not working from flatpaks ====

If you run into issues using WINE, and WINE based programs in flatpaks, it is likely due to an SELinux issue, and can be checked by running:

   # sudo getsebool selinuxuser_execmod

For Android Studio:

   # sudo getsebool selinuxuser_execstack

If that returns 'selinuxuser_execmod --> disabled' and 'selinuxuser_execstack --> disabled' you will need to enable it.  This can be done temporarily (resets on next boot)

For WINE:
   # sudo setsebool selinuxuser_execmod 1

For Android Studio:
   # sudo setsebool selinuxuser_execstack 1

Or can be set Persistent:

   # sudo setsebool -P selinuxuser_execmod 1
   # sudo setsebool -P selinuxuser_execstack 1

The openSUSE Security team is reviewing these default policies, and you are enabling this at your own risk.  See https://bugzilla.opensuse.org/show_bug.cgi?id=1206292 & https://bugzilla.opensuse.org/show_bug.cgi?id=1206789 for further information.

----

== Reporting Bugs ==

Please use the following link for reporting bugs: [https://bugzilla.opensuse.org/enter_bug.cgi?product=openSUSE+Aeon&format=guided Report a bug for openSUSE Aeon]

Please see [[openSUSE:Submitting_bug_reports|Submitting Bug Reports]] for more information on how best to file a bug

== Place for questions ==
As openSUSE Aeon has various places discuss the project

* ''Telegram'': https://t.me/openSUSE_Aeon
* ''Matrix'': https://matrix.to/#/#aeon:opensuse.org
* ''Discord'': https://discord.gg/opensuse #aeon-kalpa channel

All these channels are bridged together via Matrix, so sending your comments in one, will be seen in the other two.


[[Category:Aeon]]
[[Category:Kalpa]]
