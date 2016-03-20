# Deploy on Heroku

This is a simple example of getting the code running on heroku using mongodb as its database.
Based on [https://github.com/chadn/heroku-sails]

## Setup

Create a new project:

1. Install sails globally `sudo npm install -g sails`
2. Create sails folder `sails new sailsjs_example`
3. Add to git: `cd sailsjs_example && git init && git add . && git commit`

or clone this one:
1. git clone https://github.com/garcianavalon/sailsjs_example.git

If you have not yet, create heroku account and install [heroku 
toolbelt](https://toolbelt.heroku.com/)

Then create a heroku app.  I created `sailsjs_example` in the following example:

	$ heroku apps:create sailsjs_example
	Creating sailsjs_example... done, region is us
	http://sailsjs_example.herokuapp.com/ | git@heroku.com:sailsjs_example.git
	Git remote heroku added

Add mongo db 

	$ heroku addons:create mongolab:sandbox
	Creating mongolab-concave-45159... done, (free)
	Adding mongolab-concave-45159 to sailsjsexample... done
	Setting MONGOLAB_URI and restarting sailsjsexample... done, v3
	Welcome to mLab.  Your new subscription is being created and will be available shortly.  Please consult the mLab Add-on Admin UI to check on its progress.
	Use `heroku addons:docs mongolab` to view documentation.


Optionally set the api key. If you don't, key check will be skipped and anyone can created/edit.
Note that we what you set here is what is sent in URL.  For more on this authentication,
[Read lib/authenKey.js](lib/authenKey.js)

	$ heroku config:set APPROVED_API_KEY=APIKEY
	Setting config vars and restarting sailsjs_example... done
	APPROVED_API_KEY: APIKEY


Optionally add papertrail, lets you view logs from a browser:

	$ heroku addons:add papertrail
	Adding papertrail on sailsjs_example... done, v4 (free)
	Welcome to Papertrail. Questions and ideas are welcome. Happy logging!
	Use `heroku addons:docs papertrail` to view documentation.

Deploy!

	$ git push heroku master

Now view your new app in your browser.
