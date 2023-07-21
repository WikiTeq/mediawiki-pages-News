# News package

`Package` is the installable set of MediaWiki pages. The News package provides a set of input forms and templates that make it easy to add and manage `News` - wiki pages announcing current events.

Content author is @wikivisor

# Requirements

## Extensions

* SemanticMediaWiki
* PageForms
* ParserFunctions
* SemanticResultFormats (for `tagcloud` format )
* MagicNoCache
* PageExchange or PagePort

## Configuration settings

* `$wgRestrictDisplayTitle = false;`
* `$wgPFEnableStringFunctions = true;`
* depending on news length, you may want to bump the string length limit `$wgPFStringLengthLimit = 10000;`

# Setup

## via PagePort

* download the repository
* run `php extensions/PagePort/maintenance/importPages.php --source ~/pages-News`

## via PageExchange

* add the following to the bottom of your `LocalSettings.php`: `$wgPageExchangePackageFiles[] = 'https://raw.githubusercontent.com/WikiTeq/mediawiki-pages-News/master/page-exchange.json';`
* navigate to `Special:Packages` and install the package
* run `php maintenance/runJobs.php`

# Usage

Once imported, navigate to `Project:All_news`. This page is created using the `{{All news|all}}` template call and displays all ever-created news categorized by the year of publication. 

![Screenshot from 2023-07-02 13-55-02](https://github.com/WikiTeq/mediawiki-pages-News/assets/62721134/4bc7eafa-b2ef-419e-8cb8-1339ec1c6ae8)

Tags and feeds can further filter news:

![Screenshot from 2023-07-02 13-55-46](https://github.com/WikiTeq/mediawiki-pages-News/assets/62721134/4d365fae-990c-4f87-9522-07b35e570d5e)

The size of the tag link font varies depending on the number of news using this tag. Feeds and tags are independent dimensions that can be used for news classification.

The most common use case is to deliver the "actual" news rather than the full history of the news posts. By "actual", we mean news, the visibility period of which includes the current date. The actual news can be delivered to any page using `{{All news|actual}}` template call and wrapped to comply with the wiki's overall styling: 

![Screenshot from 2023-07-02 14-05-19](https://github.com/WikiTeq/mediawiki-pages-News/assets/62721134/26e57994-5746-4cf6-b79a-5a4dd5b550ae)

News can be created by clicking the `Add news` button. A form with necessary controls and inputs is provided:

![Screenshot from 2023-07-02 14-04-19](https://github.com/WikiTeq/mediawiki-pages-News/assets/62721134/3a771c51-13fd-4466-a5f4-184dffcd3d2e)

The form is designed to help users to set:
* News display title that will override the technical page name given to the news page (similar to `News_20230426090835`);
* News feed name (the default set of feeds can be extended or completely re-defined on the `Property:News_type` page);
* News tags (the existing tags will be suggested as you type, the new tags can be added right in the form input);
* A period when the news is to be considered `actual`;
* "Repeat every year" flag, which makes the news appear in actual news within the specified period (days/months, regardless of the year);
* "Is sticky" flag, which pins the news at the top of the actual news list;
* "Not ready for publication yet" flag, which hides the work in progress from the list of actual news;

The form provides the textarea for the news text (supports VisualEditor if [Extension:VEForAll](https://www.mediawiki.org/wiki/Extension:VEForAll) is installed) and a subform for adding attachments.

Once saved, the form will produce the news page:

![Screenshot from 2023-07-02 13-58-58](https://github.com/WikiTeq/mediawiki-pages-News/assets/62721134/daa7207a-e2cb-4de0-a388-c45bff5f897c)



