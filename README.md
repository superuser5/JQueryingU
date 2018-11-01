# JQueryingU

## NOTES:
Base client side detection code created by Christian Ludwig (https://jsfiddle.net/ChristianL/AVyND/), and used by APT 29 in 2016. APT 29 modified the popup to be a POST request and used it during a conference shadowing campaign to profile user systems and who clicked before sending malicious payloads.

Code has been modified to send information via Base64 encoded fake analytics GET request rather than a clear text POST used by APT 29.  Support for Flash detection has been added via https://ajax.googleapis.com/ajax/libs/swfobject/2.2/swfobject.js inside the script. The document window was added to the script log so that you can feed each target a unique URI via FiercePhish or manually and then correspond the system to the user.

The whole script was minified and then packed before being appended to legitimate jquery: https://code.jquery.com/jquery-2.2.4.min.js so you can use the script for dual purposes and it might pass the sniff test of tier 1 SOC.

### Example Log output:
``` [Mon Apr 16 11:51:17 2018] ::1:63582 [200]: /analytics.gif?uid=aHR0cDovL2xvY2FsaG9zdDo4MDAwL2luZGV4LnBocD9pZD1zYW18T1M6IE1hYyBPUyBYIDEwLjEzfEJyb3dzZXI6IEZpcmVmb3ggNjAgKDYwLjApfE1vYmlsZTogZmFsc2V8Rmxhc2g6IDI5LjAgcjB8SmF2YTogZmFsc2V8Q29va2llczogdHJ1ZXxTY3JlZW4gU2l6ZTogMTY4MCB4IDEwNTB8TGFuZ3VhZ2U6IGVuLVVTfEZ1bGwgVXNlciBBZ2VudDogTW96aWxsYS81LjAgKE1hY2ludG9zaDsgSW50ZWwgTWFjIE9TIFggMTAuMTM7IHJ2OjYwLjApIEdlY2tvLzIwMTAwMTAxIEZpcmVmb3gvNjAuMA== ```

#### Example Log output base 64 decoded:

``` http://localhost:8000/index.php?id=sam|OS: Mac OS X 10.13|Browser: Firefox 60 (60.0)|Mobile: false|Flash: 29.0 r0|Java: false|Cookies: true|Screen Size: 1680 x 1050|Language: en-US|Full User Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.13; rv:60.0) Gecko/20100101 Firefox/60.0 ```


Future ideas:  Hypervisor script which alerts on suspicious user agents (fake crawlers, wget, curl, virustotal cloud, etc).
