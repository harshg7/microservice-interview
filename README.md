# CSV X1 Apps Engineering Coding Challenge
Hello and welcome to the coding challenge for the Comcast Silicon Valley X1 Apps team.  Please choose the appropriate question for the position you are applying for and proide the answer(s) within 24hrs. Please read and follow all instructions (both general and specific to your challenge).  All challenges relate to a fictitious microservice as defined below

# Product Definition
## overview
The json transformer service is a webservice which accepts a JSON payload (via an HTTP PUT or HTTP POST action) and performs an action on it based on the endpoint the payload is received on.  The JSON transformer service has three endpoints

| Endpoint        | Function           | HTTP Verb  |
| ------------- |-------------| -----|
| `\alpha`     | Alphabetize the keys in the request JSON payload and return the resulting JSON back in the HTTP response | `PUT` |
| `\flatten`      | Flatten any JSON Arrays in the request JSON payload (comma separated) such that the resulting JSON does not contain any JSON Arrays        |   `POST` |
| `\status`      | Obtains the health status of the system and responds with the details in the HTTP response | `GET` |

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

### \status
**input**
`HTTP GET \status`

**output**
```
{
  "mem-used-pct" : 83.6,
  "disc-space-avail" : [
                         { "discname" : "/dev/SDA1", "availbytes" : "12345000"},
                         { "discname" : "/dev/SDA2", "availbytes" : "12345000"}
                       ]
  "cpu-used-pct" : 55.0
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
Your task is to write a script which queries the `\status` endpoint and checks for the following conditions
1. Memory Usage is >95.0%
2. Disc Space Available on either disc < 1k
3. CPU usage is >97.0%

if any of the above conditions are true, the script is to make a call to a fictitious alerting tool which uses HTTP Basic Authentication (use the user name `monitoring` and the password `f0rth3w1n`) and expects a payload as follows:
```
TBD
```
TBD
## Test Engineering
TBD


