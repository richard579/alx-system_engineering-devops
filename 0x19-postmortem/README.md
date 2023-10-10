## Issue Summary:

- Duration of Outage: Start time: 10/10/23 10:00 AM (SAST) and End time: 10/10/23 12:05 PM (SAST).
- An outage occurred on an isolated Ubuntu 14.04 container running an Apache web server. GET requests on the server led to 500 Internal Server Error's, when the expected response was an HTML file defining a simple Holberton WordPress site.
- Users affected: 25%

## Timeline:

+ 10:00 AM(SAST) — The outage occured and was detected by a few users.
+ 10:11 AM(SAST) — Checked running processes using ps aux. Two apache2 processes - root and www-data - were properly running.
+ 10:26 AM(SAST) — Looked in the sites-available folder of the /etc/apache2/ directory. Determined that the web server was serving content located in /var/www/html/.
+ 10:45 AM(SAST) — In one terminal, ran strace on the PID of the root Apache process. In another, curled the server. Strace gave no useful information.
+ 11:00 AM(SAST) — Repeatedthe step before, except on the PID of the www-data process. Strace revealed an -1 ENOENT (No such file or directory) error occurring upon an attempt to access the file /var/www/html/wp-includes/class-wp-locale.phpp.
+ 11:15 AM(SAST) — Looked through files in the /var/www/html/ directory one-by-one, using Vim pattern matching to try and locate the erroneous .phpp file extension. Located it in the wp-settings.php file. (Line 137, require_once( ABSPATH . WPINC . '/class-wp-locale.php' );).
+ 11:29 AM(SAST) — Removed the trailing p from the line.
+ 11:45 AM(SAST) — Tested another curl on the server.
+ 12:05 PM(SAST) — Wrote a Puppet manifest to automate fixing of the error.

## Root cause and Resolution:

- A typo. They are very Annoying! The WordPress app was encountering a critical error in wp-settings.php when trying to load the file class-wp-locale.phpp. The correct file name, located in the wp-content directory of the application folder, was class-wp-locale.php.
- Patch involved a simple fix on the typo, removing the trailing p.

## Corrective and Preventative measures:

- Test the application before deploying. This error would have arisen and could have been addressed earlier had the app been tested. Enable some uptime-monitoring service such as UptimeRobot to alert instantly upon outage of the website.

A Puppet manifest 0-strace_is_your_friend.pp was written to automate fixing of any such identitical errors should they occur in the future. The manifest replaces any phpp extensions in the file /var/www/html/wp-settings.php with php.

But we're Programmers, we never make errors! :)
