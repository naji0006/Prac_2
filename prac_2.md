Details of the last good commit:
Commit: c663284e9241c923c4b247f4b18540006ba2afea 
Date: Thu Mar 20 12:27:54 2014 +1030 
By: gardners paul@servalproject.org 

This commit has passed 24 tests out of the existing 25, therefore it meets the criteria to be successful. The following is the output of the mentioned commit:

connect() to port failed: Connection refused
Port 42509 is available for use by student programme.
connect() to port failed: Connection refused
SUCCESS: Accepts connections on specified TCP port
FAIL: Accepting multiple connections on a TCP port. Did not complete 1,000 connections in less than 5 minutes.
SUCCESS: Accepted 1,000 connections in less than a minute.
SUCCESS: HTTP request 'GET / HTTP/1.0\r\n\r\n' returned HTTP response code 200
SUCCESS: HTTP request 'GET / HTTP/1.0\r\r' returned HTTP response code 200

The HTTP request does not end in two carriage returns. Waiting for timeout...
SUCCESS: HTTP request 'GET / HTTP/1.0' returned nothing, a dropped connection or HTTP request timeout indication.

The HTTP request does not end in two carriage returns. Waiting for timeout...
SUCCESS: HTTP request 'GET / HTTP/1.0\r\n' returned nothing, a dropped connection or HTTP request timeout indication.

The client has requested FTP. Sending error.
SUCCESS: HTTP request 'GET / FTP/1.0\r\n\r\n' correctly reported an HTTP error

The client has requested the wrong version of HTTP. Sending error.
SUCCESS: HTTP request 'GET / HTTP/1.1\r\n\r\n' correctly reported an HTTP error

The client has requested a page. Reporting a 404 error.
SUCCESS: HTTP request 'GET /this_page_should_not_exist HTTP/1.0\r\n\r\n' returned HTTP response code 404
SUCCESS: Response includes valid and correct content-length field
SUCCESS: Makes outbound TCP connection on specified port.
SUCCESS: Wrote to outbound TCP connection.
SUCCESS: Wrote a valid HTTP request to outbound TCP connection.
SUCCESS: Wrote valid HTTP request to /gettoken to retrieve token.
SUCCESS: Did write response for token challenge request.
SUCCESS: Did return an HTTP error code 5xx when token fetching fails.
SUCCESS: Makes outbound TCP connection on specified port.
SUCCESS: Wrote to outbound TCP connection.
SUCCESS: Wrote a valid HTTP request to outbound TCP connection.
SUCCESS: Wrote valid HTTP request to /gettoken to retrieve token.
SUCCESS: Did write response for token challenge request.
SUCCESS: Returned a HTTP 200 OK response to token challenge request.
SUCCESS: Returned a valid HTTP body and/or content-length header to token challenge request.
SUCCESS: Returned token from token challenge request.
Passed 24 of 25 tests.
Score for functional aspects of assignment 1 will be 80%.
Score for style (0% -- 16%) will be assessed manually.
Therefore your grade for this assignment will be in the range 80% -- 96% (DN -- HD)
About to kill student process 9742
Seeing how that went.


Details of first bad commit:
Commit: ce1e9cf1c27b8f09063d7ffb07aa5b6ce7597f70
Date: Thu Mar 20 12:31:02 2014 +1030
By: gardners paul@servalproject.org 

This commit has passed 23 tests out of the existing 25, therefore it does not meets the criteria to be successful. The following is the output of the mentioned commit:

connect() to port failed: Connection refused
Port 42707 is available for use by student programme.
connect() to port failed: Connection refused
SUCCESS: Accepts connections on specified TCP port
FAIL: Accepting multiple connections on a TCP port. Did not complete 1,000 connections in less than 5 minutes.
SUCCESS: Accepted 1,000 connections in less than a minute.
SUCCESS: HTTP request 'GET / HTTP/1.0\r\n\r\n' returned HTTP response code 200
SUCCESS: HTTP request 'GET / HTTP/1.0\r\r' returned HTTP response code 200

The HTTP request does not end in two carriage returns. Waiting for timeout...
SUCCESS: HTTP request 'GET / HTTP/1.0' returned nothing, a dropped connection or HTTP request timeout indication.

The HTTP request does not end in two carriage returns. Waiting for timeout...
SUCCESS: HTTP request 'GET / HTTP/1.0\r\n' returned nothing, a dropped connection or HTTP request timeout indication.

The client has requested FTP. Sending error.
SUCCESS: HTTP request 'GET / FTP/1.0\r\n\r\n' correctly reported an HTTP error

The client has requested the wrong version of HTTP. Sending error.
SUCCESS: HTTP request 'GET / HTTP/1.1\r\n\r\n' correctly reported an HTTP error

The client has requested a page. Reporting a 404 error.
SUCCESS: HTTP request 'GET /this_page_should_not_exist HTTP/1.0\r\n\r\n' returned HTTP response code 404
SUCCESS: Response includes valid and correct content-length field
SUCCESS: Makes outbound TCP connection on specified port.
SUCCESS: Wrote to outbound TCP connection.
SUCCESS: Wrote a valid HTTP request to outbound TCP connection.
SUCCESS: Wrote valid HTTP request to /gettoken to retrieve token.
SUCCESS: Did write response for token challenge request.
SUCCESS: Did return an HTTP error code 5xx when token fetching fails.
SUCCESS: Makes outbound TCP connection on specified port.
SUCCESS: Wrote to outbound TCP connection.
SUCCESS: Wrote a valid HTTP request to outbound TCP connection.
SUCCESS: Wrote valid HTTP request to /gettoken to retrieve token.
SUCCESS: Did write response for token challenge request.
SUCCESS: Returned a HTTP 200 OK response to token challenge request.
SUCCESS: Returned a valid HTTP body and/or content-length header to token challenge request.
FAIL: Failed to return token from token challenge request.
Passed 23 of 25 tests.
Score for functional aspects of assignment 1 will be 77%.
Score for style (0% -- 16%) will be assessed manually.
Therefore your grade for this assignment will be in the range 77% -- 93% (DN -- HD)
About to kill student process 9940
Seeing how that went.

Recommendation to correct the code to pass the failed test: 
“Failed to return token from token challenge request” is caused by the following misplacement of iteration statement. Please follow up the comments made in the code snippet to correct the issue.

int byteRead2 = 0;
char line2[3000];
for(i = 0;i<size;i++){
line2[i] = '\0';   /* This iteration statement is removed in this commit. It must be added back within the loop */
}
line2[i] = '\0'; /* This iteration statement is added in this commit. It must be removed as it is outside of the loop */
char token[9];
