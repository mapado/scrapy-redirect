``scrapy-redirect`` restricts authorized HTTP redirections to the website homepage.

If the `Scrapy <http://scrapy.org/>`_ ``REDIRECT_ENABLED`` config key is set to ``False`` and a request to the homepage of the crawled website returns a `3XX status code <https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#3xx_Redirection>`_, the crawl will stop immediatly.

``scrapy-redirect`` will force Scrapy to tolerate redirections coming from the ``start_urls`` urls, in the case  where``REDIRECT_ENABLED = False``.

Installation
------------

.. code-block:: bash

    $ pip install scrapy-redirect


Configuration
--------------

Install ``scrapy-redirect`` in your Scrapy middlewared by adding the following key/value pair in the ``SPIDER_MIDDLEWARES`` settings key (in ``settings.py``):

.. code-block:: python

    SPIDER_MIDDLEWARES = {
        ...
        'scrapyredirect.redirect.HomepageRedirectMiddleware': 575,
        ...
    }

Note that it is important for the middleware order value to be inferior to 600 (the `default value <http://doc.scrapy.org/en/0.16/topics/settings.html#downloader-middlewares-base>`_  of the ``'scrapy.contrib.downloadermiddleware.redirect.RedirectMiddleware'`` middleware), as it must be executed before Scrapy blocks the redirection.

License
-------

``scrapy-redirect`` is published under the MIT License.