#########
Changelog
#########

This is the changelog for Puppetboard.

0.0.5
=====

* Now requires WTForms versions less than 2.0
* Adding a Flask development server in ``dev.py``.
* Adding CSRF protection VIA the flask_wtf CsrfProtect object.
* Allowing users to configure the report limit on pages where reports are
  listed with the LIMIT_REPORTS configuration option.
* Adding an inventory page to users to be able to see all available nodes
  and a configure lists of facts to display VIA the INVENTORY_FACTS
  configuration option.
* Adding a page to view a node's catalog information if enabled, disabled
  by default. Can be changed with the ENABLE_CATALOG configuration attribute.
* New configuration option GRAPH_FACTS allows the user to choose which graphs
  will generate pie on the fact pages.
* Replacing Chart.js with c3.js and d3.js.
* Adding Semantic UI 0.16.1 and removing unused bootstrap styles.
* Adding an OFFLINE_MODE configuration option to load local assets or from a
  CDN service. This is useful in environments without internet access.

0.0.4
=====

* Fix the sorting of the different tables containing facts.
* Fix the license in our ``setup.py``. The license shouldn't be longer than
  200 characters. We were including the full license tripping up tools like
  bdist_rpm.

0.0.3
=====
This release introduces a few big changes. The most obvious one is the
revamped Overview page which has received significant love. Most of the work
was done by Julius Härtl. The Nodes tab has been given a slight face-lift
too.

Other changes:

* This release depends on the new pypuppetdb 0.1.0. Because of this the SSL
  configuration options have been changed:

  * ``PUPPETDB_SSL`` is gone and replaced by ``PUPPETDB_SSL_VERIFY`` which
    now defaults to ``True``. This only affects connections to PuppetDB that
    happen over SSL.
  * SSL is automatically enabled if both ``PUPPETDB_CERT`` and
    ``PUPPETDB_KEY`` are provided.

* Display of deeply nested metrics and query results have been fixed.
* Average resources per node metric is now displayed as a natural number.
* A link back to the node has been added to the reports.
* A few issues with reports have been fixed.
* A new setting called ``UNRESPONSIVE_HOURS`` has been added which denotes
  the amount of hours after which Puppetboard will display the node as
  unreported if it hasn't checked in. We default to ``2`` hours.
* The event message can now be viewed by clicking on the event.

Puppetboard is now neatly packaged up and available on PyPi. This should
significantly help reduce the convoluted installation instructions people had
to follow.

Updated installation instructions have been added on how to install from PyPi
and how to configure your HTTPD.

0.0.2
=====
In this release we've introduced a few new things. First of all we now require
pypuppetdb version 0.0.4 or later which includes support for the v3 API
introduced with PuppetDB 1.5.

Because of changes in PuppetDB 1.5 and therefor in pypuppetdb users of the v2
API, regardless of the PuppetDB version, will no longer be able to view reports
or events.

In light of this the following settings have been removed:

* ``PUPPETDB_EXPERIMENTAL``

Two new settings have been added:

* ``PUPPETDB_API``: an integer, defaulting to ``3``, representing the API
  version we want to use.
* ``ENABLE_QUERY``: a boolean, defaulting to ``True``, on wether or not to
  be able to use the Query tab.

We've also added a few new features:

* Thanks to some work done during PuppetConf together with Nick Lewis (from
  Puppet Labs) we now expose all of PuppetDB's metrics in the Metrics tab. The
  formatting isn't exactly pretty but it's a start.
* Spencer Krum added the graphing capabilities to the Facts tab.
* Daniel Lawrence added a feature so that facts on the node view are clickable
  and take you to the complete overview of that fact for your infrastructure
  and made the nodes in the complete facts list clickable so you can jump to a
  node.
* Klavs Klavsen contributed some documentation on how to run Puppetboard with
  Passenger.

0.0.1
=====
Initial release.
