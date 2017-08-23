# Web Checklist

- Does it work on mobile?
- Google Analytics
- Social Sharing / Open Graph
  - specific values for important/interesting pages
- Submitted to Google/Bing/Yandex (for duckduckgo)?
  - sitemap
- HTTPS by default
- Do colours/contrasts look ok on cheap old devices?
  - Looking good on a top-end mac or iphone isn't a sufficient test.
- Does www. work?
  - Even if it redirects to non-www, it needs to work because people will add it even when you ask them not to!
- global javascript error logging
  - e.g. `window.addEventListener('error', trackJavaScriptError, false);`
- AJAX error handlers
  - This is so important
  - This can be as simple as adding `.fail(function( jqXHR, textStatus, errorThrown ) { throw textStatus })` to your jQuery ajax request.