
In order to target APIs, you must first be able to find them.
### Api's
Partner APIs:-They are intended to be used exclusively by partners of the provider.
Private APIs:-They are intended for use, privately, within an organization. These APIs are often documented less than partner APIS, if at all, and if any documentation exists it is even harder to find. 
## Web API Indicators
 When searching for APIs there are several signs that will indicate that you have discovered the existence of a web API. Be on the lookout for obvious URL naming schemes:
https://target-name.com/api/v1 
https://api.target-name.com/v1 
https://target-name.com/docs
https://dev.target-name.com/rest

Look for API indicators within directory names like:
/api, /api/v1, /v1, /v2, /v3, /rest, /swagger, /swagger.json, /doc, /docs, /graphql, /graphiql, /altair, /playground

Also, subdomains can also be indicators of web APIs:
api.target-name.com
uat.target-name.com
dev.target-name.com
developer.target-name.com
test.target-name.com

Another indicator of web APIs is the HTTP request and response headers. The use of JSON or XML can be a good indicator that you have discovered an API.

HTTP Request and Response Headers containing "Content-Type: application/json, application/xml"

Also, watch for HTTP Responses that include statements like:
{"message": "Missing Authorization token"}

 

One of the most obvious indicators of an API would be through information gathered using third-Party Sources like Github and API directories.
Gitub: https://github.com/ 
Postman Explore: https://www.postman.com/explore/apis
ProgrammableWeb API Directory: https://www.programmableweb.com/apis/directory 
APIs Guru: https://apis.guru/ 
Public APIs Github Project: https://github.com/public-apis/public-apis 
RapidAPI Hub: https://rapidapi.com/search/ 

### Passive Reconnaissance
Gathering information without interacting with the target directly
As you are collecting OSINT, it is entirely possible you will stumble upon a critical data exposure, such as API keys, credentials, JSON Web Tokens (JWT), and other secrets that would lead to an instant win. Other high-risk findings would include leaked PII or sensitive user data such as SSN, full names, email addresses, and credit card information.
##### 1)Google Dorking

inurl:"/wp-json/wp/v2/users"->Finds all publicly available WordPress API user directories.

intitle:"index.of" intext:"api.txt"->Finds publicly available API key files.

inurl:"/api/v1" intext:"index of /"->Finds potentially interesting API directories.

ext:php inurl:"api.php?action="->
	Finds all sites with a XenAPI SQL injection vulnerability. (This query was posted in 2016; four years later, there are currently 141,000 results.)

intitle:"index of" api_key OR "api key" OR apiKey -pool -> It lists potentially exposed API keys.
2) Git dorking 
search for API keys, passwords, and tokens, which could prove useful during an attack.
“api key,” "api keys", "apikey", "authorization: Bearer", "access_token", "secret", or “token.” 
3)TruffleHog 
bash```
 $ sudo docker run -it -v "$PWD:/pwd" trufflesecurity/trufflehog:latest github --org=target-name
```
Note:change target-name
4)Shodan
You can use Shodan to discover external-facing APIs and get information about your target’s open ports, making it useful if you have only an IP address or organization’s name to work from
eX:-
hostname:"targetname.com"
"content-type: application/json"
"wp-json"
5)The wayback machine
It is an archive of various webpages
search like https://target-site.com/api-endpoints


### Active Reconnissance
Active reconnaissance is the process of interacting directly with the target primarily through the use of scanning
1)nmap(network mapper)
it is a tool to discover the open ports on the target website
bash```
$nmap -sC -sV targetip 
/
$nmap -sC -sV -p- [target] -oA allports
```
2)Amass 
 Amass is a command-line tool that can map a target’s external network by collecting OSINT from over 55 different sources. 
bash```
$ amass enum -active -d target-name.com |grep api
```
3)gobuster
Gobuster can be used to brute-force URIs and DNS subdomains from the command
bash```
$ gobuster dir -u target-name.com:8000 -w /home/hapihacker/api/wordlists/common_apis_160
```
4)KiteRunner
Kiterunner is currently the best tool available for discovering API endpoints and resources. Gobuster/dirbuster scans url by get method but kiterunner will try to use methods like get,post,put,delete etc..to discover it.
bash```
$ kr scan HTTP://127.0.0.1 -w ~/api/wordlists/data/kiterunner/routes-large.kite
```
bash```
$ kr kb replay "GET  414 [183,7,8]
http://192.168.50.35:8888/api/privatisations/count0cf6841b1e7ac8badc6e237ab300a90ca873d571" -w ~/api/wordlists/data/kiterunner/routes-large.kite```
5)dev tools
By above all you have to get api endpoints. We can discover endpoints using devtools.
Begin by opening your target page, and then open DevTools with F12 or ctr-shift-I. Adjust the DevTools window until you have enough space to work with. Select the Network tab and then refresh the page (CTRL+r).Enable url in network tab if not present.
You can use the filter tool to search for any term you would like, such as "API", "v1", or "graphql". This is a quick way to find API endpoints in use. You can also leave the Devtools Network tab open while you perform actions on the web page.

we copy particular endpoint as curl which is used to seng req from postman/burp 