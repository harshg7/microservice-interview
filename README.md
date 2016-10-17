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
Your task is to implement the first two apis of the service (`alpha` and `flatten`).  This should be implemented using Maven and either Java or Node.js and must include tests to prove that your service is working correctly.  

_NOTE: Attention should be paid to both happy path and error conditions_

_BONUS: implement the `\status` endpoint_

## Site Reliability Engineer
Your task is to write a script which queries the `\status` endpoint and checks for the following conditions:

1. Memory Usage is >95.0%
2. Disc Space Available on either disc < 1k
3. CPU usage is >97.0%

if any of the above conditions are true, the script is to generate an alert in a fictitious alert service.  To generate an alert, one must make an `HTTP POST` to the `/createIncident` endpoint on the alert service.  The service uses HTTP Basic Authentication and otherwise follows the spec for the [PagerDuty Events Trigger API](https://v1.developer.pagerduty.com/documentation/integration/events/trigger).  You can use the following values:

* username `monitoring`
* password `f0rth3w1n`
* service_key `abcdefg`  

_NOTE: Make sure you specify the details of the alert in the `details` section of the payload_

_BONUS: Specify the cron expression you would use to enable this query to run every 5 minutes_

## Test Engineering
Your task is twofold

* Develop a smoke test plan for this service.  The tests should include functional verification as well as error cases.  Your smoke test should be documented in a github README or wiki page.  
_BONUS: Implement the test plan using a BDD language such as [Gherkin](https://cucumber.io/docs/reference) _

* Implement at least one of the tests you defined in the smoke test plan.  These test(s) should be implemented using Maven and Java
_BONUS: Test your tests using a mock of the real service_
