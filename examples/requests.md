# Python requests library
In python libraries are referred to as modules
## What is an HTTP request?
#### An http request could be considered as an exchange of information between a client and server.  

## Example 
Let's say that you're using instagram, when you visit the website or the app you're making a request to the instagram server to send you information about your instagram feeds. Another example would be if you were to post something on instagram, you're making a request to the server to accept your picture,text, or whatever is included in the post.
<br>

## Common HTTP Methods
- Get
    - Get data from the server. Like looking up a user on instagram
- Post
    - Uploading data to the server. Uploading a post to any type of social media platforms.
- Patch
    - Request to modify data to the server. Editing titles, text, or tags on your posts.
- Delete
    - As the word states, delete data. Deleting a post from instagram, deleting message on discord.

In our case we'll most likely only be using the `Get` and `Post` HTTP methods
<br>
<br>
## Installing the library/module


To install the module simply open up a command prompt or terminal and type the following.  
#### NOTE: Make sure to add the scripts folder from python to your environment path if the command below doesn't work.
`pip install requests`



## Using the module

Let's tart off by importing the module and making a simple get request.

```python
import requests as rq
#you can rename the package inside your code by adding the keyword as followed by it's new name.

url = 'https://catfact.ninja/fact
#this website returns a random cat fact.



#Make a get request to the following link
data = rq.get(url)
#This will return an object with the type Response


print(data)
#This will return <Response [200]> if everything went well. The 200 means that everything went well

#We can see what type of attributes the object has by doing dir(data)
print(dir(data))
#This should display something like this 
['__attrs__', '__bool__', '__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__enter__', '__eq__', '__exit__', '__format__', '__ge__', '__getattribute__', '__getstate__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__nonzero__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__setstate__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', '_content', '_content_consumed', '_next', 'apparent_encoding', 'close', 'connection', 'content', 'cookies', 'elapsed', 'encoding', 'headers', 'history', 'is_permanent_redirect', 'is_redirect', 'iter_content', 'iter_lines', 'json', 'links', 'next', 'ok', 'raise_for_status', 'raw', 'reason', 'request', 'status_code', 'text', 'url']

#You can ignore the attributes starting and ending with double underscore (__) for now . Feel free to experiment around with the attributes to learn more about them or ask me. 
```

## Requests attributes and methods
We'll mainly be working on the following attributes, methods and what they do.
A `method` is basically another word for `function`

- url
    - attribute
    - returns the url that we used to send the request. In our case, the value of the variable `url` 
    - `print(data.url)`
    - `https://catfact.ninja/fact`
- text
    - attribute
    - returns `str` value of the response 
    - `print(data.text)`
    - `{"fact":" A cat only has the ability to move their jaw up and down, not side to side like a human can.","length":93}`
- status_code
    - attribute
    - returns the status code of the response in `int` value
    - `print(data.status_code)`
    - `200`
- ok
    - attribute
    - returns `True` if status code is `200` or `201` meaning everything went well
    - `print(data.ok)`
    - `True`
- json
    - method
    - converts the response data into a json format if available, otherwise it'll cause an error
    - `print(data.json())`
    - `{"fact":" A cat only has the ability to move their jaw up and down, not side to side like a human can.","length":93}`
    - the return value of text and json may look the same but they are different data types
- content
    - attribute
    - returns the raw binary contents of the response 
    - `print(data.content)`
    - `b'{"fact":"A cat\'s brain is more similar to a man\'s brain than that of a dog.","length":66}'`
    - If the returned value is an image we can write the image file into our directory and save it with the built-in library `open()` which there will be an example of later.

## Accessing the value of the json data.

```python

#convert it into json data type or dict in the case of python
#You can check the data type of a variable or a value via print(type(data))
json_data = data.json()
random_fact = json_data['fact']
print(random_fact)

#Your fact may be different because it's random.

#A cat only has the ability to move their jaw up and down, not side to side like a human can.
```

## Writing an image  

Let's say now that we have an image as a response from our get request.


We can download the image and save it on our computer with the following code
```python
import requests as rq  

img= rq.get('https://ddragon.leagueoflegends.com/cdn/11.24.1/img/profileicon/5093.png')

with open("edward_gaming_icon.png","wb") as file:
    file.write(img.content)


#the following image will be saved in the directory that the python code ran.
#Or you can specify a directory via r"D:\path\to\dir\edward_gaming_icon.png"

```

The image should look like this.  
<img src="edward_gaming5093.png" width="250">