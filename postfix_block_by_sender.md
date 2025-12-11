Block email senders in Postfix using sender_access file and postmap to rebuild the database.

03/08/18
I added a script in /usr/lib/update_sender_access for this task.

08/16/12

Used: http://www.cyberciti.biz/faq/howto-blacklist-reject-sender-email-address/
and: http://archives.neohapsis.com/archives/postfix/2002-09/1719.html
and: http://www.postfix.org/postconf.5.html#check_sender_access

As root:
- Add the email to /etc/postfix/sender_access
- Rebuild the database with # postmap hash:sender_access

