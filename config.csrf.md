#Cross-Site Request Forgery Protection

 When enabled, all non-GET requests to the Sails server must be accompanied by a special token, identified as the '_csrf' parameter.

This option protects your Sails app against cross-site request forgery (or CSRF) attacks. A would-be attacker needs not only a user's session cookie, but also this timestamped, secret CSRF token, which is refreshed/granted when the user visits a URL on your app's domain.

This allows you to have certainty that your users' requests haven't been hijacked, and that the requests they're making are intentional and legitimate.
  
This token has a short-lived expiration timeline, and must be acquired by either:

###*For traditional view-driven web apps:*
Fetching it from one of your views, where it may be accessed as a local variable, i.e.: `<%= _csrf %>`
e.g.:
```html
<form>
 <input type='hidden' name='_csrf' value='<%= _csrf %>'>
</form>
```
####*or*

###*For AJAX/Socket-heavy and/or single-page apps:*
Sending a GET request to the `/csrfToken` route, where it will be returned as JSON, e.g.: `{ _csrf: 'ajg4JD(JGdajhLJALHDa' }`




Enabling this option requires managing the token in your front-end app. For traditional web apps, it's as easy as passing the data from a view into a form action. In AJAX/Socket-heavy apps, just send a GET request to the /csrfToken route to get a valid token.

#####For more information on CSRF, check out: [this](http://en.wikipedia.org/wiki/Cross-site_request_forgery) article.
