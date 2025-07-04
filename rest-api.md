---
layout: default
---
Just here for the code? Click [here](#the-code)

# The REST API Protocol

## Communication is key
Not too dissimilar to two people talking, applications need a stardard language(in tech lingo this is called a "protocol") in order to effectively communicate with one another. Just like two people from two very different cultures and backgrounds speaking one common language, applications with two completely different underlying technologies(e.g. programming language, infrastrucutre, libraries) can interact with one another as long as they use the same dialect.

## Why REST?
With an ever growing list of programming languages and infrastrucutre types, the need for a protocol that can work in today's internet-heavy world _regardless_ of what two applications are built with is greater than ever. Since each programming lanuage has its own compiler, trying package up a Java code along with a Python code will never work. Packaged code certainly still exists in the form of SDKs, but a developers have to rewrite the code in _all_ of the programming langauges they want to support. For example the AWS SKD has boto3 for Python, aws-sdk for JavaScript, and software.amazon.awssdk for Java. While language-specific code has its advantages, being able to write an application that _any_ application can consume regardless of its underlying language save a lot of time and resources.

...Enter REST(Representational State Transfer). At its core, the REST architecture pattern builds on top of the HTTP protocol by defining a stateless, client-server architecutre style for easy manipulation of data. By leveraging the already exisitng HTTP protocol, data gets transferred over the internet and can then be easily trnaslated by the cosuming application. As long as the data being sent by application 1 is in the format that application 2 is expecting, the interaction should be seamless. 

## How to speak REST
### Definitions
> Method - action being done to request <br/>
> Route - everything after the forward slash in the URL <br/>
> Request body - where the content of the data lives(in JSON format)
> URL paramaters - dynamic value in the URL route(ex. /users/user123, the url parameter is the user ID user123) <br/>
> Query parameters - way of applying query when retrieving data(ex. /users/?limit=100)


### Methods
| Method | Definition           | Example |
|:-------|:---------------------|:--------|
| GET    | For retriving data   | GET /api/user/user123  |
| POST   | For creating data    | POST /api/user <br> {userId: "user123", firstName: "Bill"} |
| PUT    | For updating an enitre data element | PUT /api/user/user123 <br> {userId: "user124", firstName: "Bob" } |
| DELETE | For deleting data    | DELETE /api/user/user123  |
| PATCH  |   For updating only certain data elements  | PUT /api/user/user123 <br> {firstName: "Bob"}


#### Methods exaplained 

## The code 
Back in 2022, the [fetch()](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) method was introducted into NodeJS as a built-in method, overtaking 3rd party libraries such as Axios and SuperAgent as the most popular way to make HTTP requests. 

To make an HTTP request do the following
```ts
async function callApi(requestBody: any): Promise<any> {
    const response = await fetch("URL", {
        method: "GET|POST|PUT|DELETE|PATCH|etc.",
        headers: {},
        body: JSON.stringify(requestBody)
    });
    if (!response.ok) {
        throw new Error(`HTTP error! status: ${response.status}`);
    } else{
        const responseData: any = await response.json();
        return responseData;
    }
}
```