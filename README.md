Markdown Chart
==============
This is a blueprint to define [markdown][] ( see more in [markdown-wiki][] and [markdown-github][] ) simple embed chart rules.

It focus on simple and easy resolution. If you want complicated draw, then you could use an external tool to generate it for you.

Common
------
All charts are defined just like you are writting normal code. For example:
		
		```js
		document.write('hi');
		```

This is how we write code example in our markdown text. Charts are defined in the same way.

		```uml-<chart type>
		…details...
		```

This is the way you write embed chart.

Currently this blueprint only defines the following chart:

* usecase

Usecase
-------
see more [usecase in wikimedia][].

The syntax is as following, just like writting a table:

		```uml-usecase
		roles | actions
		------|--------
		admin | login | manage user | manage news | logout
		user | login | read news | logout
		guest | read news
		```
		
should generate:

![usecase example]

There could be some enhanced features in future:

* action merge, some action could be merged into one. 
* add color generating
* external png? embed svg?



[markdown]:http://daringfireball.net/projects/markdown/ "original markdown"
[markdown-wiki]:http://en.wikipedia.org/wiki/Markdown "markdown wikimedia intro"
[markdown-github]:http://github.github.com/github-flavored-markdown/

[usecase in wikimedia]:http://en.wikipedia.org/wiki/Use_Case_Diagram "usecase in wikimedia"
[usecase example]:https://raw.github.com/yarcowang/mdchart/master/usecase.png "usecase example"