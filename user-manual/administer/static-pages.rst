.. _manage-static-pages:

===================
Manage static pages
===================

In AtoM, :term:`static pages <static page>` are pages that are designed to look
the same each time they are accessed; this is in contrast to dynamic pages,
which can vary according to your network or institution and according to the
content that is uploaded into AtoM. Examples of dynamic pages include:
search results pages; :term:`view pages <view page>`;
and :term:`edit pages <edit page>`. By default, AtoM has two :term:`static pages
<static page>`: the :term:`Home page` and the :term:`About page`.

A default welcome message appears on the :term:`Home page` when first logging
into AtoM.

.. image:: images/welcome-page.*
   :align: center
   :width: 70%
   :alt: An image of the Home page

.. SEEALSO::

   * :ref:`Home page <home-page>`

The :term:`About page` provides additional information about the application and
the project. To access the :term:`About page`, click on the |info| :ref:`Quick
links menu <quick-links-menu>` in the :term:`main menu` located in the
:term:`header bar` and select "About".

.. image:: images/about-page.*
   :align: center
   :width: 70%
   :alt: An image of the About page

.. |info| image:: images/info-sign.png
   :height: 18
   :width: 18

For more information on navigating in AtoM, see :ref:`access-content`.

All static pages in AtoM, including the two default static pages described above,
can be customized by logged-in users via the :term:`user interface`. New static
pages can also be created, and all static pages (except the home page) can be
deleted from the application.

**Below are instructions on how to edit and add static pages in AtoM:**

* :ref:`security-static-pages`
* :ref:`edit-static-page`

  * :ref:`Edit the "Home page" <edit-home-page>`
  * :ref:`Edit the "About page" <edit-about-page>`

* :ref:`Add a new static page <add-static-page>`
* :ref:`Add links to a new static page <add-links-static>`
* :ref:`static-pages-menu`
* :ref:`Styling static pages <styling-static-page>`

.. NOTE::

   :term:`Static pages <static page>` can only be edited and added by an
   authenticated (i.e. logged-in) :term:`administrator` or :term:`editor`.
   For more information on user permissions, see :ref:`edit-user-permissions`.

.. _security-static-pages:

Static pages and security configuration
=======================================

.. _htmlpurifier: http://htmlpurifier.org/

As of version 2.2, AtoM now has advanced configuration settings that will allow
a system administrator to enable htmlpurifier_ on static pages. htmlpurifier is:

      *...a standards-compliant HTML filter library written in PHP. HTML Purifier
      will not only remove all malicious code (better known as XSS) with a
      thoroughly audited, secure yet permissive whitelist, it will also make
      sure your documents are standards compliant, something only achievable
      with a comprehensive knowledge of W3C's specifications.*

By default, htmlpurifier is **not** turned on in AtoM, to allow a broad use of
HTML and inline CSS on static pages. System administrators interested in enabling
all possible security settings and mitigating the risk of XSS-based attack vectors
can enable the library by altering the ``config/app.yml`` file. For more
information, see:

* :ref:`config-app-yml`
* :ref:`admin-security`

When the configuration is set to ``true``, htmlpurifier_ will limit the available
html elements to the following:

**Tags allowed**

.. code:: bash

   'div', 'span', 'p',
   'h1', 'h2', 'h3', 'h4', 'h5', 'h6',
   'strong', 'em',
   'abbr[title]', 'acronym', 'address',
   'blockquote', 'cite', 'code',
   'pre', 'br',
   'a[href]', 'img[src]',
   'ul', 'ol', 'li',
   'dl', 'dt', 'dd',
   'table', 'tr', 'td', 'th',
   'tbody', 'thead', 'tfoot',
   'col', 'colgroup', 'caption',
   'b', 'i', 'tt',
   'sub', 'sup', 'big', 'small', 'hr'

**Attributes allowed**

.. code:: bash

   'class', 'title', 'src', 'href'

.. IMPORTANT::

   Any elements used that do not match these parameters when htmlpurifier is
   engaged will not render in the browser, meaning they will not be visible in
   your  static page. Make sure you review the content you have added to your
   static pages before engaging this security setting!

