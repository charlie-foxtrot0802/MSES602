## Week 1 Lab Assignment. 

## Part 2a: Installing a local virtual machine

Vagrant commands:

**This creates a vagrant file in directory I created.**

    vagrant init alvistack/ubuntu-20.04

**This downloaded and launched my VM using virtualbox.**

    vagrant up

**Image below is of my git-bash using vagrant to bring up my ubuntu in virtualBox**

![alt text](images/vagrant_gitBash.PNG)

**Checksum of .iso**

I was actually unable to figure out how to properly do this since I used Vagrant to install my Ubuntu 20.04 LTS VM on VirtualBox.  I did, however, find instructions on how to perform a checksum on the Ubuntu image here:

https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview

This basically has you download the SHA256SUMS(and .gpg) files that contain the hashes to confirm you have an uncorrupted download of Ubuntu.  I was unable to perform this manually, but I believe when I did a `vagrant init alvistack/ubuntu-20.04` a checksum was automatically performed but I do not have evidence of this.

## Part 2b: Linux Operations exploring DNS and Dig.

I had to use the username and login as vagrant then create a username and password for myself, and then add my user to the sudoers group.  After that I installed the update using:

    sudo apt-get update

![This is the picture of the completion of the update](images/ubuntuGetUpdate.PNG)

Once that was complete I had to install dig, which was done using the following command:

    sudo apt-get install dnsutils

![Image of dig command being installed](images/digInstalled.PNG)

Using the dig command to find the IP address of regis.edu: 

    bcutcliff@ubuntu:~$ dig regis.edu +short
    216.54.215.129

Using the dig command to find the IP address of programmingkitchen.com:

    bcutcliff@ubuntu:~$ dig programmingkitchen.com +short
    172.200.38.66

`dig programmingkitchen.com +short`


