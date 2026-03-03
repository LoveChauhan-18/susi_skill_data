# susi_skill_data
This is the storage place for susi skills. It is for now a temporary solution for a wiki-like skill editing service that we want to create in the near future.

## Installation
This repository must be cloned along https://github.com/fossasia/susi_server to make it available to SUSI.AI.
The production platform of http://susi.ai will do a `git pull origin master` every minute. That means, every change will be available very soon.

## Create a new skill
Creation of a new skill is easy, DO NOT PANIC!

### Learn the skill language
Read https://github.com/fossasia/susi_skill_cms/blob/master/docs/Skill_Tutorial.md.

### Write a new skill

To create a new skill, please choose "Create Skill" at https://susi.ai.

## License
All new skills shall be licensed under CC0 https://creativecommons.org/publicdomain/zero/1.0/deed.de 
We choosed this data because many skills may be similar to knowledge as published by wikidata.org which licenses it's data under CC0 as well.
If you take skill data from non-cc0 sources, you may do so but please also copy the license information.

## Using Yahoo Query Language (YQL) with SUSI

Yahoo Query Language (YQL) can be used to extract structured data from HTML and XML sources.

Sometimes useful data is hidden inside HTML tables or XML feeds. YQL allows querying such data using SQL-like syntax and returning results in JSON format, which can then be used inside SUSI skills.

### Example YQL Query
select * from html where url="http://example.com
" and xpath="//table"


This query fetches table data from the webpage and converts it into structured JSON output.

### Integration in SUSI Skill

In a SUSI skill file:
"url": "https://query.yahooapis.com/v1/public/yql?q=YOUR_QUERY&format=json
",
"path": "$.query.results"


The `path` field helps extract the required data from the returned JSON response.

### Note

YQL support may vary depending on Yahoo API availability. Alternative APIs or direct JSON endpoints are recommended where possible.