:ref:`Back to top <manage-static-pages>`

.. _edit-static-page:

Edit an existing static page
============================

.. |gears| image:: images/gears.png
   :height: 18
   :width: 18

In AtoM, :term:`static pages <static page>`, that is both the :term:`Home page`
and the :term:`About page` can be edited by authenticated (i.e. logged-in)
:term:`administrators <administrator>` or :term:`editors <editor>` to reflect
your own institution's or :term:`network's <network>` requirements.

This section contains instructions on how to edit :term:`static
pages <static page>` in AtoM. There are two ways to edit :term:`static pages
<static page>` - doing so via the |info| :ref:`Quick links menu
<quick-links-menu>` in the :term:`main menu` and selecting either "Home" or
"About" from the :term:`drop-down menu` is the easiest, but to accommodate
different workflows, these :term:`static pages <static page>` can also
be edited by clicking the the |gears| :ref:`Admin <main-menu-admin>` and
selecting "Static pages" from the :term:`drop-down menu`. This second option
will route you to a "List" page, where all :term:`static pages <static page>`
in the application will be listed. Navigate to the :term:`static page` you wish
to edit by clicking on the blue menu name. Below are instructions to edit to
the :ref:`Home page <edit-home-page>` and the :ref:`About page
<edit-about-page>`.

For more information on navigating in AtoM, see :ref:`Navigation in AtoM
<navigate>`.

.. _edit-home-page:

Edit the "Home page"
--------------------

To edit the "Home page" in AtoM:

#. Start by navigating to the :term:`Home page`. Do this by either:

   * Clicking on the AtoM :term:`site logo` located in the top-left corner of
     the AtoM :term:`header bar`;
   * Clicking the |info| :ref:`Quick links menu <quick-links-menu>` in the
     :term:`main menu` of the :term:`header bar` and selecting  "Home" from the
     :term:`drop-down menu`; **or**
   * Clicking the |gears| :ref:`Admin <main-menu-admin>` of the
     :term:`header bar` and selecting "Static pages" from the
     :term:`drop-down menu`. Once you are directed to the "List page" for
     :term:`static pages <static page>`, click on the "Welcome" blue menu.

   All three options will direct you to the :term:`Home page` :term:`view page`.

   .. NOTE::

      Editing the "Title" :term:`field` of the :term:`Home page` will edit the
      blue menu that you will select in the :term:`static page` "List page"
      (i.e. if you change "Welcome" to say "Bienvenue", the blue menu in the
      "List page", as well as the main header of the :term:`Home page` will
      change to "Bienvenue").

#. To switch from the main :term:`view page` to :term:`edit mode`, click on the
   :term:`edit button` in the :term:`button block`.
#. On loading, the `edit page` will display a "Title" :term:`field`, a
   :term:`Slug` :term:`field` and a "Content" :term:`field`.

   .. IMPORTANT::

      The :term:`Slug` :term:`field` is a page title referenced by AtoM
      code to manage URLs; it **cannot be changed** for the :term:`Home page` or
      the :term:`About page`. However, it can be edited in any static pages that
      you :ref:`add yourself <add-static-page>`.

#. Add and/or revise data as required.

   .. TIP::

      Users can include `HTML <https://en.wikipedia.org/wiki/Html>`__ and inline
      `CSS <https://en.wikipedia.org/wiki/CSS>`__ code to the "Content"
      :term:`field` to include any links and special styling. See :ref:`below
      <styling-static-page>` for information on how to style :term:`static
      pages <static page>`.

#. You can quit the edit process at any time by clicking the "Cancel" button
   in the :term:`button block`; any data already entered will not be saved. Note
   that simply navigating away from the page by any other means, **without first
   clicking "Create"** will also result in no edits being saved.
#. To save the changes made to the :term:`Home page`, click the
   :term:`"Create" button <create button>` located in the :term:`button block`
   at the bottom of the record.

.. _edit-about-page:

Edit from About page
--------------------

To edit the :term:`About page` in AtoM:

