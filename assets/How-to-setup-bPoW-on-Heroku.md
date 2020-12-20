How to setup bPoW in Heroku for Free BAN (Cloud Mining bPoW)

Requirements:
A Heroku.com account (free)
A computer

1. Prepare Heroku

Follow the instructions at https://devcenter.heroku.com/articles/getting-started-with-python, up until “View Logs”

2. Add Heroku Buildpacks

```
heroku buildpacks:add heroku/python
heroku buildpacks:add heroku-community/apt
```

3. Add the bPoW source code

Download https://drive.google.com/file/d/1BA34O62vxDkiOvOGjVjx-6KT9Jm4BfXs/view and extract it in the Heroku app folder. This contains the bPoW source code plus some Heroku files needed.

4. Push the code to Heroku

Run: ```git add * && git commit -m “commit” && git push```

5. Add a free worker dyno

Run ```heroku ps:scale worker=1```

6. Verify everything is working

Run ```heroku ps``` to see your worker info, and ```heroku logs -t``` to see the logs.

7. Make it yours

Now that everything is working fine, edit start.sh and replace my BAN address with yours (it’s the first line, keep the “BAN_ADDR=” part though). Follow step 4 again to push the changes to Heroku.

8. Optional: Run 24/7

Free Heroku accounts come with 550 free Dyno hours per month. There’s about 750 hours in a month. That’s a problem. If Free Dynos run out of hours, they just stop working until the hours are reset. However, if you add a credit card to your account, Heroku will give you enough extra hours to run 24/7 all month, and then some. (Don’t worry, even if you run out of free hours, Free Dynos will NEVER charge you, they’ll just stop working.)

Great! Now you should be earning small amounts of BAN passively, for free, in the cloud.
Don’t expect to get tons and tons of BAN, Heroku is pretty powerful but it doesn’t have GPUs.

Anyway, I hope this guide was helpful to you! Go bananas. - Randomblock1#8622

_banano: the only crypto with any ~~nutritional~~ value_
