This is a prototype of Jekyll-based hypermedia API client.

It consumes data in collection/json format from an external URL.
The URL is configured in jekyll-site/_config.yml, at jekyll_get.json

We used collection/json out put, produced by [https://github.com/switzersc/api-in-a-box](api-in-the-box) by Shelby Switzer. Sample JSON output in collection/json format is is samples/resources.json.zip

The JSON data is loaded upon Jekyll server startup, by means of "jekyll_get" plugins.

Liquid template, located in
- jekyll-site/_posts/2017-09-14-hackaton.markdown
- jekyll-site/_posts/2017-09-14-hackaton2.markdown

are responsible for rendering JSON data into an HTML table.

External JS/CSS tool turns the raw HTML table into a browsable interface, featuring search, paging, sorting.

Jekyll server can be started by this command:

```
cd jekyll-site
bundle exec jekyll serve
```

Jekyll needs to be installed as a pre-requisite

The actual client pages are at
- http://127.0.0.1:4000/jekyll/update/2017/09/14/hackaton.html
- http://127.0.0.1:4000/jekyll/update/2017/09/14/hackaton2.html

Collection/json is agnostic to actual object model, which means that one collection can contain a mix of object of different types with different properties

The first page only loads object of the same type as the first one in the collection, ignoring all other objects

The second page identifies all types of objects in the collection, using FILE_SOURCE properties,  where api-in-the-box puts the source CSV file. Then it renders as many separate tables, as there are different object types.

The tool is a merely a hackaton experimentation and is not meant to be used in practice.
