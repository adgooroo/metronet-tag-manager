=== Metronet Tag Manager ===
Contributors: ronalfy, pereirinha
Tags: google, google tag manager, tag manager
Requires at least: 3.9
Tested up to: 4.3
Stable tag: 1.0.6
License: GPLv2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

Integrate Google Tag Manager into  your website.

== Description ==

Integrate Google Tag Manager into your website.

The great thing about Google Tag Manager (GTM) is that you are able to gather most of your tracking scripts in one place. You can then fire these scripts whenever you want, specified by the rules you set up. This sounds great, right? Well it is.  The only problem is that sometimes it takes a bit of implementing to set these rules up. This implementation can either be setting a dataLayer variable in the dataLayer before the tag manager script is loaded, or pushing a HTML event handler with the variable "event" to the dataLayer when a button is clicked. The problem is that this isn’t always that easy to do when you don’t have the ability/access to add the code to your site.

This is where the Metronet Tag Manager plugin shines. It really unlocks the power of the dataLayer so you can easily set macros and firing rules on almost any element.

This plugin lets you:
<ul>
<li>Easily add as many dataLayer variables on a per-post and per-page basis as you need.</li>
<li>The plugin already gives you six predefined dataLayer variables that you can change/remove or test the system with. These will be loaded on all pages and posts.</li>
<li>Set up separate dataLayer variables for pages that aren’t posts or pages (like archives etc).</li>
<li>Lets you easily add a HTML event handler to any content link with the GTM TinyMCE  button in the WYSIWYG.</li>
<li>Lets you add your own unique ID or a class to each content link with the GTM TinyMCE button in the WYSIWYG.</li>
</ul>

Please note that for this plugin to work there is a slight customization that is needed. WordPress doesn’t let you load scripts straight after the opening <body> tag which is where the GTM script needs to be placed to work correctly. To fix this you need to add `<?php do_action( 'body_open' ); ?>` just after the `<body>` tag and that’s it.

Please let us know if you have any feature requests or if you have any issues with this plugin.

Below are a couple of resources you might find valuable if you are new to Google Tag Manager

Official Google Tag Manager website
https://developers.google.com/tag-manager/

Tracking Google Analytics Events with Google Tag Manager
http://moz.com/ugc/tracking-google-analytics-events-with-google-tag-manager
 
Make Analytics Better with Tag Management and a Data Layer
http://cutroni.com/blog/2012/05/14/make-analytics-better-with-tag-management-and-a-data-layer/

== Installation ==

1. Just unzip and upload the "metronet-tag-manager" folder to your '/wp-content/plugins/' directory
2. Activate the plugin through the 'Plugins' menu in WordPress
3. Modify your theme's `header.php` to include `<?php do_action( 'body_open' ); ?>` right after the opening `<body>` tag.
4. Go to the plugin's settings and input your Google Tag Manager data.

== Frequently Asked Questions ==

= What is Google Tag Manager =

Please refer to the <a href="http://www.google.com/tagmanager/faq.html">Google Tag Manager FAQ</a>.

= What are dataLayer variables? =

Please refer to the <a href="https://developers.google.com/tag-manager/reference">Google Tag Manager API</a> reference.

= What are dataLayer variables used for? =

The data layer is an object that contains the information that you want to pass to Google Tag Manager. By setting up rules in Google Tag Manager, these variables can then be used to include the correct snippets or scripts – for example when a certain button is clicked.

== Screenshots ==

1. Admin settings.
2. Per-post/page settings.
3. TinyMCE button for adding dataLayer variables.

== Changelog ==

= 1.0.6 =
* Updated 2015-08-20 - WordPress 4.3
* Released 2015-04-03
* Bug fix - Allow periods in datavariables to comply with GTM 2.0.

= 1.0.5 =
* Updated 2014-12-11 - Ensuring WordPress 4.1 compatibility 
* Released 2014-09-11
* Fixed anonymous function crashing PHP < 5.3 users

= 1.0.4 =
* Released 2014-08-27
* Fixed meta problem with datavariables showing up in areas where there aren't posts or pages
* Ensuring WordPress 4.0 compatibility

= 1.0.3 =
* Released 2014-07-08
* Migration to TinyMCE 4
* Translations template

= 1.0.2 =
* Released 2013-07-30
* Documentation update

= 1.0.1 =
* Released 2013-07-24
* Fixing TinyMCE JavaScript issue

= 1.0 =
* Initial release.

== Upgrade Notice ==

= 1.0.6 =
Bug fix - Allow periods in datavariables to comply with GTM 2.0.

= 1.0.5 =
Fixed anonymous function crashing PHP < 5.3 users

= 1.0.2 =
Documentation update

= 1.0.1 =
Fixing TinyMCE JavaScript bug.

= 1.0 =
Initial Release

== Filtering Variables ==

If you choose to place variable values inside percentage signs (e.g., %replace_test%), you can filter these as necessary.

Here's an example:
`
add_filter( 'gtm_replace_test', 'gtm_replace_test', 10, 3 );
function gtm_replace_test( $total_match, $match, $post_id ) {
	return "replaced with content";
}
`

The filter name is `gtm_` with the suffix of `replace_test`, since that content is inbetween the percentage signs.
