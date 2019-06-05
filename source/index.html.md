---
title: searchcode API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - json

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

search: true

includes:
  - _errors
---

# Introduction

searchcode offers a free comprehensive API.

Various examples of how to use the API can be found at [DuckDuckHack's Github repo](https://github.com/duckduckgo/zeroclickinfo-spice) (look inside `share/spice/code_search` and `share/spice/search_code` for examples) and at [Varemeno's Doc-Finder](https://github.com/varemenos/Doc-Finder). Working examples include and [Doc-Finder](http://docfinder.aklp.gr/).

Are you using searchcodes API? Let us know and we will include your site / application as part of our showcase

# Code Index

Queries the code index and returns at most 100 results. All filters supported by searchcode are available. These include src (sources), lan (languages) and loc (lines of code). These work in the same way that the main page works. See the examples for how to use these.

If the results list is empty, then this indicates that you have reached the end of the available results. To fetch all results for a given query, keep incrementing 'p' until you get a page with an empty results list. Note you can reach further into the results by setting per_page to 100.

### JSON

`https://searchcode.com/api/codesearch_I/?q=[searchterm]&p=[page]&per_page[per_page]&lan=[lan]&src=[src]&loc=[loc]&loc2=[loc2]`

### JSONP

`https://searchcode.com/api/jsonp_codesearch_I/?q=[searchterm]&p=[page]&per_page[per_page]&lan=[lan]&src=[src]&loc=[loc]&loc2=[loc2]&callback=[myCallback]`

> Result (JSON)

```json
{
  "matchterm": "soup",
  "previouspage": 0,
  "searchterm": "soup",
  "query": "soup",
  "total": 4,
  "page": 0,
  "nextpage": 1,
  "language_filters": [
    {
      "count": 3,
      "id": 3,
      "language": "HTML"
    },
    {
      "count": 1,
      "id": 123,
      "language": "JSON"
    },
    {
      "count": 1,
      "id": 19,
      "language": "Python"
    }
  ],
  "source_filters": [
    {
      "count": 5,
      "source": "Github",
      "id": 2
    }
  ],
  "results": [
    {
      "repo": "https://code.google.com/p/html5lib/",
      "linescount": 239,
      "location": "/python3/html5lib/treebuilders",
      "name": "html5lib",
      "language": "Python",
      "url": "https://searchcode.com/codesearch/view/24862775/",
      "md5hash": "b8e6b1d1f53d5e4f87995ebeb35b358c",
      "lines": {
        "4": "",
        "5": "warnings.warn(\"BeautifulSoup 3.x (as of 3.1) is not fully compatible with html5lib and support will be removed in the future\", DeprecationWarning)",
        "6": "",
        "7": "from BeautifulSoup import BeautifulSoup, Tag, NavigableString, Comment, Declaration",
        "8": "",
        "139": "class TextNode(Element):",
        "140": "    def __init__(self, element, soup):",
        "141": "        _base.Node.__init__(self, None)",
        "142": "        self.element = element",
        "143": "        self.soup = soup",
        "144": "    ",
        "150": "        if namespaceHTMLElements:",
        "151": "            warnings.warn(\"BeautifulSoup cannot represent elements in any namespace\", DataLossWarning)",
        "152": "        _base.TreeBuilder.__init__(self, namespaceHTMLElements)",
        "154": "    def documentClass(self):",
        "155": "        self.soup = BeautifulSoup(\"\")",
        "156": "        return Element(self.soup, self.soup, None)"
      },
      "id": 24862775,
      "filename": "soup.py"
    }
  ]
}
```

### Query Parameters

| Parameter | Default | Description                                                                                                                                                                                                                                                                                                                                                                                                                        |
| --------- | ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| q         |         | Search Term<br>The following filters are textual and can be added into query directly:<br><ul><li>Filter by file extention **ext:EXTENTION** `E.g. "gsub ext:erb"`</li><li>Filter by language **lang:LANGUAGE** `E.g. "import lang:python"`</li><li>Filter by repository **repo:REPONAME** `E.g. "float Q_rsqrt repo:quake"`</li><li>Filter by user/repository **repo:USERNAME/REPONAME** `E.g. "batf repo:boyter/batf"`</li></ul> |
| p         |         | result page starting at 0 through to 49                                                                                                                                                                                                                                                                                                                                                                                            |
| callback  |         | callback function (JSONP only)                                                                                                                                                                                                                                                                                                                                                                                                     |
| per_page  |         | number of results wanted per page max 100                                                                                                                                                                                                                                                                                                                                                                                          |
| lan       |         | allows filtering to languages supplied by return types. Supply multiple to filter to multiple languages.                                                                                                                                                                                                                                                                                                                           |
| src       |         | allows filtering to sources supplied by return types. Supply multiple to filter to multiple sources.                                                                                                                                                                                                                                                                                                                               |
| loc       |         | filter to sources with greater lines of code then supplied int. Valid values 0 to 10000.                                                                                                                                                                                                                                                                                                                                           |
| loc2      |         | filter to sources with less lines of code then supplied int. Valid values 0 to 10000.                                                                                                                                                                                                                                                                                                                                              |

### **EXAMPLES**

### JSON

`https://searchcode.com/api/codesearch_I/?q=soup&p=1&per_page=100`

### Example Language Filter (Java and Javascript)

`https://searchcode.com/api/codesearch_I/?q=test&lan=23&lan=22`

### Example Source Filter (Bitbucket and CodePlex)

`https://searchcode.com/api/codesearch_I/?q=test&src=3&src=5`

### Example Lines of Code Filter (Between 500 and 1000)

`https://searchcode.com/api/codesearch_I/?q=test&loc=500&loc2=1000`

### Example (JSONP)

`https://searchcode.com/api/jsonp_codesearch_I/?q=soup&p=1&callback=myCallback`

# Legalese

## Disclaimer

The searchcode API is provided "as is" and on an "as-available" basis. All care is taken but there is no warranty provided that the API will be error free or that access will be continuous or uninterrupted.

## Liability

In no event will searchcode be liable with to respect to any special, incidental, or consequential damages; the cost of procurement of substitute products or services; or for interruption of use or loss or corruption of data.

## Conditions

The only condition of using the searchcode API is to provide a clickable link attributing searchcode as the source. No rate limiting implemented unless abuse is detected. Operate as Bill and Ted would and "Be excellent to each other".

# Corporate Usage

Generally speaking corporate usage using the searchcode API is not an issue. However if you are running a company with business critial functions using the API and want to ensure the service is still running next week, contact Ben via bboyte01@gmail.com and we can work some form of commercial licence out.
