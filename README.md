# Fix-Mixed-Content-SSL-Error-on-Linux-Web-Hosting
How To Fix Mixed Content SSL Error on Linux Web Hosting

How To Fix Mixed Content SSL Error on Linux Web Hosting.
This article describes an issue that occurs when visitors to your web site request a secure web page that contains insecure elements.

When visitors to your web site request a page using a secure https:// connection, a broken padlock icon may appear in the web browser’s location bar. Additionally, they may receive a warning message in their browser like

Mozilla Firefox displays: “The connection to this website is not fully secure because it contains unencrypted elements (such as images).”
Microsoft Internet Explorer displays: “Do you want to view only the webpage content that was delivered securely? This webpage contains content that will not be delivered using a secure HTTPS connection, which could compromise the security of the entire webpage.”
Google Chrome displays: “Your connection to example.com is encrypted with 256-bit encryption. However, this page includes other resources which are not secure. These resources can be viewed by others while in transit, and can be modified by an attacker to change the look of the page.”
This problem occurs because a web page contains hyperlinks to insecure elements. For example, consider a web page that contains the following HTML snippet:

```html
<a href="http://www.example.com/images/picture.jpg">View my picture</a>
```

In the above HTML snippet, the hyperlink is a non-secure http:// resource (a .jpg file). The page itself is encrypted, but the hyperlinked image file is not. As a result, the page contains secure and insecure content, and the browser displays a warning message to the user.

This problem can occur with any type of hyperlinked resource file: a JavaScript library, a CSS file, etc.

Solution
Add the following lines to the .htaccess file (or files) that you use on your website:

```html
<IfModule mod_headers.c>
    Header always set Content-Security-Policy "upgrade-insecure-requests;"
</IfModule>
```
And You Are DONE
