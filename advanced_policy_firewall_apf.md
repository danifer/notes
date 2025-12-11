APF (Advanced Policy Firewall) commands to allow, deny, and remove IP addresses from firewall rules.

---

Per: https://sysadminspot.com/server-administration/allow-deny-and-remove-with-apf/

Using the apf command via SSH has to be my preferred method of adjusting the firewall. To deny a source you can simply type:

apf -d <source> [comment]
apf -d 123.45.67.89 Keepings dosing the server

If you have a default deny policy and only want to allow on an individual basis then you can use a command like this:

apf -a <source> [comment]
apf -a 123.45.67.89 Melbourne office allow complete access

Another handy parameter I didn.t learn about until later (much regretted) is the -u one. It will remove the IP source from either allow or denied if it exists. Saves you modifying the rule files directly and restarting the firewall. So to remove a source use:

apf -u <source>
apf -u 123.45.67.89
