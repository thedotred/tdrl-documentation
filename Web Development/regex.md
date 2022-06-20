# 🌐 URL Validation

Regex if you want to ensure URL starts with HTTP/HTTPS:
```javascript 
https?:\/\/(www\.)?[-a-zA-Z0-9@:%._\+~#=]{1,256}\.[a-zA-Z0-9()]{1,6}\b([-a-zA-Z0-9()@:%_\+.~#?&//=]*)
```

If you do not require HTTP protocol:
```javascript
[-a-zA-Z0-9@:%._\+~#=]{1,256}\.[a-zA-Z0-9()]{1,6}\b([-a-zA-Z0-9()@:%_\+.~#?&//=]*)
```

Example JavaScript implementation:
```javascript
var expression = /[-a-zA-Z0-9@:%._\+~#=]{1,256}\.[a-zA-Z0-9()]{1,6}\b([-a-zA-Z0-9()@:%_\+.~#?&//=]*)?/gi;
var regex = new RegExp(expression);
var t = 'www.google.com';

if (t.match(regex)) {
  alert("Successful match");
} else {
  alert("No match");
}
```

[Credit: Daveo @Stackoverflow](https://stackoverflow.com/questions/3809401/what-is-a-good-regular-expression-to-match-a-url)

# 📧 Email Validation

Example JavaScript implementation:
```javascript
var expression = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;
var regex = new RegExp(expression);
var t = 'naz@google.com';

if (t.match(regex)) {
  alert("Successful match");
} else {
  alert("No match");
}
```