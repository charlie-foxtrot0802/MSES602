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

# This creates a vagrant file in directory I created.
vagrant init alvistack/ubuntu-20.04

# This downloaded and launched my VM using virtualbox.
vagrant up

# Checksum automatically performed by vagrant for Ubuntu image.