#. Navigating to the :term:`About page`. You can do this by either:

   * Clicking the |info| :ref:`Quick links menu <quick-links-menu>` in the
     :term:`main menu` of the :term:`header bar` and selecting  "About" from the
     :term:`drop-down menu`; **or**
   * Clicking the |gears| :ref:`Admin <main-menu-admin>` of the
     :term:`header bar` and selecting "Static pages" from the
     :term:`drop-down menu`. Once you are directed to the "List page" for
     :term:`static pages <static page>`, click on the "About" blue menu.

   Both options will direct you to the :term:`About page` :term:`view page`.

   .. NOTE::

      Editing the "Title" :term:`field` of the :term:`About page` will edit the
      blue menu that you will select in the :term:`static page` "List page"
      (i.e. if you change "Welcome" to say "Bienvenue", the blue menu in the
      "List page", as well as the main header of the :term:`About page` will
      change to "Bienvenue").

#. To switch from the main :term:`view page` to :term:`edit mode`, click on the
   :term:`edit button` in the :term:`button block`.
#. On loading, the `edit page` will display a "Title" :term:`field`, a
   :term:`Slug` :term:`field` and a "Content" :term:`field`.

   .. IMPORTANT::

      The "Slug" :term:`field` is a page title referenced by AtoM code
      to manage URLs; it **cannot be changed** for the :term:`Home page` or the
      :term:`About page`. However, it can be edited in any static pages that you
      :ref:`add yourself <add-static-page>`.

#. Add and/or revise data as required.

   .. TIP::

      Users can include `HTML <https://en.wikipedia.org/wiki/Html>`__ and
      inline `CSS <https://en.wikipedia.org/wiki/CSS>`__ code to the "Content"
      :term:`field` to include any links and special styling. See :ref:`below
      <styling-static-page>` for information on how to style :term:`static
      pages <static page>`.

#. You can quit the edit process at any time by clicking the "Cancel" button
   in the :term:`button block`; any data already entered will not be saved. Note
   that simply navigating away from the page by any other means, **without first
   clicking "Create"** will also result in no edits being saved.
#. To save the changes made to the :term:`Home page`, click the
   :term:`"Create" button <create button>` located in the :term:`button block`
   at the bottom of the record.

:ref:`Back to top <manage-static-pages>`

.. _add-static-page:

Add a new static page
=====================

In AtoM, new :term:`static pages <static page>` can be added at any time by any
authenticated (i.e. logged-in) :term:`administrator`. Similar to both the
:term:`Home page` and the :term:`About page`, you may wish to add a new static
page in order to include permanent, or "timeless" content to your webpage.
:term:`Static pages <static page>` may be customized to offers users
instructions or help in navigating the site (i.e. a "Help" page),
provide contact information (i.e. a "Contact Us" page), or feature website
content, categories, and/or contributors.

To add a new static page in AtoM:

#. Click the the |gears| :ref:`Admin <main-menu-admin>` in the
   :term:`header bar` and select "Static pages" from the :term:`drop-down menu`.
