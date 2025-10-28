#Few way to fix that breach.

1. We can encode the cookie.
So even if we have access to it we will be not able to use it or read it.

2. Simply not using HTML in our JS with calling innerHTML for example so if we want to write some stuff just use text.Content or innerText. Because InnerHTML it's an javascript propriety that allows to read or modify a content of HTML element in a web page.

For example:
Replace that, 
```
document.getElementById("output").innerHTML = "<b>" + userInput + "</b>";
```
by that
```
document.getElementById("message").textContent = userInput;
```

We should not create a variable named script because it's an easy way for an attacker to exploit us and it opens many doors.By executing user input directly as JavaScript code, a user can send us anything they want.

We sometimes create DOM elements using user input without checking that input. Therefore we must always secure user input. Even if we want to use var script = ... in our index.html, we must parse and validate it to make sure it is valid and safe — which is not an easy task.

Like sandboxed the userInput and send it with iframe for example. But we highly recommend to not executing user JS in your page.

So what we recommend here is not to interpret HTML from untrusted sources and, above all, never create a <script> using user content without at least checkit, because we would directly execute attacker code.

It seems logical — sometimes it’s the simplest things that we forget.
An attacker doesn’t need to look for a backdoor or the most complicated way to steal data; sometimes you only need to push the door.
