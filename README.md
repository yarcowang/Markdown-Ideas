# Ideas of Markdown Enhanced
[Markdown][] is original defined by John Gruber, and soon become widely used. (more detail on [Markdown-wiki][]).  
[Markdown-github][] add some awesome rules to enhance the writting on github.

When I'm using markdown, I sometimes feel it lacks some features i want. (Maybe you also have the same feelings).  
But you know, it is widely used and you can not force others to agree with you. That's why I collect the ideas here, maybe it is useful for those developing Markdown editors.

Current ideas are listed here:  
* [Markdown Options](#markdown-options)
* [Markdown Chart](#markdown-chart)
* [Enhanced Attachments: Using MessagePack](#enhanced-attachments-using-messagepack)

## Markdown Options
Markdown options is a way to extend markdown by external markdown engine. Let's make an example to clarify this idea.

For example, sometimes I want the markdown engine could output the indexed version of the html for long article; but sometimes, I dont want it. So there could be an option to indicate it. My idea is using something like reference link grammar, but begin with `@`:

    @index: true

That means I wish the external tool could create an indexed version pdf/html for me. But whether it can do or can not do that depends on the external tool itself. For those don't support `@index` grammar, just ignore it.

Other cases, maybe it can also be used in coloring the elements. For example:

    @color-red: red
    @color-red: #900

Then you can reference the element as red color.

    Some Title@color-red
    ----
 
## Markdown Chart
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

## Enhanced Attachments: Using MessagePack
In markdown, we can display images either using external links or data url. But it is quite limited.

If the requirement is we want a all-in-one solution, the data url solution is messed up. So, my idea is using Text with MessagePack as attachement. (MessagePack itself can also be used with other Text format).

The basic format is:

    ```
    ... Here is the Text (Markdown in this case) ...
    \x1E \x1E ---- two \x1E for seperating text and binary data
    [Optional Class Tag:] ... MessagePack binary data goes here ....
    \x1E ---- Another section
    [Optional Class Tag:] ... MessagePack binary data goes here ....
    ```

For example:

    ```
    # Title
    This is a simple text.
    \x1E \x1E 
    {"user": "yarco", "image1":"data:image/png;base64,...", "image2":"data:image/png;base64,...}
    \x1E 
    Avatar:{"image1":"data:image/png;base64,"width":"200px",...}
    ```

You can reference the image in markdown as:

    ![image1](data:with/messagepack,"image1")

or

    ![image1](data:with/messagepack,Avatar:"image1")


[Markdown]:http://daringfireball.net/projects/markdown/ "original markdown"
[Markdown-wiki]:http://en.wikipedia.org/wiki/Markdown "markdown wikimedia intro"
[Markdown-github]:https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax

[usecase in wikimedia]:http://en.wikipedia.org/wiki/Use_Case_Diagram "usecase in wikimedia"
[activity in wikimedia]:http://en.wikipedia.org/wiki/Activity_diagram "activity in wikimedia"
[class in wikimedia]:http://en.wikipedia.org/wiki/Class_diagram "class in wikimedia"
[usecase example]:https://raw.github.com/Yet-Another-Org/Markdown-Enhanced-Ideas/master/usecase.png "usecase example"
[activity example]:https://raw.github.com/Yet-Another-Org/Markdown-Enhanced-Ideas/master/activity.png "activity example"
[class example]:https://raw.github.com/Yet-Another-Org/Markdown-Enhanced-Ideas/master/class.png "class example"
[object example]:https://raw.github.com/Yet-Another-Org/Markdown-Enhanced-Ideas/master/object.png "object example"