
Translating and building
------------------------

To build english version of rst files in source folder::

 make html

For translations, see:

http://www.sphinx-doc.org/en/stable/intl.html#using-transifex-service-for-team-translation

https://github.com/rduivenvoorde/translationtest

https://www.transifex.com/qgis/translationtest_1/

So onetime (if there is not a .tx folder yet.. which there is for this project..)::

 tx init

Then run to build the pot files (in this project in `build/en/gettext` folder)::

 make gettext

The 'pot' file now generated are use to create 'transifex resources'

Now to fill the `.tx/config` file with your resources, run (in our project, which I called translationtest_1 at transifex)::

 sphinx-intl update-txconfig-resources --pot-dir build/en/gettext/ --transifex-project-name translationtest_1

And push the pot files to transifes::

 tx push -s

Add some languages (at the transifex website).

Do some translations (at website)

Now to pull for example the dutch translations, do::

 tx pull -l nl

This will pull the po files with translations from tx into the locale folder

now you can build the dutch site with::

 make html LANG=nl


If you now add new strings to excisting files::

 make gettext
 tx push -s

BUT if you add a new rst file or resource::

 make gettext
 sphinx-intl update-txconfig-resources --pot-dir build/en/gettext/ --transifex-project-name translationtest_1
 tx push -s






