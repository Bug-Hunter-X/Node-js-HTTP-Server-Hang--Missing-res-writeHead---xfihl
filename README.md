# Node.js HTTP Server Hang: Missing `res.writeHead()`

This repository demonstrates a subtle bug in a Node.js HTTP server where omitting the `res.writeHead()` method call before `res.end()` can cause the server to hang.  The issue is not immediately apparent and highlights the importance of following the proper sequence of HTTP response handling.

## Bug Description

The `bug.js` file contains a minimal HTTP server.  If you run this server and make a request, the connection will hang indefinitely.  The solution is simple – adding the missing `res.writeHead()` call.  This demonstrates how crucial it is to send the HTTP headers before sending the response body.

## How to Reproduce

1. Clone this repository.
2. Navigate to the directory.
3. Run `node bug.js`.
4. Make a request to `http://localhost:3000` using a tool like `curl` or your browser.
5. Observe that the request hangs.
6. Uncomment the `res.writeHead(200);` line in `bug.js` and run again. The issue is resolved.

## Bug Solution

The `bugSolution.js` file contains the corrected server code.  The addition of `res.writeHead(200);` ensures that the server sends the proper HTTP headers before sending the response body, preventing the hang.