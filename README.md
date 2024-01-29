# **Written Assignment for Week 2** 

# What are the Pros and Cons of The Three Cloud Service Models?

| Cloud Model                        |             Pros             |               Cons           | 
| :--------------------------------: | :--------------------------: | :--------------------------: |
| Infrastructure as a Service (IaaS) | |
| | - Most similar to existing IT resources. | - Security is outsourced to vendor. |
| | - Allows for scalability of operations. | - Might still be more costly due to hardware procurement an maintenance. |
| | - Allow direct control of your own resources. | - Limited control of networking components. |
| | - Can control what OS you are using and storage solutions. | |
| Platform as a Service (Paas) | | 
| | - Not required to manage your own physical infrastructure. | - Can lack scalability capabilities. |
| | - Libaries, service, and tools are provided. | - Does not control network, storage, or operating system. |
| | | - Can be difficult to move from vendor to vendor with this model. |
Software as a Service (SaaS) | | |
| | - Lowest barrier to entry, easiest to get into. | - No control over systems, use what vendor offers. |
| | - Easily scalable operations, just upgrade plans to accommodate more users. | - Can have software conflicts with provider. |
| | - Can access your product from almost anywhere there is a web browser. | | 



## What are the Three Different Solutions for Managing State of Services in the Cloud.

The three ways state can be stored in a service are in each service instance, in the clients of that service, or an external storage area (database).  The first option will have a class or method that will increment internally to for each client-side call to the service.  The second option will rely on the client itself to pass the amount of times it has called the service, then increment with a class/method there as well.  The final option could use a database to store and pull the information about its interactions with the client.  The first option is a stateful service, while the second and third are stateless services.

### What is an example of a program that is performing the three storage options from the previous question?

A relevant example of a stateful service could possibly using a search engine, and I'm going to use Craigslist.com for the example.  So If I am on craiglist and I am looking for cars I might enter "used honda civic" in the search bar.  As an example for the first type of storing state, when I enter the search the client interface sends the query to the search engine service and the service itself recognizes how many times I have entered "used honda civic" in the client GUI.  For the second example the frontend/client-side would remember how many times i've looked for "used honda civic" and pass that number of queries onto the service itself to give it the state information.  For the last example, perhaps if you are logged into an account or authenticated in some way, the search engine service remembers my search history because the service passes on my search queries to a database, and can recall them when I navigate to the site.  This might present me with previous searches immediately upon typing my search.  