My FQDN (Fully Qualified Domain Name, didn't know that one!) was www.seriouseats.com, my favorite cooking site. Here is the command line:

    bcutcliff@ubuntu:~$ dig seriouseats.com +short
    151.101.130.137
    151.101.194.137
    151.101.2.137
    151.101.66.137
    bcutcliff@ubuntu:~$

**For regis.edu:**

The regis.edu A DNS record:

    bcutcliff@ubuntu:~$ dig regis.edu A

    ; <<>> DiG 9.16.1-Ubuntu <<>> regis.edu A
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 7373
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

    ;; OPT PSEUDOSECTION:
    ; EDNS: version: 0, flags:; udp: 65494
    ;; QUESTION SECTION:
    ;regis.edu.                     IN      A

    ;; ANSWER SECTION:
    regis.edu.              300     IN      A       216.54.215.129

    ;; Query time: 16 msec
    ;; SERVER: 127.0.0.53#53(127.0.0.53)
    ;; WHEN: Sat Jan 20 20:45:40 UTC 2024
    ;; MSG SIZE  rcvd: 54

The regis.edu MX DNS Record:

        bcutcliff@ubuntu:~$ dig regis.edu MX

        ; <<>> DiG 9.16.1-Ubuntu <<>> regis.edu MX
        ;; global options: +cmd
        ;; Got answer:
        ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 45984
        ;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

        ;; OPT PSEUDOSECTION:
        ; EDNS: version: 0, flags:; udp: 65494
        ;; QUESTION SECTION:
        ;regis.edu.                     IN      MX

        ;; ANSWER SECTION:
        regis.edu.              3600    IN      MX      10 d174024a.ess.barracudanetworks.com.
        regis.edu.              3600    IN      MX      20 d174024b.ess.barracudanetworks.com.

        ;; Query time: 24 msec
        ;; SERVER: 127.0.0.53#53(127.0.0.53)
        ;; WHEN: Sat Jan 20 20:46:23 UTC 2024
        ;; MSG SIZE  rcvd: 113

The regis.edu CNAME DNS Record:

        bcutcliff@ubuntu:~$ dig regis.edu CNAME

        ; <<>> DiG 9.16.1-Ubuntu <<>> regis.edu CNAME
        ;; global options: +cmd
        ;; Got answer:
        ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 51204
        ;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

        ;; OPT PSEUDOSECTION:
        ; EDNS: version: 0, flags:; udp: 65494
        ;; QUESTION SECTION:
        ;regis.edu.                     IN      CNAME

        ;; Query time: 16 msec
        ;; SERVER: 127.0.0.53#53(127.0.0.53)
        ;; WHEN: Sat Jan 20 20:47:26 UTC 2024
        ;; MSG SIZE  rcvd: 38


**The programmingkitchen.com DNS records:**

The programmingkitchen.com A DNS record:

        bcutcliff@ubuntu:~$ dig programmingkitchen.com A

        ; <<>> DiG 9.16.1-Ubuntu <<>> programmingkitchen.com A
        ;; global options: +cmd
        ;; Got answer:
        ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 23642
        ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

        ;; OPT PSEUDOSECTION:
        ; EDNS: version: 0, flags:; udp: 65494
        ;; QUESTION SECTION:
        ;programmingkitchen.com.                IN      A

        ;; ANSWER SECTION:
        programmingkitchen.com. 600     IN      A       172.200.38.66

        ;; Query time: 108 msec
        ;; SERVER: 127.0.0.53#53(127.0.0.53)
        ;; WHEN: Sat Jan 20 20:48:24 UTC 2024
        ;; MSG SIZE  rcvd: 67

The programmingkitchen.com MX DNS record:

        bcutcliff@ubuntu:~$ dig programmingkitchen.com MX

        ; <<>> DiG 9.16.1-Ubuntu <<>> programmingkitchen.com MX
        ;; global options: +cmd
        ;; Got answer:
        ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 42490
        ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

        ;; OPT PSEUDOSECTION:
        ; EDNS: version: 0, flags:; udp: 65494
        ;; QUESTION SECTION:
        ;programmingkitchen.com.                IN      MX

        ;; ANSWER SECTION:
        programmingkitchen.com. 3600    IN      MX      0 smtp.secureserver.net.

        ;; Query time: 124 msec
        ;; SERVER: 127.0.0.53#53(127.0.0.53)
        ;; WHEN: Sat Jan 20 20:49:03 UTC 2024
        ;; MSG SIZE  rcvd: 88


The programmingkitchen.com CNAME DNS record:

        bcutcliff@ubuntu:~$ dig programmingkitchen.com CNAME

        ; <<>> DiG 9.16.1-Ubuntu <<>> programmingkitchen.com CNAME
        ;; global options: +cmd
        ;; Got answer:
        ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58403
        ;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

        ;; OPT PSEUDOSECTION:
        ; EDNS: version: 0, flags:; udp: 65494
        ;; QUESTION SECTION:
        ;programmingkitchen.com.                IN      CNAME

        ;; Query time: 120 msec
        ;; SERVER: 127.0.0.53#53(127.0.0.53)
        ;; WHEN: Sat Jan 20 20:51:27 UTC 2024
        ;; MSG SIZE  rcvd: 51

**The seriouseats.com DNS records:**

The seriouseats.com A DNS record:

        bcutcliff@ubuntu:~$ dig seriouseats.com A

        ; <<>> DiG 9.16.1-Ubuntu <<>> seriouseats.com A
        ;; global options: +cmd
        ;; Got answer:
        ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 26569
        ;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 1

        ;; OPT PSEUDOSECTION:
        ; EDNS: version: 0, flags:; udp: 65494
        ;; QUESTION SECTION:
        ;seriouseats.com.               IN      A

        ;; ANSWER SECTION:
        seriouseats.com.        600     IN      A       151.101.2.137
        seriouseats.com.        600     IN      A       151.101.66.137
        seriouseats.com.        600     IN      A       151.101.130.137
        seriouseats.com.        600     IN      A       151.101.194.137

        ;; Query time: 16 msec
        ;; SERVER: 127.0.0.53#53(127.0.0.53)
        ;; WHEN: Sat Jan 20 20:52:22 UTC 2024
        ;; MSG SIZE  rcvd: 108

The seriouseats.com MX DNS record:

        bcutcliff@ubuntu:~$ dig seriouseats.com MX

        ; <<>> DiG 9.16.1-Ubuntu <<>> seriouseats.com MX
        ;; global options: +cmd
        ;; Got answer:
        ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12589
        ;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 1

        ;; OPT PSEUDOSECTION:
        ; EDNS: version: 0, flags:; udp: 65494
        ;; QUESTION SECTION:
        ;seriouseats.com.               IN      MX

        ;; ANSWER SECTION:
        seriouseats.com.        276     IN      MX      20 alt1.aspmx.l.google.com.
        seriouseats.com.        276     IN      MX      10 aspmx.l.google.com.
        seriouseats.com.        276     IN      MX      50 aspmx3.googlemail.com.
        seriouseats.com.        276     IN      MX      40 aspmx2.googlemail.com.
        seriouseats.com.        276     IN      MX      30 alt2.aspmx.l.google.com.

        ;; Query time: 0 msec
        ;; SERVER: 127.0.0.53#53(127.0.0.53)
        ;; WHEN: Sat Jan 20 20:53:14 UTC 2024
        ;; MSG SIZE  rcvd: 174


The seriouseats.com CNAME DNS record:

        bcutcliff@ubuntu:~$ dig seriouseats.com CNAME

        ; <<>> DiG 9.16.1-Ubuntu <<>> seriouseats.com CNAME
        ;; global options: +cmd
        ;; Got answer:
        ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 62012
        ;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

        ;; OPT PSEUDOSECTION:
        ; EDNS: version: 0, flags:; udp: 65494
        ;; QUESTION SECTION:
        ;seriouseats.com.               IN      CNAME

        ;; Query time: 36 msec
        ;; SERVER: 127.0.0.53#53(127.0.0.53)
        ;; WHEN: Sat Jan 20 20:53:50 UTC 2024
        ;; MSG SIZE  rcvd: 44

# TTL for each portion of DNS Hierarchy:

**TTL for regis.edu:**

        bcutcliff@ubuntu:~$ !39
        dig +nocmd +noall +answer regis.edu A
        regis.edu.              300     IN      A       216.54.215.129
        bcutcliff@ubuntu:~$ !40
        dig +nocmd +noall +answer regis.edu MX
        regis.edu.              3600    IN      MX      20 d174024b.ess.barracudanetworks.com.
        regis.edu.              3600    IN      MX      10 d174024a.ess.barracudanetworks.com.
        bcutcliff@ubuntu:~$ dig +nocmd +noall +answer www.regis.edu CNAME


**TTL for www.programmingkitchen.com**

        bcutcliff@ubuntu:~$ dig +nocmd +noall +answer www.programmingkitchen.com A
        www.programmingkitchen.com. 3600 IN     CNAME   programmingkitchen.com.
        programmingkitchen.com. 599     IN      A       172.200.38.66
        bcutcliff@ubuntu:~$ dig +nocmd +noall +answer www.programmingkitchen.com MX
        www.programmingkitchen.com. 3589 IN     CNAME   programmingkitchen.com.
        programmingkitchen.com. 3600    IN      MX      0 smtp.secureserver.net.
        bcutcliff@ubuntu:~$ dig +nocmd +noall +answer www.programmingkitchen.com CNAME
        www.programmingkitchen.com. 3585 IN     CNAME   programmingkitchen.com.
        bcutcliff@ubuntu:~$

**TTL for www.seriouseats.com:**

        bcutcliff@ubuntu:~$ dig +nocmd +noall +answer www.seriouseats.com A
        www.seriouseats.com.    30981   IN      CNAME   k.sni.global.fastly.net.
        k.sni.global.fastly.net. 12     IN      A       151.101.70.137
        bcutcliff@ubuntu:~$ dig +nocmd +noall +answer www.seriouseats.com MX
        www.seriouseats.com.    7197    IN      CNAME   k.sni.global.fastly.net.
        bcutcliff@ubuntu:~$ dig +nocmd +noall +answer www.seriouseats.com CNAME
        www.seriouseats.com.    7194    IN      CNAME   k.sni.global.fastly.net.
        bcutcliff@ubuntu:~$

**Reverse DNS lookup:**

Did reverse lookup for the IPv4 addresses provided (8.8.8.8 and 8.8.4.4), which appear to be google's public addresses:

        bcutcliff@ubuntu:~$ dig -x 8.8.8.8

        ; <<>> DiG 9.16.1-Ubuntu <<>> -x 8.8.8.8
        ;; global options: +cmd
        ;; Got answer:
        ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12398
        ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

        ;; OPT PSEUDOSECTION:
        ; EDNS: version: 0, flags:; udp: 65494
        ;; QUESTION SECTION:
        ;8.8.8.8.in-addr.arpa.          IN      PTR

        ;; ANSWER SECTION:
        8.8.8.8.in-addr.arpa.   74111   IN      PTR     dns.google.

        ;; Query time: 12 msec
        ;; SERVER: 127.0.0.53#53(127.0.0.53)
        ;; WHEN: Sun Jan 21 16:50:04 UTC 2024
        ;; MSG SIZE  rcvd: 73

        bcutcliff@ubuntu:~$ dig -x 8.8.4.4

        ; <<>> DiG 9.16.1-Ubuntu <<>> -x 8.8.4.4
        ;; global options: +cmd
        ;; Got answer:
        ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 8278
        ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

        ;; OPT PSEUDOSECTION:
        ; EDNS: version: 0, flags:; udp: 65494
        ;; QUESTION SECTION:
        ;4.4.8.8.in-addr.arpa.          IN      PTR

        ;; ANSWER SECTION:
        4.4.8.8.in-addr.arpa.   71461   IN      PTR     dns.google.

        ;; Query time: 12 msec
        ;; SERVER: 127.0.0.53#53(127.0.0.53)
        ;; WHEN: Sun Jan 21 16:50:38 UTC 2024
        ;; MSG SIZE  rcvd: 73

        bcutcliff@ubuntu:~$ dig -x 8.8.8.8 +short
        dns.google.
        bcutcliff@ubuntu:~$ dig -x 8.8.4.4 +short
        dns.google.

## Part 3: Git Hub 

I first created a new project on my GitHub titled "MSES602" as instructed.  From there I also logged into my GitHub on MS Visual studio code.  With logging into and linking my GitHub with my VS Code I was able to see all my projects there.  Traditionally I have done the following:

**Git Clone via SSH keys:**

1). Generate keys on my Linux OS/VM and then I would then include that key in my GitHub account.

