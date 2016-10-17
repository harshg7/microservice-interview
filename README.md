# CSV X1 Apps Engineering Coding Challenge
Hello and welcome to the coding challenge for the Comcast Silicon Valley X1 Apps team.  Please choose the appropriate question for the position you are applying for and proide the answer(s) within 24hrs. Please read and follow all instructions (both general and specific to your challenge).  All challenges relate to a fictitious microservice as defined below

# Product Definition
## overview
The json transformer service is a webservice which accepts a JSON payload (via an HTTP PUT or HTTP POST action) and performs an action on it based on the endpoint the payload is received on.  The JSON transformer service has three endpoints

| Endpoint        | Function           | HTTP Verb  |
| ------------- |:-------------:| -----:|
| `\alpha`     | Alphabetize the keys in the request JSON payload and return the resulting JSON back in the HTTP response | `PUT` |
| `\flatten`      | Flatten any JSON Arrays in the request JSON payload (comma separated) such that the resulting JSON does not contain any JSON Arrays        |   `POST` |

## examples
### \alpha
**input**
`HTTP PUT \alpha`
```
{
  "fruit":"apple",
  "animal":"zebra",
  "city-list":["sunnyvale","sanjose"]
}
```
**output**
```
{
  "animal":"zebra",
  "city-list":["sunnyvale","sanjose"],
  "fruit":"apple"
}
```

### \flatten
**input**
`HTTP PUT \alpha`
```
{
  "fruit":"apple",
  "animal":"zebra",
  "city-list":["sunnyvale","sanjose"]
}
```
**output**
```
{
  "fruit":"apple",
  "animal":"zebra",
  "city-list":"sunnyvale,sanjose"
}
```

# General Instructions
1. Your solution must be implemented as a repo in your personal org (or using a throw away account).  Solutions submitted as jar/zip/etc files via email will not be accepted
2. Your solution must be executeable by someone who clones your repo.  This means that you will likely need to provide instructions on how to execute your code
3. In cases where not enough information is given, make reasonable assumptions and document your assumptions
4. Your solution should involve unit tests to validate that your code is working as designed

# Challenges
## Developer
TBD
## Site Reliability Engineer
TBD
## Test Engineering
TBD


