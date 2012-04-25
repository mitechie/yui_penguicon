jQuery who?
===========

Why everyone here needs some YUI.
---------------------------------

.. raw:: pdf

   Transition Dissolve 1
   PageBreak


Rick Harding who?
==================

Launchpad Developer [#]_

Bookie developer [#]_


- @mitechie
- blog.mitechie.com
- Richard Harding on Google+


.. raw:: pdf

   Transition Dissolve 1
   PageBreak



In the right room?
===================

MOAR JAVASCRIPT!
----------------

.. raw:: pdf

   Transition Dissolve 1
   PageBreak


What's a javascript application?
================================
Turn off JS and no worky

.. raw:: pdf

   Transition Dissolve 1
   PageBreak

Stages of javaScript
====================

Stage 1 - "I don't need any JavaScript, that stuff sucks!"


.. raw:: pdf

   Transition Dissolve 1
   PageBreak

Stage 2:
========
"Well, I only dropped in a few lines for that effect...isn't it cool!"


.. raw:: pdf

   Transition Dissolve 1
   PageBreak


Stage 2.5:
==========
"DAMN YOU IE!!!!!!"

.. raw:: pdf

   Transition Dissolve 1
   PageBreak

Stage 3:
========
"Oooh, this jQuery thing works in IE...oh and I can do this...and that..."

... 2hrs later ...

"Hmmm, I could use that pretty datepicker on my site!""

.. raw:: pdf

   Transition Dissolve 1
   PageBreak


Stage 4:
========
"Where's the code that makes the pretty bordered popup again?"

`JS Driven Dimentia`

.. raw:: pdf

   Transition Dissolve 1
   PageBreak


Now you've got an application
===================================

- Look for the PHP Devs in the room

.. raw:: pdf

   Transition Dissolve 1
   PageBreak


There's hope!
=============

.. raw:: pdf

   Transition Dissolve 1
   PageBreak

Application needs
=================

- small units of code
- version control the small units of code
- tests of the small units of code
- library-ize the small units of code
- reuse the small units of code
- profile the small units of code
- only include the small units of code you need

.. raw:: pdf

   Transition Dissolve 1
   PageBreak

What's a small unit of code?
=============================

- Class?
- Method?
- Library?

.. raw:: pdf

   Transition Dissolve 1
   PageBreak

Small unit of code: jQuery
===========================

- Plugin

::

    (function( $ ) {
      $.fn.myPlugin = function() {
        // Do your awesome plugin stuff here

      };
    })( jQuery );

.. raw:: pdf

   Transition Dissolve 1
   PageBreak


Using the jQuery plugin
=======================
::

    <script type="text/javascript" src="jquery.js"></script>
    <script type="text/javascript" src="myPlugin.js"></script>
    <script type="text/javascript">
        $('body').myPlugin();
    </script>

.. raw:: pdf

   Transition Dissolve 1
   PageBreak


Small unit of code: YUI
========================

- Module

::

    YUI.add('myPlugin', function(Y) {
        var ns = Y.namespace('myPlugin');
        // Add your awesome code to the namespace

    }, '0.1', { requires: [ 'node' ] });

.. raw:: pdf

   Transition Dissolve 1
   PageBreak




Using a YUI module
==================
::

    <script type="text/javascript"
      src="/combo?y/yui/yui-min.js&y/loader/loader-min.js"></script>
    <script type="text/javascript" src="myPlugin.js"></script>
    <script type="text/javascript">
      YUI().use('myPlugin', function (Y) {

        var node = Y.one('body');
        Y.myPlugin.dostuff(node);

      });
    </script>

.. raw:: pdf

   Transition Dissolve 1
   PageBreak


Good practices
===============

- both are pretty isolated
- both don't pollute the global namespace
- YUI only pulls in the code it needs to run

  - node module (via myPlugin dependencies!)
  - no event, json parsing, cookie, ajax, effects


.. raw:: pdf

   Transition Dissolve 1
   PageBreak


Have a module, test a module!
=============================

::

    YUI().use('test', 'myPlugin' function (Y) {
        var testCase = new Y.Test.Case({
            name: "myPlugin Base Tests",
            testPluginDoesSomething : function () {
                Y.Assert.isTrue(...)
                Y.Assert.isFalse(...)
            },
            ...
        });
        var testCase2 = new Y.Test.Case({
            name: "myPlugin Event Tests",
            ...
        });


.. raw:: pdf

   Transition Dissolve 1
   PageBreak


Have a module, test a module, release a module?
===============================================
Combo Loader

::

    ...combo?yui/yui-min.js&loader/loader-min.js&substitute/substitute-min.js

.. raw:: pdf

   Transition Dissolve 1
   PageBreak


Combo loader duties
===================================
- Find the modules requested
- Get their listed dependencies
- Concat all the files together
- Reply!

.. raw:: pdf

   Transition Dissolve 1
   PageBreak


Controlling the combo loader
===================================

::

    YUI.GlobalConfig = {
        combine: true,
        base: '/combo?y/',
        comboBase: '/combo?',
        root: 'y/',
        groups: {
            bookie: {
                combine: true,
                base: '/combo?b',
                comboBase: '/combo?',
                root: 'b/',
                // filter: 'raw',
                // comes from including bookie/meta.js
                modules: YUI_MODULES,

.. raw:: pdf

   Transition Dissolve 1
   PageBreak


Less config more code!
=======================
- Cookies
- Async (ajax)
- Templates (Handlebars)
- Chart generation
- History
- Internationalization
- Profiler

.. raw:: pdf

   Transition Dissolve 1
   PageBreak


Cookie for example
==================
::

    // Create a YUI instance and use the cookie module.
    YUI().use('cookie', function(Y) {
        Y.Cookie.set("name", "value", { expires: new Date("January 12, 2025") });

        var value = Y.Cookie.get("name");

.. raw:: pdf

   Transition Dissolve 1
   PageBreak



Well thought out: Cookies
==========================

::

        // subcookie!
        var data = {
            name: "ace123",
            age: 22,
            track: true
        };

        //set a cookie named "user" with subcookies
        Y.Cookie.setSubs("user", data);


.. raw:: pdf

   Transition Dissolve 1
   PageBreak


jQuery me some cookies!
=======================

.. image:: http://uploads.mitechie.com/yui/jquery_cookie_search.png
   :alt: finding cookie
   :align: center


.. raw:: pdf

   Transition Dissolve 1
   PageBreak

jQuery finding...
=======================

.. image:: http://uploads.mitechie.com/yui/jquery_cookie_simple.png
   :alt: no sub cookies
   :align: center


.. raw:: pdf

   Transition Dissolve 1
   PageBreak

jQuery missing?
=======================

.. image:: http://uploads.mitechie.com/yui/jquery_cookie_notfound.png
   :alt: ummm, second result?
   :align: center


.. raw:: pdf

   Transition Dissolve 1
   PageBreak


YUI: Yahoo scale
=================

- Hotmail = 350M
- Yahoo Mail = 310M
- Gmail = 260M


.. raw:: pdf

  Transition Dissolve 1
  PageBreak


Modular Code
============
::

    YUI.add('bookie-indicator', function (Y) {
            var ns = Y.namespace('bookie');

        /**
         * Indicator widget class
         *
         * @class Indicator
         * @extends Y.Widget
         *
         */
        ns.Indicator = Y.Base.create( 'bookie-indicator', Y.Widget, [], {
            initializer: function(cfg) {
                this.hide();
            },

.. raw:: pdf

  Transition Dissolve 1
  PageBreak

What's it mean to be Base
==========================

- initializer(), destroy()
- ATTRS, get/set
- on, after, before, fire

.. raw:: pdf

  Transition Dissolve 1
  PageBreak


jQuery - plugins what api?
============================
remove, destroy, empty, even available?

.. raw:: pdf

  Transition Dissolve 1
  PageBreak


Everything uses Base
====================
- Plugins


`Plugins are used to add atomic pieces of functionality or features to component instances (hosts), without having to bake support or even knowledge of the feature into the component class.`

.. raw:: pdf

  Transition Dissolve 1
  PageBreak



Ummm, Plugin what?
===================
::

    Y.Panel = Y.Base.create('panel', Y.Widget, [
        // Other Widget extensions depend on these two.
        Y.WidgetPosition,
        Y.WidgetStdMod,

        Y.WidgetAutohide,
        Y.WidgetButtons,
        Y.WidgetModality,
        Y.WidgetPositionAlign,
        Y.WidgetPositionConstrain,
        Y.WidgetStack
    ], {

.. raw:: pdf

  Transition Dissolve 1
  PageBreak


Reusable ain't it?!
====================
- Design
- Modular
- Tested


.. image:: http://uploads.mitechie.com/yui/yui_tested.png
   :alt: just a few tests...
   :align: center
   :width: 900px


.. raw:: pdf

  Transition Dissolve 1
  PageBreak



So what do I write then?
========================

- Class (Base.create())
- Module
- Plugin
- Widget
- View
- App

.. raw:: pdf

  Transition Dissolve 1
  PageBreak


Back to the widget
====================
Show Indicator on bookie

.. raw:: pdf

  Transition Dissolve 1
  PageBreak

Indicator
===========

::

    var indicator = new Y.bookie.Indicator({
        target: Y.one('#bmarks')
    });
    // doens't show, just makes sure all the html is there and events bound
    // ready to go
    indicator.render();
    // all widgets have these methods
    indicator.show();
    indicator.hide();

.. raw:: pdf

  Transition Dissolve 1
  PageBreak

Look at indicator code
=======================

...

.. raw:: pdf

  Transition Dissolve 1
  PageBreak



Look at indicator tests
=========================

...

.. raw:: pdf

  Transition Dissolve 1
  PageBreak


Lots of parts, what about an app?
==================================
- App
- Router
- Model
- ModelList
- View

.. raw:: pdf

  Transition Dissolve 1
  PageBreak


App
====

::

    var app = new Y.App({
        views: {
            home : {preserve: true},
            users: {preserve: true},
            user : {parent: 'users'}
        }
    });

.. raw:: pdf

  Transition Dissolve 1
  PageBreak


View
======

::

    var Y.UserView = Y.Base.create('userview', Y.View, [], {
        event: {
            '.add': {
                click: 'adduser'
            },
        },
        initializer: function (cfg) {
        },
        render: function () {
          var container = this.get('container'),
              html      = this.template(this.get('model').toJSON());
          container.setContent(html);
        }
    });

.. raw:: pdf

  Transition Dissolve 1
  PageBreak


.. [#] http://launchpad.net
.. [#] https://bmark.us