#. You will be directed to a "List pages" page, where all :term:`static pages
   <static page>`, including the :term:`Home page` and the :term:`About page`
   will be listed.
#. Click on the :term:`Add new button` in the :term:`button block` to be
   directed to the :term:`edit page` for your new static page.
#. On loading, the `edit page` will display blank "Title", :term:`Slug` and
   "Content" :term:`fields <field>`. Add data as required.

   .. TIP::

      The :term:`slug` indicates the word, or sequence of words that will be
      visible to users in the URL link when they are navigating on a specific
      :term:`static page` (e.g.: the slug in the URL *www.artefactual.com/help*
      is */help*). The slug should be indicative of the content of that
      specific static page.

   When creating a new :term:`static page`, the :term:`slug` :term:`field` can
   either be customized or left blank. If you choose to customize the
   :term:`slug`, make the slug all lowercase, keep it short, and avoid accented
   characters (e.g.: "é"; "ñ"; "û") and punctuation (e.g.: "!"; ";"; "..."). If
   you leave the :term:`field` blank, AtoM will automatically generate a slug
   based on the "Title" you have indicated for your page (e.g.: If your "Title"
   is *About Us*, the slug for that static page will automatically be generated
   as *.../about-us*). Note that AtoM will automatically replace all accented
   characters with letters from the English alphabet and punctuation will either
   be removed or replaced by a dash "-" or percent-encoding (e.g.: If your
   "Title" is *Instructions & More*, the slug for that static page will
   automatically be generated as *.../instructions%26more* or
   *.../instructions-more*, unless otherwise indicated). The :term:`slug` will
   also appear in the once blank "Slug" :term:`field` and can be viewed when
   switching from the :term:`view page` to the :term:`edit page` of that
   :term:`static page`.

   .. WARNING::

      A :term:`slug` cannot be duplicated once it has been generated in AtoM. If
      you duplicate a slug, AtoM will automatically generate a "-2 (or the next
      subsequent number) at the end of the slug to distinguish it from the other
      one in the same name (e.g.: Two slugs titled *information* will result in
      the second of the two becoming *information-2*). If you remove an AtoM
      automatically generated :term:`slug` from the slug :term:`field` of a
      :term:`static page` you've created, AtoM will not re-generate the original
      slug, regardless of whether or not the "Title" of your page has
      changed; rather, it will generate a new slug in the form of a series
      of letters and numbers. **This should be avoided**, as it creates
      confusion because it does not accurately indicate the content of that
      :term:`static page`. To avoid this, simply enter a custom :term:`slug`.

#. You can quit the creation process at any time by clicking the "Cancel" button
   in the :term:`button block`; any changes made will not be saved. Note that
   simply navigating away from the page by any other means, **without first
   clicking "Save"** will also result in no new :term:`static page` being
   created.
#. When you are finished creating your new :term:`static page`, click the "Save"
   button in the :term:`button block`.

You will be directed to the :term:`view page` of the new :term:`static page`
where you can view your changes. The page can be :ref:`edited
<edit-static-page>` again at any time.

:ref:`Back to top <manage-static-pages>`

.. _add-links-static:

Add links to a new static page
==============================

Once a new :term:`static page` has been created, a new link must also be
created in order to allow users to navigate to the new static page. You can do
this by either creating a link within one of the default :term:`static pages
<static page>` or by clicking Admin > Menus and clicking the
:term:`Add new button` in the :term:`button block` or by linking the new
:term:`static page` to an existing menu.

This example shows a newly created "Contact Us" :term:`static page` that has
been added as a menu under the |info| :ref:`Quick links <quick-links-menu>`
parent menu:

.. image:: images/add-new-menu.*
   :align: center
   :width: 70%
   :alt: An image of Contact Us menu linked under Quick Links menu

Here is the result of the above:

.. image:: images/new-contact-us.*
   :align: center
   :width: 70%
   :alt: An image of new Contact Us menu

The information which will be needed when linking a new static page:

1. Name: an internal name which is not visible to users.

2. Label: how you wish the name of the page to appear in the menu.

3. Parent: which menu you wish the page to be linked from.

4. Path: in the format ``staticpage/index?slug=yourSlug``. yourSlug is the
   slug you either created or had AtoM generate automatically for you when the
   page was created.

5. Description: an optional area to describe the purpose of the page.

For more information on managing menus in AtoM, see: :ref:`manage-menus`.

:ref:`Back to top <manage-static-pages>`

.. _static-pages-menu:

Add a custom sidebar menu with links to your static pages
=========================================================

If you have certain static pages that you would like to be prominent and
readily available to users throughout the application, you can also create a
custom Static pages menu. This involves working with both static pages, and
the :ref:`manage-menus` module.

.. image:: images/staticpages-menu-top.*
   :align: center
   :width: 80%
   :alt: An example of the Static pages menu, shown on a static page

When nodes are added as children to the ``staticPagesMenu`` in |gears| **Admin
> Manage menus**, They become visible in the following places:

* On the homepage's left-hand side, above the Browse and Popular this week
  links
* On all :term:`archival description` pages, below the treeview (or below the
  Quick search menu, when the full-width treeview is in use - see:
  :ref:`treeview-type` for more information)
* As a sidebar menu on the left side of all static pages.

You can also give the new sidebar menu a custom heading. The following
instructions will use the example of adding links to help pages, created using
the static pages module.

.. SEEALSO::

   * :ref:`manage-menus`

**To add a custom sidebar menu wtih links to your static pages:**

1. Prepare the static pages you would like to use in the menu items. If you
   haven't created them yet, see above, :ref:`add-static-page` for guidance on
   creating new static pages, and below, :ref:`styling-static-page` for hints
   on how to use HTML and simple inline-CSS to style them.

2. You will need to know the :term:`slug` you have assigned to each static
   page you want to add to the new menu - you can either return to the
   :term:`edit page` of your static page, or navigate to the :term:`view page`,
   and look at the URL to identify the permalink (the unique part of the URL -
   for example, on the webpage http://www.example.com/about-us, ``about-us``
   would be the slug. For further information, see :ref:`slugs-in-atom`).
3. Navigate to |gears| **Admin > Menus** and scroll down until you see the
   ``staticPagesMenu`` node near the bottom. Click on it to enter
   :term:`edit mode`.

.. image:: images/staticpages-menu.*
   :align: center
   :width: 80%
   :alt: An image of the staticPagesMenu node in Manage Menus

4. You can now edit the "Label" :term:`field` value, to give your new menu a
   custom header. In this example, we'll call our new menu "Help pages."

.. image:: images/staticpages-menu-label.*
   :align: center
   :width: 80%
   :alt: An image of editing the staticPagesMenu Label value

5. Save the page by clicking the "Save" button in the :term:`button block` at
   the bottom of the page. **Note:** you may be prevented from saving the
   first time - AtoM will prompt you for a Path value, even though none was
   there before. You can simply enter a ``/`` slash character in the field,
   and then click "Save."

.. image:: images/staticpages-menu-path.*
   :align: center
   :width: 80%
   :alt: An example of a save warning, and adding a slash to the Path field to
         resolve it.

6. AtoM will return you to the Manage menus page. Now we'll add our static
   page(s) to this menu. Click the "Add new" button in the
   :term:`button block` located at the bottom of the Manage menus page.
7. AtoM will open a new :term:`edit page` for a menu item. For further
   information on working with menus, see: :ref:`manage-menus`.
8. Fill out the menu edit page with the information about your static page:

   * **Name:** This is an internal name used by AtoM, that will not be seen by
     AtoM users.  We suggest using
     `camelCase <https://en.wikipedia.org/wiki/CamelCase>`__ as part of a naming
     convention. In this example, we've called our menu node ``searchHelp``.
   * **Label**: This is what public users will see in your sidebar menu. Note
     that the name does not need to be the same one you've given your static
     page - in our example, we've named our static page "Searching in AtoM,"
     but we've decided to call the menu link "Search Help."
   * **Parent**: For your new menu node to show up in the sidebar menu, you
     must choose ``-staticPagesMenu`` from the drop-down list
   * **Path**: This is where we'll use the :term:`slug` from your static page.
     We could just add the slug directly, but to make the routing more
     reliable, add it as follows: ``staticpage/index?slug=your-slug-here``,
     where ``your-slug-here`` is the slug you gave your static page.
   * **Description** This is not visible to public users - you can add a
     description to remind yourself and other
     :term:`administrators <administrator>` how and why this node was added to
     the Menus page, if you like.

