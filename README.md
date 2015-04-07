This is a django 1.8 project with basic functionality like:

 * registration
 * social authentication
 * debug toolbar


I use this as starter project for my sites. 


Example usage
=============

    $ virtualenv mysite-env --no-site-packages
    $ source mysite-env/bin/activate
    (mysite-env)$ pip install django==1.8
    (mysite-env)$ django-admin.py startproject --template=https://github.com/kl4us/django_basement/zipball/master mysite
    (mysite-env)$ cd mysite
    (mysite-env)$ pip install -r requirements.txt
    (mysite-env)$ python manage.py migrate
    (mysite-env)$ python manage.py runserver

For social authentication and debug toolbar you need to create a file named local_settings.py in the same folder of your settings file. This file will have the following content:

	from settings import MIDDLEWARE_CLASSES, INSTALLED_APPS

	DEBUG = True
	TEMPLATE_DEBUG = DEBUG


	if DEBUG:

	    # Email backend
	    EMAIL_BACKEND = "django.core.mail.backends.console.EmailBackend"

	    # Debug Toolbar
	    MIDDLEWARE_CLASSES += (
	        'debug_toolbar.middleware.DebugToolbarMiddleware',
	    )    
	    INSTALLED_APPS += (
	        'debug_toolbar',
	    )
	    INTERNAL_IPS = ('127.0.0.1',)

	    DEBUG_TOOLBAR_PANELS = [
	        'debug_toolbar.panels.versions.VersionsPanel',
	        'debug_toolbar.panels.timer.TimerPanel',
	        'debug_toolbar.panels.settings.SettingsPanel',
	        'debug_toolbar.panels.headers.HeadersPanel',
	        'debug_toolbar.panels.request.RequestPanel',
	        'debug_toolbar.panels.sql.SQLPanel',
	        'debug_toolbar.panels.staticfiles.StaticFilesPanel',
	        'debug_toolbar.panels.templates.TemplatesPanel',
	        'debug_toolbar.panels.cache.CachePanel',
	        'debug_toolbar.panels.signals.SignalsPanel',
	        'debug_toolbar.panels.logging.LoggingPanel',
	        'debug_toolbar.panels.redirects.RedirectsPanel',
	    ]

	    DEBUG_TOOLBAR_CONFIG = {
	        'INTERCEPT_REDIRECTS': False,
	    }

	    GOOGLE_OAUTH2_CLIENT_ID = '<your id>'
	    GOOGLE_OAUTH2_CLIENT_SECRET = '<your secret>'

	    TWITTER_CONSUMER_KEY = '<your id>'
	    TWITTER_CONSUMER_SECRET = '<your secret>'
	    
	    FACEBOOK_APP_ID = '<your id>'
	    FACEBOOK_API_SECRET = '<your secret>'     

Hit http://127.0.0.1:8000 to view the site!