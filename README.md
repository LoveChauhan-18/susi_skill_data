# susi_skill_data

This is the storage place for SUSI skills. It is for now a temporary solution for a wiki-like skill editing service that we want to create in the near future.

## Installation

This repository must be cloned along with https://github.com/fossasia/susi_server to make it available to SUSI.AI.  
The production platform of http://susi.ai will do a `git pull origin master` every minute. That means, every change will be available very soon.

## Create a new skill

Creation of a new skill is easy, DO NOT PANIC!

### Learn the skill language

Read https://github.com/fossasia/susi_skill_cms/blob/master/docs/Skill_Tutorial.md

### Write a new skill

To create a new skill, please choose "Create Skill" at https://susi.ai.

## License

All new skills shall be licensed under CC0  
https://creativecommons.org/publicdomain/zero/1.0/deed.de  

We choose this data because many skills may be similar to knowledge as published by wikidata.org which licenses its data under CC0 as well.  
If you take skill data from non-cc0 sources, you may do so but please also copy the license information.

---

# Using Yahoo Query Language (YQL) with SUSI

Yahoo Query Language (YQL) can be used to extract structured data from HTML and XML sources.

Sometimes useful data is hidden inside HTML tables or XML feeds. YQL allows querying such data using SQL-like syntax and returning results in JSON format, which can then be used inside SUSI skills.

---

## Example YQL Query

```sql
SELECT * FROM html 
WHERE url="https://example.com"
AND xpath="//table"
```

This query fetches table data from the webpage and converts it into structured JSON output.

---

## Integration in SUSI Skill

The YQL query must be URL-encoded when used inside the API URL.

### Encoded Version of Query

Original Query:
```
SELECT * FROM html WHERE url="https://example.com" AND xpath="//table"
```

URL Encoded Query:
```
SELECT%20*%20FROM%20html%20WHERE%20url%3D%22https%3A%2F%2Fexample.com%22%20AND%20xpath%3D%22%2F%2Ftable%22
```

### SUSI Skill Snippet

```json
{
  "url": "https://query.yahooapis.com/v1/public/yql?q=SELECT%20*%20FROM%20html%20WHERE%20url%3D%22https%3A%2F%2Fexample.com%22%20AND%20xpath%3D%22%2F%2Ftable%22&format=json",
  "path": "$.query.results"
}
```

---

### Important Notes

- Always close quotation marks properly.
- Always wrap code examples inside fenced code blocks.
- Always URL-encode the YQL query before using it inside the API URL.
- Spaces must be replaced with `%20`
- Quotes `"` must be replaced with `%22`
- `/` becomes `%2F`
- `:` becomes `%3A`

---

Now your YQL documentation example is properly formatted, readable, and copy-paste safe.
