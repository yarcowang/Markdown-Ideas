Markdown Enhanced Ideas
====
[markdown][] is original defined by John Gruber, and soon become widely used. (More detail on [markdown-wiki][]).

[markdown-github][] add some awesome rules to enhance the original definitions.

When i'm using markdown, i feel it lacks some features i want. (Maybe you also have same feelings).  
But you know, it is widely used and you can not create another tool and make it as a standard.(Needless to say i don't know how to)

That's why i put it here, to collect ideas to enhance markdown standard. And it is free to add more from others who would like to join. 

And i think it is also good to those who are developing markdown engines.

Here are the ideas (from me for now):

* markdown options
* markdown chart

For more details and explanations, see below.


Markdown Options
----
Markdown options is a way to extend markdown by external markdown engine. Let's make an example to clarify my idea.

For example, sometimes i want the markdown engine could output index version of the html for long article; but sometimes, i dont want it. So there should be an option to indicate it. My idea is using something like reference link grammar, but begin with `@`.

For example:

    @index: true

That means i wish the external tool could create an index version pdf/html for me. But whether it can do or can not is only based on the external tool. For those don't support `@index`, just ignore it.

And also, it may good for adding colors on elements. For example:

    @color-red: red
    @color-red: #900

Then you can reference an element as red color.

    Some Title@color-red
    ----
 
Well, this title may have red color. (whether it is background or font also based on the external engine)

If you really want to write down `@` and not a reference, you could escape it just like "\\ \` \* ..." defined in original markdown grammar.

Markdown Chart
----
All charts are defined just like you are writting normal code. For example:
		
    ```js
    document.write('hi');
    ```

This is how we write markdown chart. (For now i just want simple uml charts)

    ```uml-<chart type>
    …details based on different chart definitions...
    ```
    
Here are the blueprint for the uml charts:

* usecase
* activity
* class
* object

### Usecase
Explanation visit [usecase in wikimedia][].

The syntax is as following:

    ```uml-usecase "a simple cms"
    admin | user | manage news, manage user
    user | guest | read news, sign out
    guest | | sign up, sign in
    ```
		
should generate:

![usecase example]

Grammar:

    role | parent role | actions...

Enhanced ideas:

* add option color, for example, if i want user role have an red color, i could do `user@color-red | login@color-red | read news ...`
* the chart could be in data url format, something like `data:image/gif;base64,...` (can it be used in pdf? Not sure)

### Activity
Explanation visit [activity in wikimedia][].

To make things simple, there's no decisions in activity chart.

    ```uml-activity "search user then send message"
    search a special user | edit message | send message both in sms and email
    search a special user | if not found, make edit message button disabled    
    ```
		
should generate:

![activity example]

Grammar:

    activity | activity | activity...

### Class
class definition here is not exactly the same as in [class in wikimedia][]. It only describes generalization.

    ```uml-class
    person | admin,user,guest
    ```

![class example]

Grammar:

    parent | son,son,son...

### Object
object only contains attributes you want to use. (then it can also describe table).

    ```uml-object
    person | id,name,roles
    user | id,name,roles,ctime
    ```

should result:

![object example]

Grammar:

    object | attribute,attribute...

But attribute here can also be written as method. Just change it to `method()` or even more add `+method()` to indicate it is a static method.

Contact
----
You may want to contact [me][] through <yarco.wang@gmail.com> according to the ideas. Programming related topics are also welcomed.

timezone: GMT+0800

[me]:http://bbish.net

[markdown]:http://daringfireball.net/projects/markdown/ "original markdown"
[markdown-wiki]:http://en.wikipedia.org/wiki/Markdown "markdown wikimedia intro"
[markdown-github]:http://github.github.com/github-flavored-markdown/

[usecase in wikimedia]:http://en.wikipedia.org/wiki/Use_Case_Diagram "usecase in wikimedia"
[activity in wikimedia]:http://en.wikipedia.org/wiki/Activity_diagram "activity in wikimedia"
[class in wikimedia]:http://en.wikipedia.org/wiki/Class_diagram "class in wikimedia"
[usecase example]:https://raw.github.com/Yet-Another-Org/Markdown-Enhanced-Ideas/master/usecase.png "usecase example"
[activity example]:https://raw.github.com/Yet-Another-Org/Markdown-Enhanced-Ideas/master/activity.png "activity example"
[class example]:https://raw.github.com/Yet-Another-Org/Markdown-Enhanced-Ideas/master/class.png "class example"
[object example]:https://raw.github.com/Yet-Another-Org/Markdown-Enhanced-Ideas/master/object.png "object example"