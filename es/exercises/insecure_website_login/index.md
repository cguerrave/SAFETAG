
####Insecure Website Login

##### Summary
## Website passwords are sent unencrypted

Administrative and user passwords on the site are submitted unencrypted.

##### Overview

* Determine website admin login link
* See if there is an SSL option to log in

##### Materials Needed 

##### Considerations

##### Walkthrough
Users and website editors log in to the site at http://www.sampleorg.org/user/login. There is no SSL security on this page, nor does there appear to be the option to use SSL.
Description

By default, all web traffic is unencrypted. For non-controversial website content, this is not a problem. However, as many websites have moved from uploading files on the backend to a front-end content management system, as well as becoming more complex with user accounts and interaction, this lack of security becomes problematic.

When an admin (or any user) logs in, their password is sent in the clear. This means anyone on the same network (at a coffee shop or workplace) as well as anyone in control of the network (coffee shop owner, workplace network admin, ISP, or government) can trivially intercept the password (often simply by searching the network traffic stream for “password”). This allows an adversary to have admin access to a website, post fake content, install malware, or attempt to discover other accounts where that same password may be used.

First, determine the login page, if there is not a “user login” link visible. Most CMS systems have a standard login path (for Drupal, it’s /user/login, for example). Then, attempt to access this page through an SSL connection.

##### Recommendation
HTTPS / SSL – this comes at a cost, both the SSL Certificate and often an upgrade to the hosting plan itself. However, without SSL, every password – including the one used for admin access to the website – goes across the Internet in the clear. This is immediately available to a state-level actor through the ISP, and can also be sniffed if accessed by a staff member on a shared wifi connection (at a coffeeshop or airport), and finally if the attacker has broken in to the office network (see the Local Access section). Enabling SSL (and making it the default for your site) also protects the users of your site.

If an organization updates their website via FTP, it is worth noting that FTP is similarly insecure. Many hosting providers provide SFTP or FTPS, (two different, but secure, FTP versions), or secure WebDAV to upload files. These should be used, turning “plain” FTP off altogether if possible.

When switching to SSL/Secure FTP after having used the plain versions, webmasters should also update all administrative passwords, and watch to make sure that no step along the way (hosting provider management/panel, file upload, CMS editing) goes over “clear” channels.
