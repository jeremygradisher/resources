A "Google dork” is an advanced Google search technique. “Google dorking” (aka “Google hacking”) is the activity of performing advanced searches on Google. You can combine different Google dorks to comb data otherwise inaccessible to ordinary users of Google search.

On a browser, if you make too many Google searches in a short time, Google requires that you unscramble garbled letters in an image called a captcha before you can proceed. Captcha completion can frustrate end users like you, but Google servers must nip denial-of-service cyberattacks in the bud.

```
site: - restricts search results to the site or domain.
inurl: - searches for the specified term in the URL.
intitle: - searches for the specified term in the page title.
intext: - searches for the specified term in the text of a page.
filetype: - searches for specific file types.
filetype:, ext: Unlike most other dorks, this requires additional keywords in the search bar or will return no results.
link: - searches for external links to pages.
info: - presents some information that Google has about a web page.
cache: - shows the version of a web page as it appeared when Google crawled the site last time.
related: - lists web pages that are similar to the web page.
stock: - searches for a stock ticker symbol.
@: Restrict search to a particular social platform.It supports popular platforms such as Facebook, Twitter, YouTube, and Reddit.A downside is it’s not as precise as the “site:” dork.
define:	Return definitions of a word or phrase	Compare define:privacy and a plain search on privacy.
stocks:	Check the financial activity of a particular stock	stocks:TWTR (Twitter), stocks:gm (General Motors), stocks:pfizer
movie:	Return information about any movie with the given title	Compare movie:”phantom of the opera” and “phantom of the opera”.
source:	Find reports from a Google News source.	source:npr
after:    Return results after a given date	after:2019-01-01
before:    Return results before a given date	before:2019-01-01
~:    Include synonyms of a given word	~privacy
-:    Exclude a word or phrase from results	Compare privacy and -privacy.
related:    Find pages related to a given page	related:https://www.npr.org
```

Here are a few examples of how these operators can be used:
```
site:wikipedia.org
intitle:"index of"
inurl:admin
filetype:pdf "history of the internet"
intext:"password" filetype:txt
link:www.example.com
@twitter pentest
@youtube google dorking
define:privacy
```


There is an extensive list here: https://www.stationx.net/google-dorks-cheat-sheet/
Here is a list of exploits: https://www.exploit-db.com/google-hacking-database