.. image:: images/staticpages-menu-add-new.*
   :align: center
   :width: 80%
   :alt: An example of a new menu page

9. You can quit the create process at any time, by clicking the "Cancel"
   button in the :term:`button block` at the bottom of the page. Note that
   navigating away from the page without first clicking "Save" will also
   result in a loss of all your changes.
10. When you are satisfied with the information entered, click the "Save"
    button located in the :term:`button block` at the bottom of the page. AtoM
    will redirect you to the Manage menus page.
11. You can repeat steps 6-10 as needed, to add other static pages to your new
    menu.
12. You should now see your new sidebar menu on the home page,
    :term:`archival description` view pages, and when viewing any other
    :term:`static page`. Some examples images are included below.

.. IMPORTANT::

   Some things to remember when working with static pages and new new Static
   pages sidebar menu:

   * Because the presence of the menu affects the normal width of the static
     pages, you might want to review how your static pages look if you have
     added a lot of custom styling to them.
   * If you create a new static page, it is **not** automatically added to
     either the Quick links menu, OR the new Static pages Menu described
     above - you must add links yourself.
   * If you delete a static page that has been added to either of the above
     menus, the menu links will **not** automatically disappear - you must
     also manually delete the links from the ``staticPagesMenu`` in the Manage
     menus page. Otherwise, they will still be visible throughout the
     application - but they will lead to a broken page!
   * If you decide you no longer want the Static pages menu to be visible,
     simply delete the child page nodes you have added - if the
     ``staticPagesMenu`` node in **Admin > Manage menus** has no children, the
     sidebar will no longer display in the user interface.
   * For more information on managing menus in AtoM, see: :ref:`manage-menus`.

