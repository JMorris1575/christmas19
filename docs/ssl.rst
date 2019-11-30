Getting SSL Updated on the Christmas 2018 Website
=================================================

Earlier today I tried, unsuccessfully, to update my LetsEncrypt certificate using a button on webfaction. I think I will
have to follow the instructions in the **Instructions** project.

Renewing the Certificate in ssh
-------------------------------

I got into ssh jmorris@web506.webfaction.com (noticing that **Instructions** incorrectly said
jmorris.web506.webfaction.com) and entered the command::

    ~$: acme.sh --issue --test -d christmas.jmorris.webfactional.com -d www.christm
    as.jmorris.webfactional.com -w ~/webapps/my_sll_app

And got this response::

    [Sat Nov 30 00:10:30 UTC 2019] Using stage ACME_DIRECTORY: https://acme-staging.api.letsencrypt.org/directory
    [Sat Nov 30 00:10:31 UTC 2019] Domains not changed.
    [Sat Nov 30 00:10:31 UTC 2019] Skip, Next renewal time is: Sun Dec  1 00:34:12 UTC 2019
    [Sat Nov 30 00:10:31 UTC 2019] Add '--force' to force to renew.

That seemed o.k. to me so I proceeded to do it for real::

    ~$: acme.sh --issue -d christmas.jmorris.webfactional.com -d www.christmas.jmor
    ris.webfactional.com -w ~/webapps/my_sll_app

    [Sat Nov 30 00:11:32 UTC 2019] Domains not changed.
    [Sat Nov 30 00:11:32 UTC 2019] Skip, Next renewal time is: Sun Dec  1 00:34:12 UTC 2019
    [Sat Nov 30 00:11:32 UTC 2019] Add '--force' to force to renew.

Nothing much seemed to happen so I tried the ``--force`` option::

    ~$: acme.sh --issue --force -d christmas.jmorris.webfactional.com -d www.christ
    mas.jmorris.webfactional.com -w ~/webapps/my_sll_app

    [Sat Nov 30 00:12:24 UTC 2019] Multi domain='DNS:christmas.jmorris.webfactional.com,DNS:www.christmas.jmorris.webfactional.com'
    [Sat Nov 30 00:12:25 UTC 2019] Getting domain auth token for each domain
    [Sat Nov 30 00:12:25 UTC 2019] Getting webroot for domain='christmas.jmorris.webfactional.com'
    [Sat Nov 30 00:12:25 UTC 2019] Getting new-authz for domain='christmas.jmorris.webfactional.com'
    [Sat Nov 30 00:12:25 UTC 2019] The new-authz request is ok.
    [Sat Nov 30 00:12:26 UTC 2019] Getting webroot for domain='www.christmas.jmorris.webfactional.com'
    [Sat Nov 30 00:12:26 UTC 2019] Getting new-authz for domain='www.christmas.jmorris.webfactional.com'
    [Sat Nov 30 00:12:26 UTC 2019] The new-authz request is ok.
    [Sat Nov 30 00:12:26 UTC 2019] Verifying:christmas.jmorris.webfactional.com
    mkdir: cannot create directory ‘/home/jmorris/webapps/my_sll_app’: Permission denied
    /home/jmorris/.acme.sh/acme.sh: line 3951: /home/jmorris/webapps/my_sll_app/.well-known/acme-challenge/D3wAVtAk3jLQvYXYy08ZfPNs4JrzGB6uhjjcboAHJkw: No such file or directory
    [Sat Nov 30 00:12:26 UTC 2019] christmas.jmorris.webfactional.com:Can not write token to file : /home/jmorris/webapps/my_sll_app/.well-known/acme-challenge/D3wAVtAk3jLQvYXYy08ZfPNs4JrzGB6uhjjcboAHJkw
    [Sat Nov 30 00:12:26 UTC 2019] Please add '--debug' or '--log' to check more details.
    [Sat Nov 30 00:12:26 UTC 2019] See: https://github.com/Neilpang/acme.sh/wiki/How-to-debug-acme.sh

That seemed to work but...

Copying the Files to Webfaction
-------------------------------

I got into FileZilla to find the new files on webfaction in ``/home/jmorris/.acme.sh/christmas.jmorris.webfactional.com``
and discovered three new files:

christmas.jmorris.webfactional.com.conf
christmas.jmorris.webfactional.com.csr
christmas.jmorris.webfactional.com.csr.conf

I copied them over to Notepad++ but they were not the right ones. The directions said to copy

* ~/.acme.sh/mysite.com.cer to the **Certificate** section
* ~/.acme.sh/mysite.com.key to the **Private key** section and
* ~/.acme.sh/ca.cer to the **Intermediates/bundle** section

Hmm... none of those were in the new files. Also, the ca.cer file was in the
``~/.acme.sh/christmas.jmorris.webfactional.com`` directory and NOT in the ``~/.acme.sh/`` directory.

However, the ``ca.cer`` and ``christmas.jmorris.webfactional.com.cer`` files had been updated on 10/1/2019 and the
``christmas.jmorris.webfactional.com.key`` file was still the 12/5/2018 copy. I copied them to the appropriate sections
of Webfaction's SSL editing page and the site is now working properly as an encrypted site!

Conclusions
-----------

It seems that the cron job that renews the certificate periodically IS working but that it doesn't copy the new
information to the proper places. Either I have to do that myself or figure out how to automate it.










