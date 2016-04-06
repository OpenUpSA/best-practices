 - Test embedded from the start
  - Even if you're sure it'll be fine - you'll be surprised. 
 - Test on mobile from the start
  - Reworking something for mobile when you didn't consider it from the start is often double work.
 - Test over HTTPS from the start
  - HTTPS sites can't include HTTP dependencies. Most sites now server over HTTPS which means things won't work and you might not be able to fix everything to be over HTTPS after all your hard work. Deal with this from the start.
 - Fixed width is bad.
  - Anything wider than 300px will badly affect mobile sites on small devices.
  - If you need to compromise and use fixed width - rather make it work on mobile (300px wide) and weirdly narrow but usable on large devices.
 - Put a space in empty tags e.g. `<iframe ...> </iframe` or `<script src="..."> </script`
  - Some CMSs rewrite empty tags e.g. as `<iframe ... />` which browsers don't accept properly. Putting a space in there is usually sufficient to stop the CMS from breaking things.
 
## Testing

### TMG

This only tests the size/shape. It doesn't test Escenic's rewriting of the code.

Insert your embed code in the part of the HTML box in [a fork of a timeslive jsfiddle](http://jsfiddle.net/hawyzhmz/4/#fork) that looks a bit like
```html
<!-- ########################################################### -->
<!-- ########################################################### -->
<!-- ########################################################### -->


<!-- insert your embed code below this line -->


<!-- ########################################################### -->
<!-- ########################################################### -->
<!-- ########################################################### -->
```