2). I would make a project structure on my Linux OS and then when I wanted to clone my repository I would perform the following command:
    
    git clone <SSH link>

**Git Clone via HTTP:**

This can also be performed by command line:
    
    git clone <HTTP link>

2) Use login and password to perform git clone.

3) With the clone being automated for GitHub integration into VS Studio Code I was mostly set.  I navigated to my project/repository for this course.  I created this README and then pushed to the GitHub repository. This is the command:

        git push --set-upstream origin week1

4) Once my local git instance and GitHub were in the same state I created a branch called "week1", and this is the command I used:

        git checkout -b week1

5) Checking status of local git repository to observe any changes:
        
        git status -v ( or -vv or no option)

## Questions:

**How did you ensure that you downloaded an Ubuntu image that was not corrupt?**

Answer: You perform a checksum of the ubuntu image from their curated image compared to your downloaded image.

**What are the different ways you can access your VM via SSH. What are the advantages of
each method?**

Answer: I used my terminal window in git-bash to ssh as my user on my vm, via localhost.  You can either use a login and password or an SSH key that you provide.  Linking 

**What is the purpose of DNS?**

Answer:  The purpose of DNS is to turn human readable words and web addresses we understand (www.seriouseats.com) into an IP address that works as that sites identification to speak to other device IP's on the internet.

