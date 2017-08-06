## links
#### &lt;a&gt;
Links are created using the `<a>` element which has an attribute called `href`. The value of the href attribute is the page that you want people to go to when they click on the link.   
Users can click on **anything** that appears between the opening `<a>` tag and the closing `</a>` tag and will be taken to the page specified in the href attribute.   

---
#### mailto:
To create a link that starts up the user's email program and addresses an email to a specified
email address, you use the `<a>` element. However, this time the value of the href attribute starts with `mailto:` and is followed by the email address you want the email to be sent to.   
`<a href="mailto:jon@example.org">Email Jon</a>` : <a href="mailto:jon@example.org">Email Jon</a>

---
#### target
If you want a link to open in a new window, you can use the `target` attribute on the opening
`<a>` tag. The value of this attribute should be `_blank`.   
`<a href="http://www.imdb.com" target="_blank"> Internet Movie Database</a> (opens in new window)` : <a href="http://www.imdb.com" target="_blank">Internet Movie Database</a> (opens in new window)   

---
#### linking to specific part of the page
You can using the `id` attribute to linking to specific part.   
e.g.   
the same page: `<a href="#top">`   
another page: `<a href="http:/www.htmlandcssbookcom/#bottom">`