.. _static-pages-menu-examples:

Examples of the Static pages menu in use
----------------------------------------

**On the homepage**:

.. image:: images/staticpages-menu-home.*
   :align: center
   :width: 80%
   :alt: An example of the sidebar menu on the home page

**On an archival description (sidebar treeview)**:

.. image:: images/staticpages-menu-tree-side.*
   :align: center
   :width: 80%
   :alt: An example of the sidebar menu on an archival description

**On an archival description (full-width treeview)**:

.. image:: images/staticpages-menu-tree-full.*
   :align: center
   :width: 80%
   :alt: An example of the sidebar menu on an archival description

**On annother static page**:

.. image:: images/staticpages-menu-static.*
   :align: center
   :width: 80%
   :alt: An example of the sidebar menu on a static page

:ref:`Back to top <manage-static-pages>`

.. _styling-static-page:

Styling static pages
====================

Basic styling of :term:`static pages <static page>` can be achieved by including
`HTML <https://en.wikipedia.org/wiki/Html>`__ and inline
`CSS <https://en.wikipedia.org/wiki/CSS>`__ code
to the "Content" :term:`field`. There are plenty of online tutorials
and resources out there for instruction on HTML and inline CSS use, but a few
basic examples commonly employed by AtoM users have been included here as an
example.

See below for instructions on how to create and edit:

* :ref:`Headers and subtitles <static-headers-subtitles>`
* :ref:`Hyperlinks <static-hyperlinks>`
* :ref:`Images <static-image>`
* :ref:`Boxes and dividers <static-boxes-dividers>`

.. TIP::

   There is also a custom syntax that you can use throughout AtoM to add
   hyperlinks, which will also work in the static pages - see:

   * :ref:`add-custom-links`

.. _static-headers-subtitles:

Headers and subtitles
---------------------

To increase the size of a heading or subtitle, wrap the relevant text in
``<h3> </h3>`` tags, like so:

.. code-block:: bash

   <h3>For more information, please contact</h3>.

This will produce the following results:

.. image:: images/larger-headings.*
   :align: center
   :width: 70%
   :alt: An image of a larger heading

For larger headings, use smaller numbers, such as ``<h2>`` or ``<h1>``.
Similarly, for smaller headers, use ``<h4>`` or ``<h5>``. To bold, italicize or
underline headers and subtitles, simply wrap the relevant text in
``<strong></strong>`` for **bold**, ``<em> </em>`` for *italics*, or ``<u> </u>``
for underline. Typing ``<strong>Artefactual Systems Inc.</strong>`` will produce
the following results:

.. image:: images/headings-subtitles.*
   :align: center
   :width: 70%
   :alt: An image of a bolded subtitle

.. _static-hyperlinks:

Hyperlinks
----------

To create external links on an AtoM static page, wrap the text you would like to
act as a link in a hyperlink ``<a> </a>`` tag, and include the web
address to which you would like the link to point, using the ``href=" "``
attribute - the http address would go in the quotations. Remember to close the
element after the text you want to link.

For example, to include a link in the "Contact Us" page, the code would
appear as such:

.. code-block:: bash

   Website: <a href="https://www.accesstomemory.org/en/">AtoM : Open Source
   Archival Description Software</a>

The above code would appear like this on the static page:

.. image:: images/hyperlinks.*
   :align: center
   :width: 70%
   :alt: An image of a hyperlink

Alternately, instead of HTML, you can also use AtoM's custom syntax for adding
hyperlinks - for more information, see: :ref:`add-custom-links`.

