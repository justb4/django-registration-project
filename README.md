# Django Registration Project Bootstrap

This is a minimal Django Project for bootstrapping your own Django Project
with full acccount registration functionality based on 
[django-registration-redux](https://django-registration-redux.readthedocs.io).

This emerged from my quest on the Web for a simple/ready Django Project
to get started with using account registration and management. 
Although the [django-registration-redux documentation](https://django-registration-redux.readthedocs.io) is
of high standard, I missed a complete example. 

Basically this project is based on the
[Django Registration test-app on GitHub](https://github.com/macropin/django-registration/tree/master/test_app)
with even more minimalism:

* using the `default` settings/urls
* leaving out `admin approval` stuff
* leaving `CustomUser` model

Check the original [App on GitHub](https://github.com/macropin/django-registration/tree/master/test_app) if
you need those functions.

This project is already configured for:

* user registration with email confirmation
* password reset via email
* changing password

The/my idea is that one should start with a registration app and work from there.
For example for building a webshop with Stripe or any other apps where
user registration is needed.

## Install and Run

* create a (Python3) virtualenv 
* `pip install -r requirements`
* `python manage.py migrate`
* `python manage.py runserver`
* go to http://localhost:8000

## Adding Email 

By default confirmation email URLs are shown in the console and can be copy/pasted
to http://localhost:8000/accounts/...

To truly test with real email, you need a real email SMTP provider.
Easiest is to make a separate gmail account 
and [enable less secure apps](https://support.google.com/a/answer/6260879?hl=en).

In [settings.py](accounts/settings.py) comment out:

	# EMAIL_BACKEND = 'django.core.mail.backends.console.EmailBackend'

and add your gmail config instead as follows:

	EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
	EMAIL_USE_TLS = True
	EMAIL_HOST = 'smtp.gmail.com'
	EMAIL_HOST_PASSWORD = '*****'  # the gmail password
	EMAIL_HOST_USER = 'yourname@gmail.com'  # the gmail username
	EMAIL_PORT = 587
	DEFAULT_FROM_EMAIL = EMAIL_HOST_USER

## Credits 

Yes, I am aware that there are two `django-registration` projects:

* [https://github.com/ubernostrum/django-registration](django-registration)
* [https://github.com/macropin/django-registration](django-registration-redux)

Credits to [James Bennet](https://github.com/ubernostrum) who initiated 
[https://github.com/ubernostrum/django-registration](django-registration) (2008) and 
subsequently [James Cutler](https://github.com/macropin/) who initiated
[https://github.com/macropin/django-registration](django-registration-redux) at a period
of inactivity at [https://github.com/ubernostrum/django-registration](django-registration).

This project-repo is based on [https://github.com/macropin/django-registration](django-registration-redux)
which started as a fork of the first, but both projects are now (2018) maintained actively.

Confused? I was as well at first, but there are now just multiple options. Not to speak of
even more Django Registration packages like  [Pinax Accounts](https://github.com/pinax/django-user-accounts)
and [Django AllAuth](https://github.com/pennersr/django-allauth). The latter has e.g. options for OAuth/Social Media
login.


## Notes

* Haven't called this project `django-registration-bootstrap` in order not to confuse with [Bootstrap the HTML, CSS, JS library](https://getbootstrap.com/))
