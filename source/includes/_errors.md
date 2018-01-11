# Errors

<aside class="notice">This error codes are used across the API responses</aside>

The Keyco/kitchen API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request sucks.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- The request is hidden for administrators only.
404 | Not Found -- The specified kitten could not be found.
405 | Method Not Allowed -- You tried to access a kitten with an invalid method.
406 | Not Acceptable -- You requested a format that isn't json.
410 | Gone -- The request has been removed from our servers.
418 | I'm a teapot.
429 | Too Many Requests -- You're requesting too many! Slow down!
500 | Internal Server Error -- .
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
