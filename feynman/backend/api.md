# API 

In this feynman note file we will discuss what API's are in programming and why are they important.

### What are API's ?

So what exactly are API's? Basically when two computer programs talk to each other (and specifically try to access each others data) they need a communucation channel. That channel is what we call an API is. You first have to understand that API is an nebolous word. Just like UX/UI an API is basically standing for application programming interface. Think about UI and UX for a second. You can do these concepts in a lot of different ways, you can use photoshop, sketch, figma or you can literally do it on a piece of paper with pencils and ereasers.

Just Like UI/UX you can design and implement API's on many different ways. For example you can deisgn them with frameworks, yourself natively with code files and good documentation :) or you can attach a piece of CD to a paper that has a hand written note that is guiding how to access ande connect your program to the data and program inside the CD.

### Why is this important ?

I mean why wouldn't you want your program to use other programs data. As you can imagine if you wanted to build a weather casting service, you would have to first get the data of the clouds ... in order to get that data you have to send sattelites to space to collect that data. As you can see it is not logical to do any of these above because we can already get the data of the weather from established companies in the industry. All you have to do is connect your program to their program with an API. An api just enhances the productivity and usability of your program.

### How to use an API ?

As we have mentioned above you can design your API in any way, shape or form you would like however, we are living in the real world. As you can imagine at first, everybody developed API's the way they wanted to but that caused problems because you had to design a new API format for every new program that wanted to connect to your own program. 

That is why the industry standartized the way we wrote APIs. Even though you can write a lot of APIs in various different programs lets give an example from web api development. Since web is used a lot by the consumers, programmers had to standartize the api writing and the data that is exchanged between the programs. That is why they developed something called JSON. It is basically a standart way to store and pass data because most of the applications are written with different langauges. With this way a python bacekend can talk to a java backend with the same JSON notation because both web applications will have to use javascript on the client side.


### Who Creates Public, Web-Based APIs?

Large tech companies, especially social media companies frequently make their aggregate data available to the public, but APIs are also maintained by government organizations, conferences, publishing houses, software startups, fan groups, eSports leagues and even individuals, in order to share anything from social media content to trivia questions, rankings, maps, song lyrics, recipes, parts lists and more. In short, any person or organization that collects data might have an interest in making that data available for use by a different app.

# REST

The main thing about REST is that it's stateless. That means that it doesn't maintain some sort of session or anything like that. So you shouldn't need to do a handshake or anything. If you send a request with the right headers then you will get a response (though those headers might include some sort of authentication).

REST should not return a user interface either - only data.

e.g. you don't get a bunch of java-script and HTML to be rendered in order to interface with the API - you get data in some form, and the details of the interface are up to your application (which indeed may get HTML and JS or other interface from some other source).

In a colloquial sense, REST apis generally mean:
- You get JSON data back
- You correctly use HTTP Methods
  - GET should only get data, not change the state of the data
  - POST should only create a new record
  - PUT should only update all the fields of a record
  - PATCH should only update some of the fields of a record
  - DELETE should only delete records

There are other things that could be used instead of JSON or HTTP methods and still be RESTful, but generally this is what it used.
e.g.:
```
GET api/movies/1
```
returns
```
{
    "id": 1,
    "name": "Con Air",
    "reviews": [
        {
            "id": 1,
            "content": "A triumph"
        }
    ] 
}
```
and for post
```
POST api/movies/1/reviews

BODY:
{
    "content": "Best movie ever"
}
```

# Authentication
