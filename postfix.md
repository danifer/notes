Postfix mail server configuration commands for viewing options, version info, and parsing incoming mail with PHP scripts.

---

Display all postfix configuration options:
    postconf -d

Display postfix version info:
    postconf -d | grep mail_version

Parse incoming mail through a PHP script:
    https://thecodingmachine.io/triggering-a-php-script-when-your-postfix-server-receives-a-mail
