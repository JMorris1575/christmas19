Getting Christmas 2019 Working Locally
======================================

I installed sphinx and django yesterday and it seemed  to go without a hitch. Using my **Instructions** I got the
command to start a local server which is:

``python manage.py runserver``

The first error is:

``django.core.exceptions.ImproperlyConfigured: Error loading psycopg2 module: No module named 'psycopg2'``

Hmm... how do I install that?

Installing psycopg2
-------------------

Ah! It's easy. According to **Instructions** it is just:

``pip install psycopg2``

After the above error, however, PyCharm's terminal was hung up until I did a Ctrl-Break to get back to the prompt.

It successfully installed psycopg2-2.8.4.

The website is now working on the local computer. That was easy!
