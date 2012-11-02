Markdown Chart
==============
This is a blueprint to define [markdown][] ( see more in [markdown-wiki][] and [markdown-github][] ) simple embed chart rules.

It focus on simple and easy resolution. If you want complicated draw, then you could use an external tool to generate it for you.

Who define the Rule?
--------------------
I'm [Yarco][yarco], an anonymous and invisible man. But you could also join and feel free to edit.

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
* activity
* class
* object

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

Activity
--------
see more [activity in wikimedia][].

The syntax is as following:

		```uml-activity
		title | condition | false goto
		------|-----------|-----------
		begin admin: | user logined? | login
		manage news |
		login: | pass login? | error page
		manage news |
		error page: |
		```
		
should generate:

![activity example]

Can be enhanced also. (arrow needed)

Class
-----
class definition here is not exactly the same as in [class in wikimedia][]. It only describes generalization.

		```uml-class
		parent | sons
		-------|-----------
		person: | admin | user | guest
		```

![class example]

Object
------
object only contains attributes you want to use. (then it can also describe table).

		```uml-object
		name | attributes
		-----|--------------
		person | id | name | roles
		user | id | name | roles | ctime
		```

should have:

![object example]



[yarco]:http://bbish.net

[markdown]:http://daringfireball.net/projects/markdown/ "original markdown"
[markdown-wiki]:http://en.wikipedia.org/wiki/Markdown "markdown wikimedia intro"
[markdown-github]:http://github.github.com/github-flavored-markdown/

[usecase in wikimedia]:http://en.wikipedia.org/wiki/Use_Case_Diagram "usecase in wikimedia"
[activity in wikimedia]:http://en.wikipedia.org/wiki/Activity_diagram "activity in wikimedia"
[class in wikimedia]:http://en.wikipedia.org/wiki/Class_diagram "class in wikimedia"
[usecase example]:https://raw.github.com/yarcowang/mdchart/master/usecase.png "usecase example"
[activity example]:https://raw.github.com/yarcowang/mdchart/master/activity.png "activity example"
[class example]:https://raw.github.com/yarcowang/mdchart/master/class.png "class example"
[object example]:https://raw.github.com/yarcowang/mdchart/master/object.png "object example"