.. _static-image:

Images
------

If you have access to the server on which your AtoM instance is located (i.e.,
if you are hosting it yourself, or can ask the host provider to include a file
for you), you can place images in a directory on the host server, and use a
local URL to point to them. Images can then be used via the HTML ``<img>``
image element, where the ``src=" "`` attribute points to the
path of the image, similar to how the hyperlinks are used above. For example, if
you wanted an image of email, named "contact-image.jpg" included on your static
"Contact Us" page, the code might look like this:

.. code-block:: bash

   ``<img src=".../path/to/contact-image.jpg">``

...where ``/path/to`` represents the internal URL path to the location of
``contact-image.jpg`` on your host server, or the path to a web-accessible image.

To center the image, you can wrap the ``<img>`` image element in a ``<div>``
element, with a ``text-center"`` class, like this:

.. code-block:: bash

   <div class="text-center"><img src=".../path/to/contact-image.jpg"></div>

You can also reuse some of the existing image classes from Bootstrap, to further
style your images. For example, you can round the corners with the ``img-rounded``
class:

.. code-block:: bash

   <img class="img-rounded" src="../path/to/my-bunny-image.jpg">

Produces:

.. image:: images/img-rounded.*
   :align: center
   :width: 40%
   :alt: An image of a picture using the rounded class

Make an image circular using the ``img-circle`` bootstrap class:

.. code-block:: bash

   <img class="img-circle" src="../path/to/my-bunny-image.jpg">

Produces:

.. image:: images/img-circle.*
   :align: center
   :width: 40%
   :alt: An image of a picture using the circle class

Or give your images a frame, like on our digital object browse page, using the
``img-polaroid`` class:

.. code-block:: bash

   <img class="img-polaroid" src="../path/to/my-bunny-image.jpg">

Produces:

.. image:: images/img-polaroid.*
   :align: center
   :width: 40%
   :alt: An image of a picture using the polaroid class

.. TIP::

   Resuing existing Bootstrap CSS classes is a good way to style elements when
   you have the htmlpurifier_ setting engaged - see above,
   :ref:`security-static-pages` for more information.

.. _static-boxes-dividers:

Boxes and dividers
------------------

You can add styled boxes around text by wrapping content in the HTML ``<div>``
element, and then using inline CSS to modify the
appearance of the box. For colors, use the HTML or RGB values for the color you
would like to use, rather than generic names such as "red," "blue," etc. - most
browsers support a limited pallette of colors using names such as this, and the
results may be inconsistent across browsers. There are many free HTML color
wheels available that allow you to choose a color and copy its HTML# or RGB
values; for example: http://www.colorpicker.com/

For a small centered box with a green color, you might use code such as
this:

.. code-block:: bash

   <div style="width:600px; margin-left:right; margin-right:right; padding: 5px;
   background-color:#39BF34; border:none;">Here is a list of ways that we can be
   contacted with any questions or concerns you may have:</div>

This is how the box will appear:

.. image:: images/boxes.*
   :align: center
   :width: 70%
   :alt: An image of a box

.. NOTE::

   The above example will **not** work if you have htmlpurifier_ engaged in AtoM.
   For more information, see the section above, :ref:`security-static-pages`
   for more information. The examples below, reusing existing Bootstrap classes,
   **will** work even when htmlpurifier is engaged.

Another example of this is the light yellow box that appears on the AtoM demo's
"Welcome" static page warning users that the data will reset every hour. This
yellow box is reusing an existing style class from the Bootstrap CSS framework
that AtoM uses - you can make use of existing Bootstrap classes to help with
styling, like so:

.. code-block:: bash

   <div style="alert">Welcome message appears here</div>

And here is the result:

.. image:: images/welcome-box.*
   :align: center
   :width: 70%
   :alt: An image of a box

Other Bootstrap alert classes that can be used to style containers include
``alert-success``, ``alert-info``, and ``alert-danger``:

.. image:: images/div-alert-classes.*
   :align: center
   :width: 70%
   :alt: An image of various boxes styled with Bootstrap classes

:ref:`Back to top <manage-static-pages>`
