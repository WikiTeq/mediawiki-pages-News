# News package

Content author is @wikivisor

# Requirements

* SemanticMediaWiki
* PageForms
* ParserFunctions (with `$wgPFEnableStringFunctions = true;`)
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

Once imported, navigate to `Project:All_news`
