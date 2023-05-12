# News package

Content author is @wikivisor

# Requirements

* SemanticMediaWiki
* PageForms
* ParserFunctions (with `$wgPFEnableStringFunctions = true;`, depending on news length you may want to bump the string length limit `$wgPFStringLengthLimit = 10000;`)
* SemanticResultFormats (for tagcloud)
* MagicNoCache
* PageExchange or PagePort

# Setup

## via PagePort

* download the repository
* run `php extensions/PagePort/maintenance/importPages.php --source ~/pages-News`

## via PageExchange

* add the following to the bottom of your `LocalSettings.php`: `#$wgPageExchangePackageFiles[] = 'https://raw.githubusercontent.com/WikiTeq/mediawiki-pages-News/master/page-exchange.json';`
* navigate to `Special:Packages` and install the package
* run `php maintenance/runJobs.php`

# Usage

Once imported, navigate to `Project:All_news`.
