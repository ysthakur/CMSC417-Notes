- Passed as HTTP headers
	- Server sends `Set-Cookie: name=value`
	- Browser sends `Cookie: name=value`

Uses:
- Authorization
- Shopping carts
- Recommendations
- User session state (web email)

How to keep state:
- Protocol endpoints: Maintain state at sender/receiver over multiple transactions
- Cookies: HTTP messages carry state

![Cookie diagram](HTTP/cookies.png)

> [!warning]
> Cookies allow sites to learn stuff like your name and email
