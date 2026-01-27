# Debian Buster
A guide to making Debian 10 usable again. 
## Upgrading or installing software
If you would install Debian 10 in 2026 (or later in the future, who knows) you would notice, that you cannot install anything. That is because Buster's software repositories have been moved to archive.debian.org.

So, open your terminal, and run a text editor with root, you could type:
- For XFCE:  `sudo mousepad`
- For Gnome: `sudo gedit`
- For KDE: `sudo kwrite`
- For others: `sudo nano`
With your text editor, open `/etc/apt/sources.list`, and anywhere you like, type these 3 lines:
- `deb http://archive.debian.org/debian/ buster main contrib non-free`
- `deb http://archive.debian.org/debian-security/ buster/updates main contrib non-free`
- `deb http://archive.debian.org/debian/ buster-backports main contrib non-free`

Now, run `sudo apt update`.

_Note: You may need to use the `-o Acquire::Check-Valid-Until=false` option with `apt-get update` if the system complains about expired signatures._

Now that you've added the repos to your Debian install feel free to do a `sudo apt upgrade` or whatever. Good luck.
> Written with [StackEdit](https://stackedit.io/).