**What are some types of attacks used for Discovery Vulnerabilities?**

Answer: According to the video at this link (https://www.youtube.com/watch?v=-rSqbgI7oZM&ab_channel=NetworkChuck) I man-in-the-middle attack uses ARP (Address Resoultion Protocol) poisoning to get access to the network traffic of devices on a network by using the ARP.  You can do this by being on another device with access ot the network that reassigns the IP addresses from particular devices to the MAC address of the device you are using to hack into the network.  This means that the network traffic that you would normally be blind to due to modern routers being switches, and not hubs, keep the information sent between devices secure.  The way that this is used successfully is to also allow the traffic to route normally to the router and devices you have reassigned MAC addresses for, hence the name man-in-the-middle.  You then need a program (wireshark is the video's example) that can monitor all the network traffic for you.

Some other ways I discovered from this kaspersky.com (https://usa.kaspersky.com/resource-center/definitions/dns) Is DNS spoofing, which is when an attack which redirects traffic from legitimate to compromised websites.  DNS cache poisoning is also mentioned which implants a fake IP address in your local cache so that anytime you try to visit the "legitimate" website it routes you to the fraudulent one.  These appear to be mostly initiated by phishing/spam e-mails using fear to get people to click on malicious links.

Some tips to defend against these are use of Virtual Private Networks (VPN's), regular malware scans, and good information security practices regarding trusted links, certificates, and recognition of phishing attempts.

**What were your biggest difficulties with this Lab?**

I haven't used dig at all before this, so learning all the commands to complete section 2b was somewhat challenging.  I also used vagrant to stand up a VM for the first time, which ended up being very easy.  It did make finding how to checksum the Ubuntu image.  Also some of the commands I used set me back a bit.  I used **vagrant destroy** at first, which led me to believe that is how you brought down the VM in a healthy state.  This made me have to add my user back into the system and then sudoers group again.  Luckily alot of utilities and updates I made stuck.  I found that **vagrant halt/suspend** is a much better option to bring down the VM in a healthy state and made it much easier.