# AWS-CORS-Cross-Origin-Resource-Sharing-
Concept:
S3 bucket1\index.html contains Javascript which will load file load.html
at the bucket2\load.html.
Normally, it is blocked by web browser.
-> Use CORS to enable it

Example:
Bucket (domain) 1: jolenengo.com
Bucket (domain) 2: ericngo.com

On domain 1:
  upload: helloworldJS.html
  This file contains the below Javascript pointing to the second domain: ericngo.com
  <script type="text/javascript">
  $("#loadDiv").load("http://ericngo.com/load.html");
On domain 2:
    upload: load.html

By default, the above JS code can not load the contain from "http://ericngo.com/load.html" because Javascript is blocked by browser.
=> to enable it, use CORS on the second bucket

CORS Configuration template:
Go to The Second S3 bucket2 -> Permission -> CORS Configuration:

<CORSConfiguration>
	<CORSRule>
		<AllowedOrigin>*</AllowedOrigin>
		<AllowedMethod>GET</AllowedMethod>
		<AllowedMethod>PUT</AllowedMethod>
		<AllowedMethod>POST</AllowedMethod>
		<AllowedMethod>DELETE</AllowedMethod>
		<AllowedHeader>*</AllowedHeader>
		<MaxAgeSeconds>3000</MaxAgeSeconds>
	</CORSRule>
</CORSConfiguration>
