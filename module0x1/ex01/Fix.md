Token-Based Mitigation¶ that's what we will use to fix that breach.

The synchronizer token pattern is one of the most popular and recommended methods to mitigate CSRF.

IMPORTANT: Remember that Cross-Site Scripting (XSS) can defeat all CSRF mitigation techniques! While Cross-Site Scripting (XSS) vulnerabilities can bypass CSRF protections, CSRF tokens are still essential for web applications that rely on cookies for authentication. Consider the client and authentication method to determine the best approach for CSRF protection in your application.

### We will first modify the server.js and make a middleware to create a unique and random token with csurf

const cookieParser = require('cookie-parser');
const csurf = require('csurf');
const fs = require('fs');

app.use(cookieParser());

### CSRF protection middleware using cookies
const csrfMiddleware = csurf({ cookie: true, value: req => req.body.tokenCSRF});

### Serve index.html with CSRF token
``` app.get('/', csrfMiddleware, (req, res) => {
    let html = fs.readFileSync(path.join(__dirname, 'index.html'), 'utf8');
    html = html.replace('{{CSRF_TOKEN}}', req.csrfToken());
    res.send(html);
});

app.post('/transfer', csrfMiddleware, (req, res) => {
    ...
} 
```
### After we will add this to our index.html

 <input type="hidden" name="tokenCSRF" value="{{CSRF_TOKEN}}">
