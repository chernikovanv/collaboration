# What is it:question:

The Skillpub is **technology and collaboration tool** for personal or team **tasks automation and sharing** automated tasks within team or entire organization through channels like Slack, Telegram, and others. Task automation and sharing boost :rocket: productivity, mobility and engagement, provide base for **building a Virtual Assistant** for you, your team or an organization. With every automated and shared task people are getting more and more free to complete creative and responsible tasks :smirk: while the Virtual Assistant handle routine tasks :man_technologist:.    

#  Core Technology :gem:

The technology is to take **any script writed in high level language** (Python), analize its inputs, outputs, images or graphs display, other interactions with user and **build connectors to this script from channles like Slack, Telegram, and others**. Imagine that you described your skill as a script and without changing anything gave it to **software robot**. And from that moment it is his skill, you and your colugues can ask him any time to run this skill and give a results.
As a script author you don't think about how to connect with different channels, how to control access, how to monitor that script works fine when colegues run it, how to save logs, how to balance load if there are too much coleagues run this scripts and so on, Skillpub does all of this stuff, author don't even think about what is that software robot, how it works, author do nothing to prepare script for sharing, Skillpub will understand everything by itself. Author **just drop script to Skillpub platform and tell to Skillpub which colleagues have the right to run a script**.

# Pricing 

The Skillpub is free to use and unlimited in functionality :tada: for all channels except Slack, **for Slack - :keycap_ten: users are free**, for more users need to buy license on www.skillpub.org.

# Use Cases


# Quickstart

The Skillpub is distributed as a **Python package** on the Python Package Index (PyPI) and hosted on your server. 
The server requarements are 
  Linux machine (CentOS, Ubuntu, Debian, ... )
  Python 3.6 and above with pip

If you are familiar with Python and pip you can just run the line bellow otherwise you need to spend some time googling how to install **Python 3 and pip on Linux server**.

```
sudo pip install skillpub
```

or, more reliable in some cases

```
sudo python3 -m pip install skillpub
```

Then create a folder where you will store shared scripts (we will imagen that we are building *Virtual Assstant for NASA team* and name this folder *nasahelper*, you choose your folder name)

```
mkdir nasahelper
```

Navigate to this folder

```
cd nasahelper
```

And run Skillpub

```
skillpub
```

It will create config file and folder for shared scripts (*skills*).
Check it out by command `ls` and then `cat config.json`

Config file will looks like 

```json
{
    "users": {
        "bob": {"channels": {"slack" : "bob", "telegram": 1001}},
        "alice": {"channels": {"slack" : "alice" , "telegram": 1002}}
    },

    "publishers": ["bob"],

    "channels": {
        "slack": {"token": "xoxb-XXXXXXXXXXX-XXXXXXXXXXXX-XXXXXXXXXXXXXXXXXXXXXX"},
        "telegram": {"token": "XXXXXXXXX:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"}
    },

    "license": "free"
}
```
**Slack token** is **"Bot User OAuth Access Token"** in terms of Slack documentation. To get it do the steps bellow

- Create **Slack App** - https://api.slack.com/apps/new. 
- Create a **Bot User** for this App:
  - Head to your [app's settings page](https://api.slack.com/apps) and click the **Bot Users** feature in the navigation menu.
  - You'll be presented with a button marked **Add a Bot User**, and when you click on it, you'll see a screen where you can configure your app's bot user.
  - The important here - **Display name**. We choose *NasaHelper*. You choose your.
  - Once you've completed these fields, click the **Add Bot User** button and then **Save Changes**.
- Install the **App to a workspace**:
  - On your [app's settings page](https://api.slack.com/apps) again, click the **OAuth & Permissions** settings item in the navigation menu.
  - On this page, click a button marked **Install App to your Workspace**.
  - You'll see a permissions authorization page, where you should click **Authorize** and then you will see your **"Bot User OAuth Access Token"**.

**Telegram token** is the token to access the HTTPS Telegram API. 
You can get it from **Telegram bot [BotFather](https://telegram.me/botfather)**. Read more [here](https://core.telegram.org/bots).

So, now you can put your token into config file, keep in config channels you have token for.

As you can guess Users part on config have user name and identificators of this user in different channels.
For Slack this identificator is Slack user name. For Telegram it's user_id. 

Publishers are users who have access to Skillpub Web Application to work with scripts (it's well known [JupyterLab](https://jupyterlab.readthedocs.io)).

So, supposing our NASA team have 5 users and only Slack channel, config can be like:

```js
{
    "users": {
        "james": {"channels": {"slack" : "james"}},
        "john": {"channels": {"slack" : "john"}},
        "mary": {"channels": {"slack" : "mary"}},
        "robert": {"channels": {"slack" : "robert"}},
        "patricia": {"channels": {"slack" : "patricia"}}
    },

    "publishers": ["james","john","mary"],

    "channels": {
        "slack": {"token": "xoxb-qwertyuiopa-123456789012-asdfghjklzxcvbnm123456"}
    },

    "license": "free"
}
```
Config is ready, RUN ```skillpub```.

Go to your Slack messenger, left menu, press + in section Apps or Direct Messages, find your bot (our is NasaHelper) and open chat whith it. It should be online (little circle next to name should be green).

Text to your bot ```hello```, you'll see the answer.

Now go to folder skill (as you remember it was created when we first time run Skillpub).
You will see hello.py script, open it, you'll see the code, play whith it. Skillpub will apply changes automatically when you save file.

That is all for Quickstart. Just a few poins to add:
 - Pyhton file in folder skills can be run from channel (Slack in our example)
 - file name - is command to run
 - first line in file in triple quote - is skill help, text to your bot ```help``` to see it
 - text to your bot ```publisher```, or just ```pub``` to get a link to Skillpub Web Application ([JupyterLab](https://jupyterlab.readthedocs.io)), check it out. Remember you must be in publishers list in config.  
 - to manage access to scripts put them to subfolders in folder skills, and add subfolder name to users groups like this ```"james": {"groups":["subfolder 1","subfolder 2"], "channels": {"slack" : "james"}}```
 
For more details and examples go to our Tutorial. Thanks for attention, see you.
