Cisco ASDM setup for ASA5505 firewall including SSH tunnel, Java configuration, and SOCKS proxy settings.

---

Making the ASDM connect to ASA5505. This is a pain in the ass.

    -The ASA5505 is configured to allow internal connections only. This is by design for security. You'll need to create an ssh tunnel to an internal machine (like dfw2), and then you can connect to the ASA5505 from the internal LAN.

        Creating the SSH tunnel: https://www.getfilecloud.com/blog/create-your-own-virtual-private-network-for-ssh-with-putty/
            I saved mine as "dfw2 tunnel" in my putty "Saved Sessions" list (3/1/18)

        Setting up IE for a SOCKS proxy: http://support.moonpoint.com/network/proxy/ie10-socks-proxy.php

Some gotchas:

    -Cisco is a jerk about licensing. The version of ASDM you have (6.4) works with Java 1.6. You'll need Java 1.6 installed on your machine, and you'll need to tell the ASDM client to use it. It's going to complain about 1.8 and it's going to fail to connect with 1.7.

        https://supportforums.cisco.com/t5/firewalling/unable-to-start-asdm-version-1-5-50/td-p/1744664

            Found when I researched the Java console error: "Exception in thread "AWT-EventQueue-0" java.lang.ClassCastException: sun.security.ssl.X509TrustManagerImpl cannot be cast to com.sun.net.ssl.internal.ssl.X509ExtendedTrustManager"

        After you download Java 1.6, you'll need to specify it for ASDM. Do that by editing the shortcut used to open ASDM.  I'm connected right now, and mine looks like:

            "C:\Program Files (x86)\Java\jre6\bin\javaw.exe" -Xms64m -Xmx512m -Dsun.swing.enableImprovedDragGesture=true -classpath lzma.jar;jploader.jar;asdm-launcher.jar;retroweaver-rt-2.0.jar com.cisco.launcher.Launcher

                Note the jre6, aka Java 1.6

    -The ASDM client will use the proxy settings configured for Internet Explorer.  Click the Java icon on the ASDM launcher page to view the Java console and look for connection errors.

    -If you're looking for files, check your desktop "Danifer" entitled "asdm asa5505 resources". I saved a copy of Java 1.6 Runtime Environment, the ASDM launcher setup program, and some screenshots for the proxy/tunnel setup.

Configuring multiple external IP ranges
        https://community.spiceworks.com/topic/1602602-how-to-add-a-second-subnet-to-cisco-asa-firewall-using-asdm
