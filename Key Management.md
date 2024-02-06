EX: Why is it necessary to use session keys?

- Avoid important keys being used multiple times, leading to a high possibility of key disclosure

- Helps make calculations simple and fast because encryption with session keys is symmetric encryption.

- Session keys change continuously, so if one session's key is revealed, it will not affect other sessions

Ex: Meaning of $r_1$ in Needham-Schroeder protocol. Presents details of attack with Needham-Shroeder protocol in the absence of $r_1$ ?

- $r_1$ is to check the novelty of the 2nd packet, thereby preventing the attack from reusing the 2nd packet and impersonating Cathy.

- The protocol without $r_1$ would be as follows:

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/f1cdb4d3-8c09-47ab-a878-ce671907610f/4e2677c1-0e94-46a0-b5cd-17b23a2db445/Untitled.png)

Suppose that at some point in the past, for example the year 2000, Alice and Bob used the above protocol to exchange session key $k_s$

At that time, the Eve attacker had not yet broken the $k_s$ key, so the transaction was safe at that time. However, some time later, for example in 2016, the Eve attacker somehow obtained the $k_s$ key and retrieved all the packets that were exchanged in the 2000 session.

By 2017, Alice and Bob used the above protocol to exchange keys. At this time, Eve will impersonate Cathy to trick Alice and Bob as follows: Eve blocks packet 1 from reaching Cathy, Eve then impersonates Cathy and resends packet number 2 that was used in 2000. Alice received a packet sent from Eve but thought it was a packet sent from Cathy, because this packet was encrypted with Alice and Cathy's secret key. After that, Alice and Bob will exchange packets 3,4,5 according to the correct protocol. As a result, Alice and Bob will reuse the key $k_s$ used in 2000. The danger is that Eve already knows this key. And so Eve can hear the entire exchange between Alice, Bob or impersonate Alice and Bob.


Ex: Suppose A and B have the same party C. A and B want to establish a session key k~s~ through C with the following protocol

Alice --> {request for session key to Bob} k~AC~ Cathy
Alice <-- {k~s~} k~AC~ || {k~s~} k~BC~ Cathy
Alice --> {k~s~} k~BC~ Bob

Please tell us what weaknesses this protocol has and how it can be overcome

Sol: 

The parties can not be mutually authenticated, meaning that when party X receives a message said to be from Y, then
X cannot verify whether the message was sent directly by Y or sent by an impersonator Y. Therefore, although the attacker cannot retrieve the confidential information that the parties transfer to each other, they can make the parties accept and process old information (replay), leading to redundant processing that can cause damage. 

