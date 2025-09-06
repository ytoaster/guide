
# Ubuntu 16.04 LTS
A guide to making Ubuntu 16.04 usable again. 
Now I know that Ubuntu Unity exists, but it's too buggy for my liking. Also Ubuntu 16.04 looks cooler.
 ## Upgrading
 Upgrade EVERYTHING (of course except to 18.04 LTS)
 If the Update Manager windows doesnt open automatically, in the terminal,## run 
`sudo apt update && sudo apt upgrade`
 
### Firefox
You might notice, that even after upgrading everything your Firefox version is 88. 
The way Canonical wants you to have an updated Firefox, involves paying for Ubuntu Pro. So instead of paying a company to keep using an old OS, try this:

Adding the official Firefox repository to Ubuntu

 1. Create a directory to store APT repository keys if it doesn't exist:
`sudo install -d -m 0755 /etc/apt/keyrings`
2. Import the Mozilla APT repo signing key:
`wget -q https://packages.mozilla.org/apt/repo-signing-key.gpg -O- | sudo tee /etc/apt/keyrings/packages.mozilla.org.asc > /dev/null`
3. The fingerprint should be **35BAA0B33E9EB396F59CA838C0BA5CE6DC6315A3**. You may check it with the following command:
`gpg -n -q --import --import-options import-show /etc/apt/keyrings/packages.mozilla.org.asc | awk '/pub/{getline; gsub(/^ +| +$/,""); if($0 == "35BAA0B33E9EB396F59CA838C0BA5CE6DC6315A3") print "\nThe key fingerprint matches ("$0").\n"; else print "\nVerification failed: the fingerprint ("$0") does not match the expected one.\n"}'` 
4. Add the Mozilla APT repo to your sources.list:
 `echo "deb [signed-by=/etc/apt/keyrings/packages.mozilla.org.asc] https://packages.mozilla.org/apt mozilla main" | sudo tee -a /etc/apt/sources.list.d/mozilla.list > /dev/null`
 5. Configure APT to prioritize packages from the Mozilla repo:
`echo '`
`Package: *`
`Pin: origin packages.mozilla.org`
`Pin-Priority: 1000`
`' | sudo tee /etc/apt/preferences.d/mozilla`
5. Update your package list, and install _firefox_ / _firefox-esr_ / _firefox-beta_ / _firefox-devedition_ / _firefox-nightly_. 
I'm going to install Firefox Developer Edition, because the installed Firefox version has more integration to Ubuntu (like unity menu bar button support), and on newer versions not provided by Canonical, Mozilla removed it (for some unknown reason).
`sudo apt-get update && sudo apt-get install firefox` /
`sudo apt-get update && sudo apt-get install firefox-devedition`
 
> Written with [StackEdit](https://stackedit.io/).

>Firefox update guide peovided by Mozilla, check [here](https://support.mozilla.org/en-US/kb/install-firefox-linux).


