Mutt email client commands for IMAP connection, sending email from command line, and deleting messages by date range.

Connect to a remote server
    mutt -f imaps://mail.yourdomain.com/

Send an email from the command line
    echo "message" | mutt -s "subject" you@example.com

Delete messages by date range:
    In Mutt, SHIFT-D for pattern delete
    Type the pattern: ~d 01/01/2016-31/12/2016 and press Enter
