# News package

`Package` is the installable set of MediaWiki pages. The News package provides a set of input forms and templates that make it easy to add and manage `News` - wiki pages announcing current events.

Content author is @wikivisor

# Requirements

## Extensions

* [SemanticMediaWiki](https://www.semantic-mediawiki.org/wiki/Help:Installation/Quick_guide)
* [PageForms](https://www.mediawiki.org/wiki/Special:MyLanguage/Extension:Page_Forms/Download_and_installation)
* [ParserFunctions](https://www.mediawiki.org/wiki/Special:MyLanguage/Extension:ParserFunctions)
* [SemanticResultFormats](https://www.semantic-mediawiki.org/wiki/Extension:Semantic_Result_Formats/Installation) (for `tagcloud` format )
* [MagicNoCache](https://www.mediawiki.org/wiki/Special:MyLanguage/Extension:MagicNoCache)
* [PageExchange](https://www.mediawiki.org/wiki/Extension:Page_Exchange)

## Configuration settings

* `$wgRestrictDisplayTitle = false;`
* `$wgPFEnableStringFunctions = true;`

When news length exceeds the default number of characters (N = 1000), you'll get a warning saying, "_Error: String exceeds N character limit._" Then you might want to bump the string length limit:

* `$wgPFStringLengthLimit = 10000;`

# Setup

* add the following to the bottom of your `LocalSettings.php`: `$wgPageExchangePackageFiles[] = 'https://raw.githubusercontent.com/WikiTeq/mediawiki-pages-News/master/page-exchange.json';`
* navigate to `Special:Packages` and install the package
* run `php maintenance/runJobs.php`

# Usage

Once imported, navigate to `Project:All_news`. This page is created using the `{{All news|all}}` template call and displays all ever-created news categorized by the year of publication. 

![Screenshot from 2023-08-14 13-29-30](https://github.com/WikiTeq/mediawiki-pages-News/assets/62721134/63a9d155-43ef-4388-80bc-914e1f47d838)

Tags and feeds can further filter news:

![Screenshot from 2023-08-14 13-30-03](https://github.com/WikiTeq/mediawiki-pages-News/assets/62721134/db6564b9-2c23-4f00-b297-eec7c8aba8cb)

The size of the tag link font varies depending on the number of news using this tag. Feeds and tags are independent dimensions that can be used for news classification.

The most common use case is to deliver the "actual" news rather than the full history of the news posts. By "actual", we mean news, the visibility period of which includes the current date. The actual news can be delivered to any page using `{{All news|actual}}` template call and wrapped to comply with the wiki's overall styling: 

![Screenshot from 2023-07-02 14-05-19](https://github.com/WikiTeq/mediawiki-pages-News/assets/62721134/26e57994-5746-4cf6-b79a-5a4dd5b550ae)

News can be created by clicking the `Add news` button. A form with necessary controls and inputs is provided:

![Screenshot from 2023-08-14 13-45-43](https://github.com/WikiTeq/mediawiki-pages-News/assets/62721134/08438298-0681-4223-862f-1e530f078ee6)

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
