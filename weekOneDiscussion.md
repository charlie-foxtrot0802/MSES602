# Week 1 Discussion

Read the above discussion between me and Aaron.

**What happens if you try to find the domain that is associated with the IP address that is listed in the DNS configuration for programmingkitchen.com?**

        bcutcliff@ubuntu:/$ dig programmingkitchen.com

        ; <<>> DiG 9.16.1-Ubuntu <<>> programmingkitchen.com
        ;; global options: +cmd
        ;; Got answer:
        ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 2329
        ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

        ;; OPT PSEUDOSECTION:
        ; EDNS: version: 0, flags:; udp: 65494
        ;; QUESTION SECTION:
        ;programmingkitchen.com.                IN      A

        ;; ANSWER SECTION:
        programmingkitchen.com. 313     IN      A       172.200.38.66

        ;; Query time: 0 msec
        ;; SERVER: 127.0.0.53#53(127.0.0.53)
        ;; WHEN: Sun Jan 21 21:25:53 UTC 2024
        ;; MSG SIZE  rcvd: 67

        bcutcliff@ubuntu:/$ dig -x 172.200.38.66

        ; <<>> DiG 9.16.1-Ubuntu <<>> -x 172.200.38.66
        ;; global options: +cmd
        ;; Got answer:
        ;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 37779
        ;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

        ;; OPT PSEUDOSECTION:
        ; EDNS: version: 0, flags:; udp: 65494
        ;; QUESTION SECTION:
        ;66.38.200.172.in-addr.arpa.    IN      PTR

        ;; Query time: 127 msec
        ;; SERVER: 127.0.0.53#53(127.0.0.53)
        ;; WHEN: Sun Jan 21 21:26:02 UTC 2024
        ;; MSG SIZE  rcvd: 55

It appears that I got no "answer" to my query when I do a reverse-DNS lookup using the IP address from the DNS record query performed first.  it appears that it is also a NXDOMAIN (non-existent).


**What could be done to change this behavior to be more helpful for someone trying to find the domain associated with a particular IP address?**

I think that something that could be done is being able to get more information out of a CNAME reverse lookup query, or make the query more human readable to give better context.

**What is the DNS server that you are using on your local PC or environment where you are doing the lab?**

To find this I opened my windows command prompt and typed: ipconfig/all, which returned a list of all my network configurations.

This provided me with my primary DNS, which is 75.75.75.75 and my secondary is 75.75.76.76.  When I did a reverse lookup using dig on my VM I get the following:

        bcutcliff@ubuntu:/$ dig -x 75.75.75.75

        ; <<>> DiG 9.16.1-Ubuntu <<>> -x 75.75.75.75
        ;; global options: +cmd
        ;; Got answer:
        ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64176
        ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

        ;; OPT PSEUDOSECTION:
        ; EDNS: version: 0, flags:; udp: 65494
        ;; QUESTION SECTION:
        ;75.75.75.75.in-addr.arpa.      IN      PTR

        ;; ANSWER SECTION:
        75.75.75.75.in-addr.arpa. 793   IN      PTR     cdns01.comcast.net.

        ;; Query time: 11 msec
        ;; SERVER: 127.0.0.53#53(127.0.0.53)
        ;; WHEN: Sun Jan 21 21:34:51 UTC 2024
        ;; MSG SIZE  rcvd: 85




Post screen shots or example output from your dig commands