# Landed Theme

The **Landed** Theme is for [Grav CMS](http://github.com/getgrav/grav). It's a port of [Landed](https://html5up.net/landed) by HTML5 UP under its [CCA 3.0 license](https://html5up.net/license).

![Landed](screenshot.jpg)

# Installation

Installing the Landed theme can be done in one of two ways. Our GPM (Grav Package Manager) installation method enables you to quickly and easily install the theme with a simple terminal command, while the manual method enables you to do so via a zip file.

>> Whichever installation method you use, ensure that Grav's `site.yaml` config file contains the vocabulary 'pagetype' as per the demo content's [`site.yaml`](https://github.com/hughbris/grav-theme-landed/blob/b89a7835cdf01e2f5d4c10ee543640a675ee452f/_demo/config/site.yaml#L13):

```yaml
taxonomies: [category, tag, pagetype]
```

>> If you don't do this, any pages you want to be featured by applying taxonomy `pagetype: feature` in frontmatter, will not appear in featured sections, and important pages like the theme homepage will look wrong.

## GPM Installation (Preferred)

The simplest way to install this theme is via the [Grav Package Manager (GPM)](http://learn.getgrav.org/advanced/grav-gpm) through your system's Terminal (also called the command line).  From the root of your Grav install type:

    bin/gpm install landed

This will install the Landed theme into your `/user/themes` directory within Grav. Its files can be found under `/your/site/grav/user/themes/landed`.

>> This method will copy the sample pages provided in the `_demo/pages` folder to your `user/pages` folder so that the theme will work out of the box with placeholder content. The content is the same _Ipsum lorem_ content provided in the original [HTML5 UP theme](https://html5up.net/landed).

## Manual Installation

To install this theme, just download the zip version of this repository and unzip it under `/your/site/grav/user/themes`. Then, rename the folder to `landed`. You can find these files either on [GitHub](https://github.com/hughbris/grav-theme-landed) or via [GetGrav.org](http://getgrav.org/downloads/themes).

You should now have all the theme files under

    /your/site/grav/user/themes/landed

>> NOTE: If you want to use and adapt the default _Ipsum lorem_ content provided with the original theme, move the contents of `_demo/pages` into your grav installations's `user/pages` directory. This will ensure that the theme templates work out of the box.

# Updating

As development for the Landed theme continues, new versions may become available that add additional features and functionality, improve compatibility with newer Grav releases, and generally provide a better user experience. Updating Landed is easy, and can be done through Grav's GPM system, as well as manually.

## GPM Update (Preferred)

The simplest way to update this theme is via the [Grav Package Manager (GPM)](http://learn.getgrav.org/advanced/grav-gpm). You can do this with this by navigating to the root directory of your Grav install using your system's Terminal (also called command line) and typing the following:

    bin/gpm update landed

This command will check your Grav install to see if your Landed theme is due for an update. If a newer release is found, you will be asked whether or not you wish to update. To continue, type `y` and hit enter. The theme will automatically update and clear Grav's cache.

## Manual Update

Manually updating Landed is pretty simple. Here is what you will need to do to get this done:

* Delete the `your/site/user/themes/landed` directory.
* Download the new version of the Landed theme from either [GitHub](https://github.com/hughbris/grav-plugin-landed) or [GetGrav.org](http://getgrav.org/downloads/themes#extras).
* Unzip the zip file in `your/site/user/landed` and rename the resulting folder to `landed`.
* Clear the Grav cache. The simplest way to do this is by going to the root Grav directory in terminal and typing `bin/grav clear-cache`.

> Note: Any changes you have made to any of the files listed under this directory will also be removed and replaced by the new set. Any files located elsewhere (for example a YAML settings file placed in `user/config/themes`) will remain intact.

# Usage

## Supported page templates

* [Sample homepage view template](templates/home.html.twig)
* [Left sidebar two-column template](templates/left-sidebar.html.twig)
* [Right sidebar two-column template](templates/right-sidebar.html.twig)
* [Single column template](templates/default.html.twig)
* Barely distinct [Error page template](templates/error.html.twig)

## Page blueprint provided

* [(Partial) homepage blueprint](blueprints/home.yaml)

## Deferred assets block support

[Deferred blocks were introduced in Grav 1.5.10](https://getgrav.org/blog/important-theme-updates) and **are now impemented in this theme**.

# Configuring

## Custom styles

The theme is bundled with an empty CSS file at `css/custom.css`. As the name suggests, this is where you can add any additional styles for your implementation of the theme. If your site uses a theme that inherits Landed, you can add this file and your customisations at the same relative location in your own theme.

## Menu Features

### Dropdown Menu

You can enable **dropdown menu** support by enabling it in the `landed.yaml` configuration file. As per usual, copy this file to your `user/config/themes/` folder (create if required) and edit there.

```yaml
dropdown:
  enabled: true
```

This will ensure that sub-pages show up as sub-menus in the navigation.

### Menu Text

Each page shows up in the menu using the title by default, however you can set what displays in the menu directly by setting an explicit `menu:` option in the page header:

```yaml
menu: My Menu
```

### Custom Menu Items

By default, Grav generates the menu from the page structure.  However, there are times when you may want to add custom menu items to the end of the menu.  This is now supported in Landed by creating a menu list in your `site.yaml` file.  An example of this is as follows:

```yaml
menu:
    - url: https://github.com/hughbris/grav-theme-landed
      text: Source
    - url: 'https://example.org/landed-signup'
      text: 'Sign Up'
      classes: 'button primary'
```

The `url:` and `text:` options are required.

If you supply a `classes:` option, those are added to the menu link classes. This is a new option added for the Landed theme.

## Source theme conformance

Thanks to some weird workarounds that hopefully don't bring me technical debt (sorry future self!), and not wanting to break any existing implementations, I've added a conformance frontmatter property to contain settings for potentially anything that might be a departure from the source HTML5UP theme.

```yaml
# theme elements that should match the source theme rather than an improved one offered in this Grav theme
conformance:
    jquery: true
```

### jQuery library

The theme is bundled with a [minified jQuery source file](https://github.com/hughbris/grav-theme-landed/blob/develop/js/jquery.min.js), which is out of date but works, and which you may prefer to use instead of the [much later version still bundled as an asset group by Grav core](https://github.com/getgrav/grav/blob/afb5b02e5750f0f9c0bcc73de5d3f62947881722/system/config/system.yaml#L139).

> For the moment your site will keep working as it has been if you don't change any settings. This might change BTW, slowly slowly.

There has been [an issue](https://github.com/hughbris/grav-theme-landed/issues/13) and some dependabot alerts about the old jQuery bundled with the source theme and with this Grav theme. I am not an expert and have not looked closely, but I _suspect_ this theme is _not vulnerable_ to these exploits. _This is not advice. Also not an invitation to anyone with nefarious intent._

This theme provides **two more options** to load whatever you like for your jQuery. The jQuery asset is added:

* in a partial template at `templates/partials/asset-jquery.html.twig` that _you can easily override in a custom theme_;
* within a Twig block called `jquery` that _you can extend inside another template_.

### Homepage settings

The [homepage template](templates/home.html.twig) supports, and is largely driven by, custom page frontmatter. It is yet to be documented fully.

The [demo homepage](_demo/pages/01.home/home.md) provides a comprehensive example implementation of the custom YAML frontmatter that you can adapt. It is reasonably intuitive and you can map parts of it to the [rendered demo page](https://behold.metamotive.co.nz/landed).

> A [homepage blueprint](blueprints/home.yaml) is being developed to support homepage custom YAML frontmatter structures.

#### Homepage banner settings

You can set some homepage banner settings using the Admin plugin console. The theme adds a custom 'Banner' tab where you edit pages.

This is the annotated format for banner frontmatter:

```yaml
banner:
    headline: 'Site headine ahoy'
    quips:
        - 'A quippy quip under the headline.'
        - 'And another one makes three.'
    media:
    # you can set the images used in the banner, these are all optional and have fallbacks
        background: # banner background image
            location: library.jpg # name of an image file in the page folder
        hero: # banner hero image
            location: desk.jpg # name of an image file in the page folder
            alt: Cluttered desk # alt text for hero image
```
Note that you can _also_ provide `alt` text for a hero image by using an adjacent [media metafile](https://learn.getgrav.org/17/content/media#metafiles) with an `alt_text` property. However, any nonempty `banner.media.hero.alt` custom frontmatter always takes precedence, so make sure you unset that if you want to reference the media metafile instead.

You can also override a file in your theme's `/images` folder called `banner.jpg` to set the banner's background image. This is a legacy hack method that will probably continue to work because the theme will always come with a fallback hero image at that location.

There are also deprecated legacy custom YAML frontmatter properties under `banner:` that you can specify currently. The [homepage demo page](_demo/pages/01.home/home.md) contains commented out examples. Any new style frontmatter under `banner.media` takes precedent over these values. Legacy frontmatter will not work in future.

## Setup

If you want to set Landed as the default theme, you can do so by following these steps:

* Navigate to `/your/site/grav/user/config`.
* Open the **system.yaml** file.
* Change the `theme:` setting to `theme: landed`.
* Save your changes.
* Clear the Grav cache. The simplest way to do this is by going to the root Grav directory in Terminal and typing `bin/grav clear-cache`.

Once this is done, you should be able to see the new theme on the frontend. Keep in mind any customizations made to the previous theme will not be reflected as all of the theme and templating information is now being pulled from the **landed** folder.

## Examples in the wild

None that I know of yet! Please let me know if you are using it (hey, it's free publicity).

The site I was building using this theme unfortunately didn't launch.

In case you missed the other links, I have also deployed a [live demo for the theme](https://behold.metamotive.co.nz/landed) which usually runs the latest release.