Whitelist email senders and domains to bypass spam checking in Amavis mail filter.

03/08/18
I added a script in /usr/lib/update_sender_access for this task. If the incoming address is in the sender_access list specifically, it should bypass spam checking.


#Bypass spam checking (amavis) by sender or domain
    Add domain or sender address to
        /etc/amavis/whitelist
            test@example.com
            example.com
    Restart amavis
        /etc/init.d/amavis restart
    Sender/domain will bypass spam check and receive WHITELISTED header tag
