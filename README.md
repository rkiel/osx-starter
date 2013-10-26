### Getting Started with OS X

Welcome to this quick start guide to setting up OS X for development.

### User Accounts

I like to have two user accounts on my Mac -- one for myself as a standard user and one for an administrator.
When you first power on your Mac, you create an initial user account, say `robert`.
That account is setup as an administrator.  Let's change that.

1. Login as `robert` and bring up the system preferences for Users & Groups.
2. Add a new user.  Select New Account: `Administration` with an Account Name: `admin`.
3. Logout and then login as `admin`.
4. Select the user `robert` and uncheck the box *Allow user to administer this computer*.

The rest of this guide will be done as the standard user and will specifically mention
when things need to be done as the administrator.

### System Preferences

Use the System Preferences to change some defaults.

* Security & Privacy
    * **General** tab -- enable `Require password`
* Trackpad
    * **Point & Click** tab -- enable both `Tap to click` and `Three finger drag` and disable `Secondary click`
    * **More Gestures** tab -- disable `App Expose` and enable all the rest
* Dock
    * decrease the **Size** and increase the **Magnification**
* Sharing
    * **Computer Name**: (dealers choice)
* Print & Scan
    * add your printer

### Safari

Change some of the default **Preferences**.

* General tab
    * **Safari opens with**: `All windows from last session`
    * **New windows open with**: `Empty Page`
    * **New tabs open with**: `Empty Page`
    * **Homepage**: (dealers choice)
* Advanced tab
    * enable `Show Develop menu in menu bar`

Change the default **View**.

* Customize Toolbar
    * drag the `Home` button up to the toobar

### Terminal

Change some of the default **Preferences**.

* Settings tab
    * Text tab
        * under **Profiles**, select `Novel` and click the `Default` button
        * change the **Font** to be `Menlo Regular 14 pt.`
    * Window tab
        * set **Columns** to be `128` and *Rows* to be `24`

### MacVim

Go to the [Google code project for MacVim](http://code.google.com/p/macvim/).

* Download the latest snapshot appropriate to your version of OS X.
* Once in **Downloads**, double-click to untar the file.
* Drag the `MacVim` binary from the **Downloads** folder into the **Applications** folder.
* Once in **Applications**, double-click `MacVim` to start it.
    * Authenicate it as a valid executable.
    * In the **Dock**, right click on `MacVim`
        * choose **Options* -> `Keep in Dock`

### Git

OS X comes with Git installed.

```unix
git --version
```

See [Git](http://git-scm.com) if you want to download and install the latest and greatest.

Set your global configuration settings.

```unix
git config --global user.name robert
git config --global user.email robert@robert.com
git config --global color.ui true
```

### SSH

Create your public/private key pair and choose a secure passphrase.

```unix
ssh-keygen -t rsa -C "robert@robert.com"
```

Verify you can read your private key

```unix
openssl rsa -noout -text -in ~/.ssh/id_rsa
```

Add your credentials to the authentication agent and Key Chain

```unix
ssh-add -K
```

### GitHub

Configure your GitHub account to recognize your new SSH credentials.

Copy your public key into the paste buffer.

```unix
cat ~/.ssh/id_rsa.pub | pbcopy
```

Go to your [GitHub account settings](https://github.com/settings/ssh).

* **SSH Keys** tab --  click the **Add SSH key** button
    * **Title**: `robert@computer name`
    * **Key**: paste

Confirm that you can access GitHub via SSH with this ping command.

```unix
ssh -T git@github.com
```

### Unix account

Download this quick start guide.

```unix
mkdir -p ~/GitHub/rkiel
cd ~/GitHub/rkiel
git clone https://github.com/rkiel/osx-starter.git
```

Setup for Bash

Use this for a basic profile.

```unix
ln -nfs ~/GitHub/rkiel/osx-starter/dotfiles/profile.basic ~/.profile
```

Setup for Vim

```unix
ln -nfs ~/GitHub/rkiel/osx-starter/dotfiles/vimrc ~/.vimrc
ln -nfs ~/GitHub/rkiel/osx-starter/dotfiles/vim   ~/.vim
mkdir ~/.backup
```

Setup for Ruby

```unix
ln -nfs ~/GitHub/rkiel/osx-starter/dotfiles/gemrc    ~/.gemrc
ln -nfs ~/GitHub/rkiel/osx-starter/dotfiles/rdebugrc ~/.rdebugrc
```

Setup for Git

```unix
ln -nfs ~/GitHub/rkiel/osx-starter/dotfiles/git-completion.bash ~/.git-completion.bash
```

### Sudo

Enable the standard user `robert` to use **sudo**.

Login as the administrator.

Edit the `sudoers`

```unix
sudo vi /private/etc/sudoers
```

Add `robert` to the User privilege specification

```unix
# User privilege specification
root    ALL=(ALL) ALL
%admin  ALL=(ALL) ALL
robert  ALL=(ALL) ALL
```


