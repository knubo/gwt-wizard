GWT-Wizard: A GWT Wizard Widget for Your Project
================================================

GWT-Wizard is a [wizard][1] widget for use in your own GWT projects. It
tries to make as few assumptions as possible about your needs, making it a
flexible and powerful tool, while still providing sane defaults that allow
simple projects to get up and running with as little configuration as possible.

![sample-wizard](http://binarymuse.github.com/gwt-wizard/images/sample-wizard.png)

GWT-Wizard has a few nice features, including the following:

  * Flexible view component: use the built in view, or provide your own by
    implementing provided interfaces.
  * Support for lazy-loading wizard pages: if you don't want to attach your
    wizard's pages to the DOM right away, enable lazy loading and attachment
    and extend `LazyComposite` for your page widgets.
  * Useful transition hooks for each of your pages: use methods like
    `beforeShow()` and `beforeNext()` to do setup, cleanup, validation and
    more in your pages. Cancel page navigation via the provided
    `NavigationEvent` if you want to cancel a page transition. Set up two-way
    links between pages based on user input.
  * Flexible behavior with sane defaults: GWT-Wizard lets you customize
    virtually every element of your wizard, from how it looks to how it
    behaves. But, if you just want a simple, linear wizard, you don't have
    to customize anything.

Getting Started
---------------

Getting started with GWT-Wizard is easy:

  1. Build the project (see below) or download a JAR from the project's [home page][2].
  2. Put `gwt-wizard.jar` on your project's build path
  3. Inherit the wizard module with `<inherits name='net.binarymuse.gwt.Wizard' />`
  4. Extend `WizardContext` to define your context object
  5. Create one or more page for your wizard (a single-page wizard seems kinda
     silly) by extending `WizardPage` (the only methods you **must** provide
     are `getTitle()`, `getPageID()`, and `asWidget()`)
  6. Create a new wizard with `new Wizard("Wizard Title", contextObject)` (you
     can also pass a custom view if you so wish)
  7. Call `wizard.addPage()` for each of the pages you wish to add to your wizard
  8. Attach the wizard to the DOM

More Details and Examples
-------------------------

You can find code samples, working examples, and more at the
[GWT-Wizard's home on the web][2].

Project Status
--------------

GWT-Wizard should be considered alpha software. The API is highly malleable
and may change from commit to commit.

Build Quick-Start
-----------------

Assuming you have GWT installed to `/path/to/gwt/gwt-x.y.z/` and Apache
Ant installed:

  1. Clone the project and change to the project directory:
     `git clone git://github.com/BinaryMuse/gwt-wizard.git && cd gwt-wizard`
  2. Specify the path of the GWT library:
     `export GWTPATH=/path/to/gwt/gwt-x.y.z/`
  3. Run the Ant script to build the project and create a JAR:
     `ant jar`

Detailed Build Target Information
---------------------------------

The `build.xml` file supplies several Apache Ant build targets:

### Building GWT-Wizard

  * **Target Command**: `ant compile`
  * **Task**: Compile the GWT-Wizard project and copy both the uncompiled source
    files and the compiled class files to the directory `bin`.
  * **Depends On**:
    * GWT installed to `/path/to/gwt/gwt-x.y.z/`
    * Environment variable `GWTPATH` set to the value `/path/to/gwt/gwt-x.y.z/`
  * **Cleaning**: `ant clean`

### Creating a JAR

  * **Target Command**: `ant jar`
  * **Task**: Package the uncompiled source and compiled class files into a JAR
    named `gwt-wizard.jar`.
  * **Depends On**:
    * Target `compile`
  * **Cleaning**: `ant clean-jar`

### Creating the JavaDoc

  * **Target Command**: `ant doc`
  * **Task**: Create the GWT-Wizard JavaDoc in the directory `doc`.
  * **Depends On**: *none*
  * **Cleaning**: `ant clean-doc`

### Creating the Site

  * **Target Command**: `ant site`
  * **Task**: Compile the GWT-Wizard site ([http://gwt-wizard.binarymuse.net][2])
    into the directory `pages-source/output`. Copies the JavaDoc if the `doc`
    task is ran first.
  * **Depends On**:
    * [Ruby][3] installed
    * [nanoc][4] installed (`gem install nanoc`)
    * [RedCloth][5] installed (`gem install RedCloth`)
    * [CodeRay][6] installed (`gem install coderay`)
    * [Nokogiri][7] installed (`gem install nokogiri`)
      (rquired `libxml2-dev` and `libxslt1-dev` on my Ubuntu box)
  * **Cleaning**: `ant clean-site`

### Cleaning All

  * **Target Command**: `ant clean-all`
  * **Task**: Run all the `clean` targets

What's Missing
--------------

There are a few things missing from the current iteration of GWT-Wizard:

  * Removing pages: once a page has been added to a wizard, it can't
    be removed
  * DOM dependence: there is some DOM/GWT dependence in classes that should
    be a presenter (in the MVP sense)
  * Unit Tests: there are currently no unit tests checked in for the project

License
-------

GWT-Wizard is licensed under the MIT License. See the LICENSE file for details.

  [1]: http://en.wikipedia.org/wiki/Wizard_%28software%29 "Wizard on Wikipedia"
  [2]: http://gwt-wizard.binarymuse.net/ "GWT-Wizard Home Page"
  [3]: http://www.ruby-lang.org/en/ "Ruby"
  [4]: http://nanoc.stoneship.org/ "nanoc"
  [5]: http://redcloth.org/ "RedCloth"
  [6]: http://coderay.rubychan.de/ "CodeRay"
  [7]: http://nokogiri.org/ "Nokogiri"
