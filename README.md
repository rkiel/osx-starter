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

### Git

OS X comes with Git installed.  See [Git](http://git-scm.com) if you want to download and install the latest and greatest.

User Terminal to setup you global configuration settings.

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

Go to your [GitHub account settings](https://github.com/settings/profile).

* **SSH Keys** tab --  click the **Add SSH key** button
    * **Title**: `robert@computer name`
    * **Key**: paste


