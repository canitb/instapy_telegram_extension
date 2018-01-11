InstaPy Telegram Extension
--
### Available methods

- hello (print Hello World to your Telegram)
- sendtext("start") prints your <instagramuser: start> message to telegram (supports multiple instagram users).
- send_daily_report
  (send daily activity report (likes, comments, follows, unfollows))
- Supports error exceptions sent directly to telegram if anything fails.

### How to install

- git clone git@github.com:converge/instapy_telegram_extension.git
- move instapy_telegram_extension (folder) to InstaPy/extensions
- add ```from extensions.instapy_telegram_extension import InstaPyTelegramExtension```
to your config file (config.py / quickstart.py) file.

### Usage example

```python
from instapy import InstaPy
from extensions.instapy_telegram_extension import InstaPyTelegramExtension

insta_username  = ''
insta_password  = ''
telegam_api     = ''
telegam_user    = ''

# InstaPy login set
session = InstaPy(username=insta_username,password=insta_password,nogui=True)

# Telegram settings
telegram_ext = InstaPyTelegramExtension(telegam_api,telegam_user,session)

# set headless_browser=True if you want to run InstaPy on a server
try:
    #Do Login
    session.login()
    telegram_ext.sendtext("start");
    
    # settings
    session.set_do_follow(enabled=True, percentage=90, times=2)
    
    # actions
    session.like_by_tags(['food'], amount=1)
    
    # Telegram End Send Report
    telegram_ext.send_daily_report()
except Exception as error:
    #Print error to telegram
    telegram_ext.sendtext('{}: {}'.format("error", error))
finally:
    # end the bot session
    session.end()


```
### Hope this helps.
