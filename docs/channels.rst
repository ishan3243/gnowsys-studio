========
Channels
========

.. module:: gstudio.views.channels

Views by author, categories, tags is not enough :).

The idea is to create specific pages based on a query search.
Imagine that we want to customize the homepage of the Weblog, because we
write on a variety of subjects and we don't want to bore visitors who
aren't interested in some really specific entries.
Another usage of the channels is for SEO, for aggregating entries
under a well-formatted URL.

For doing that Gstudio provides a view called
:func:`~gstudio.views.channels.entry_channel`.

If we take our first example, we will do like that for customizing
the Weblog homepage in our project's urls.py. ::

  url(r'^weblog/$', 'gstudio.views.channels.objecttype_channel',
      {'query': 'category:python OR category:django'}),
  url(r'^weblog/', include('gstudio.urls')),

The first URL will handle the homepage of the blog instead of the default
URL provided by Gstudio.

As we can see, the only required argument for this view is ``query``. This
parameter represents a query search string. This string will be interpreted
by the search engine activated in Gstudio and return a list of entries (See
:doc:`search_engines` for more informations).

So our homepage will only display entries filled under the categories
**Python** or **Django**.

The others parameters handled by the channel view are the same that
the generic view named :func:`~django.views.generic.list_detail.object_list`
bundled in :mod:`django.views.generic.list_detail`.
