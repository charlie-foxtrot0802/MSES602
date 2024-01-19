## Week 1 Lab Assignment. 

What to Submit

Each week you will submit a document (README.md) in Markdown format to the appropriate branch
(week1, week2, etc.)  in GitHub.   At the end of this class you will be comfortable with a Git Ops
workflow, but if you don't have previous experience with this, ask for help. Create a folder for your
screen shots called "images".  The README.md document should be one layer above the "images"
folder.

The README.md document should include:

Description of your Step by Step Procedure for Part 2.   
A.) Include important screen shots (between 3 and 5 ) like some screen shots of the installation,
    final results of the VM running Virtual Box, a login terminal to the VM, etc.   

B.) Include code commands for Part 2b (e.g. dig) and results in code format (not screen shots).

Answer to the following questions.
How did you ensure that you downloaded an Ubuntu image that was not corrupt.   a.
b. What are the different ways you can access your VM via SSH.   What are the advantages of
each method.
c. What is the purpose of DNS?
d. Research the kind of attacks that could use "Discovery Vulnerabilities" (DNS is an example)
to hack into a victims computer.   Tip:  Search for "Network Chuck" on YouTube and look for
Man in the Middle Attacks, ARP poisoning, etc.
e. What were your biggest difficulties with this Lab?

Description of your Step by Step Procedure for Part 2.   
A.) Include important screen shots (between 3 and 5 ) like some screen shots of the installation,
final results of the VM running Virtual Box, a login terminal to the VM, etc.

B.) Include code commands for Part 2b (e.g. dig) and results in code format (not screen shots).


Vagrant commands:

**This creates a vagrant file in directory I created.**

    vagrant init alvistack/ubuntu-20.04

**This downloaded and launched my VM using virtualbox.**

    vagrant up

**Image below is of my git-bash using vagrant to bring up my ubuntu in virtualBox**

![alt text](images/vagrant_gitBash.PNG)

I had to use the username and login as vagrant then create a username and password for myself, and then add my user to the sudoers group.  After that I installed the update using:

    sudo apt-get update

![This is the picture of the completion of the update](images/ubuntuGetUpdate.PNG)

Once that was complete I had to install dig, which was done using the following command:

    sudo apt-get install dnsutils



**Part 3: Git Hub**

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



