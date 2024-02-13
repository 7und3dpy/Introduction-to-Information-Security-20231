
<!--
## Exam 1

1. When first learning about the DES code system, a student A commented that perhaps only designing 8 loops would be enough; Student B responded that years of practice showed that using up to 16 loops was correct. Let me clearly analyze the rationale for the above comments. 


2. Suppose in an operating system that simulates Unix, one needs to set up a system function command that allows each user to ask special test questions in case of needing to restore account control when accidentally forgetting the password ( as well as set the corresponding answer). This system command will have to access system resources with root (superuser) rights. Shows the solution mechanism so that any user can download and execute this system command file.

3. Traditional password authentication systems can have problems with terminal attacks, when an attacker The public can access the connection from the client to the server. Clearly analyze this problem and how to solve it. Refers (briefly) to the Kerberos system as a solution general decision. 


4. How to generate large prime numbers (RSA) efficiently? State and analyze a specific algorithm if known.


# Part A
## Morning
X = 48

Z = X mod 4

Suppose H is a hash function with output size of (Z+3)*16 bits. Suppose Scorp-k (k=1-9) is a chip capable of performing 10k+2 H hashes per second (for example, Scorp-2 can perform 10000 hashes per second). This is the fastest and most economical chip in its class on the market at a unit price of (k+1)! *$1000 (Scorp-2 costs $6000 with 6=3!). Consider the following Bit-Commitment protocol used for soccer betting and address the two questions below.

(1) Alice creates 2 random bit strings, R1 and R2, the length is (Z+2)\*12 and (Z+2)\*10 bits 

(2) Alice creates and sends to Bob: M = H(R1 || R2 || **_b_**) || R1 

(3) When it's time to announce **_b_**, Alice sends Bob: (R2,**_b_**) 

(4) Bob checks the validity by recalculating the hash value H(R1 || R2 || b) and comparing it with the value value received from (2) 

a) How much money does the dealer Bob have to invest to be able to correctly guess **_b_** in 5 minutes? 

b) Suppose that the betting game starts 3 days before the football match event, that is, the rules and hash algorithm are announced 3 days Before ending the bet, how much money will Alice have to invest to be able to trick Bob according to the scenario: Alice prepares for step (1) so that later in step (3) she can change the value of bit **_b_** success (if needed). 

c) If we use the above protocol to let Alice "commit" a 10-bit string, that is, **_b_** is a 10-bit binary string, will the security guarantee be as high as before? Use probability for analysis.

-->

# Final exam 20212
1. Analyze the weaknesses of building an access control mechanism based on the definition of ACM using 3 sentences

Sol:

ACM is large, so it consumes memory resources, not to mention many empty cases. For saving, the entire thing is not necessary but can be decomposed matrix to save memory and make processing more efficient. Decomposition by row creating capability lists attached to user subjects or decomposition by column: create management objects that are access control list, which are most common

2. Alice builds her RSA based on 2 prime number p and q of size 50 and 100 digits, while Cathy builds it with 2 numbers of length 60 and 70 digits. Let's compare and analyze the safety between these two cases which side is better, please explain in 1-2 senetences

Sol:

It's seem that Alice's solution is better because n is larger. However, when the adversary tries to factorize the prime numbers, it will soon find p (smaller number first) so Cathy's solution is better. 


Ex: During a security lecture, instructor Lam introduced a simple basic protocol PRT_AU (see below) and asked students to discuss in groups to analyze the purpose & critique pros and cons; then try to design a protocol that does better or is more beneficial in some way.

PRT_AU: 

1.  A-->S: ID<sub>A</sub>

2.  S-->A: Password Request

3.  A-->S: H(PW<sub>A</sub>)||T  

PRT_00 (An):

1)    A-->S: ID<sub>A</sub>

2)    S-->A: R

3)    A-->S: H(PW<sub>A</sub>||R)

PRT_10 (Binh):

1) A-->S: ID<sub>A</sub>

2) S-->A: R

3) A-->S: H(PW<sub>A</sub>||R)

4) S-->A: {k<sub>s</sub>}p<sub>A</sub>

PRT_01 (Chi):

A-->S: ID<sub>A</sub> || H(PW<sub>A</sub>||T) || T


PRT_11 (Dung):

1)  A-->S: ID<sub>A</sub>

2)  S-->A: R

3)  A-->S: {R+1}p<sub>A</sub>

4)  S-->A: {k<sub>s</sub>}p<sub>A</sub> where pA = H(PW<sub>A</sub>)

The symbols used above have the following meanings:

ID<sub>A</sub> – is the ID (identity) of A; R is a random number; T is a timestamp at the current time (by computer clock)

PW<sub>A</sub> is A's password string; p<sub>A</sub> is the hash value of A's password, i.e. p<sub>A</sub> =H(PW<sub>A</sub>) and where H is a pre-determined hash function.


Q1: Analyze the purpose of PRT_AU and then compare PROT_0x to clearly see the advantages and disadvantages.

Sol:

The purpose of the PRT_AU is to authenticate identityy in password login. However, the system (S) only needs to store the hash value of their password. When analyzing the difference with An or Chi's solution, it should be clearly stated that the PRT_AU solution is weaker because it seems to use timestamp to prevent replay attacks but fails because the adversary can completely create fake T combined with H(PW<sub>A</sub>) eavesdropping. Meanwhile, An/Chi's GP can resist replay attacks: An's can uses a challenge-response mechanism with a random number R, while Chi's puts T in the hash so it cannot be interfered with. Both of these solutions S always stores A's password itself (not just the hash value).

Q2: Analysis clearly shows the differences and new features of PROT_1Y compared to the two protocols in the above sentence (1) ?

Sol: 

The general novelty compared to PRT_AU is authentication with a challenge-response mechanism using random values However, R – the value always changes and does not repeat across sessions of the protocol, thus not allowing an adversary to perform a replay attack by trivially replaying old records. Note that the solution Binh's solution still needs S to store the user's original password value, while Dung's solution requires S to only store the hash value of the password. The new feature (and key difference from PROT_0X) is the PROT_1Y protocol for Allows creating a new session key for user A that can be used to connect cryptographically to the system in the next exchange of information or data.

Q3: Mr. Lam then presented another advanced version and challenged the class to analyze and find the remaining problem.


1) A-->S: ID<sub>A</sub> || ID<sub>B</sub> || r<sub>1</sub>
2) S-->A: {ID<sub>A</sub> || ID<sub>B</sub> || r<sub>1</sub> || k<sub>s</sub> || {ID<sub>A</sub> || k<sub>s</sub> || r<sub>1</sub>} p<sub>B</sub> } p<sub>A</sub>
3) A-->B: {ID<sub>A</sub> || k<sub>s</sub> || r<sub>1</sub>} p<sub>B</sub>
4) B-->A: {r<sub>2</sub>} k<sub>s</sub>
5) A-->B: {r<sub>1</sub> + r<sub>2</sub>} k<sub>s</sub>

Student Dat answered the teacher's question well, correctly analyzed the existing problem and found a solution success, in which only one modification in step 5 needs to be made. Please analyze the purpose of the protocol and try to guess the problem that Dat pointed out? If possible please Point out solutions as well as Dat's solution ideas.

Sol: 

This protocol is designed to perform session key generation for A and B through support of S (of course, including S's authentication to A) and hopefully prevent attacks from enemies who know the old (previously used) session key. The designer's idea is that even if the adversary has an old session key, it will not be able to respond successfully (in step 5) because it does not know r<sub>1</sub>. However, the sinister enemy may have recorded everything messages in the past, so it is possible to trace the messages used with the old session key and from there easily find r<sub>1</sub> (try to think more about why?). This is the weakness that Dat discovered. From there, come up with a solution to hide r<sub>1</sub>, such as using hash in step 5 (please find a way to specify it yourself).

Can you guess and explain Dung's idea in details?

Sol:

In the original PRT_AU protocol, the third step presents a security vulnerability. The hashed password of user A is concatenated with a timestamp and transmitted. This exposes the hashed password to potential interception by a malicious actor, such as Eve, who could then impersonate user A in future communications.
Dung’s proposed protocol mitigates this risk by implementing a challenge-response mechanism. In this improved protocol, the server S sends a random number R to user A. User A then encrypts the value of R+1 using the hash of their password and sends it back to the server. This allows user A to prove their identity without transmitting their password or its hash. The server can decrypt the received value using the stored hash of A’s password and verify if it matches R+1. If the verification is successful, the server acknowledges the authenticity of user A and sends a session key ks, encrypted with the hash of A’s password, for secure communication during the session.
In summary, Dung’s protocol enhances the security of the authentication process by preventing the exposure of the password hash and introducing a session key for secure communication. This makes it more resistant to man-in-the-middle attacks and impersonation attempts.

EX: From M, an English text, one generates Vigenere code with the keys K<sub>1</sub>, K<sub>2</sub>, K<sub>3</sub> below to create ciphertexts X<sub>1</sub>, X<sub>2</sub> and X<sub>3</sub>. Let's try to give a comparative assessments of the ICs code X<sub>1</sub>, X<sub>2</sub> and X<sub>3</sub> with clear and detailed arguments. K<sub>1</sub> = "12345678", K<sub>2</sub> = "hellobello", K<sub>3</sub> = 8 characters extracted from the student full name (i.e delete some characters from the full name). For example, "Nguyễn Lê Thanh" ==> "Nlethanh" or "nguyentha", ...

Sol:

We have: 

K<sub>1</sub> = "12345678"
K<sub>2</sub> = "hellobello"
K<sub>3</sub> = "tranmuan"

K<sub>1</sub> has 8 substitutions, K<sub>2</sub> has 5 substitutions, K<sub>3</sub> has 6 substitutions. Because the more potential tables, the more the IC is reduced. Based on the comparison of the number of substitution tables used in the keys, we have 5 < 6 < 8, so the IC of code X<sub>2</sub> is highest, then X<sub>3</sub> and finally X<sub>1</sub>. 

- We will explain why the more potential tables used, the lower the IC (1)

- We see that the more substitutions a plaintext uses to encode, the more flat the frequency of letters in the alphabet appears.

On the other hand, the concept of IC is defined by : 

$$IC = \frac{\sum{f_i(f_i - 1)}}{n(n - 1)}$$ 

where f~i~ is the frequency of letters in the alphabet with i = 1,...,26 and n is the number of letters in the ciphertext. According to the Cauchy inequality, $\sum{f_i(f_i - 1)}$ is the smallest when the f~i~ are equal. Therefore, if the f<sub>i</sub> are closed to each other, the IC decreases, thereby (1) is proven. 

Ex: Point out the connection between the birthdate paradox and Diriclet's principle. Why we need to care about that, with regard to information security? 

Sol: (3/4 đ)

The Birthday Paradox refers to the surprising probability that in a group of just 23 people, there’s a 50% chance that at least two people have the same birthday.
Dirichlet’s Principle is a theorem in mathematics that states that in a bounded domain, if you place n+1 rabbits into n cages, at least two rabbits will end up in the same cage. This suggests an exhaustive search: given |Y| as the size of the hash output, if you try |Y| + 1 messages, you are guaranteed to find a collision.
Both these principles are connected in the sense that they deal with probabilities in large data sets and the potential for collisions or matches.
In information security, this concept is used in a type of attack known as the Birthday Attack, which aims to find collisions in a hash function. Therefore, in practice, we need to choose |Y|, the size of the hash output, to be large enough so that an exhaustive search is computationally infeasible, thereby enhancing security.


<!--Ex: Alice and Bob have the following exchange: 

Ex: When first learning about the DES code system, a student A commented that perhaps only designing 8 loops would be enough; Student B responded that years of practice showed that using up to 16 loops was correct. Let me clearly analyze the rationale for the above comments. 

Ex: Suppose in an operating system that simulates Unix, one needs to set up a system function command that allows each user to ask special test questions in case of needing to restore account control when accidentally forgetting the password ( as well as set the corresponding answer). This system command will have to access system resources with root (superuser) rights. Indicates the solution mechanism so that any user can download and execute this system command file.

Ex: Traditional password authentication systems can have problems with terminal attacks, when an attacker can access the connection from the client to the server. Clearly analyze this problem and how to solve it. Refers (briefly) to the Kerberos system as a general solution.

Ex: How to generate large prime numbers (RSA) efficiently? State and analyze a specific algorithm if known.-->

Ex: Alice and Bob have the following exchange: 
- a) Alice say that the correctness of RSA is directly derived from Euler's theorem; but Bob disagrees, which ever side you think is right, please argue to defend that opinion
- b) Bob said that the extended GCD algorithm is a series of iterations in which each loop must execute a series of 8-9 complicated computation statements that are difficult to remember. However, Alice say that is not the case , each loop must consist of 3 small processing blocks with similar properties. If you agree with me, please argue to defend your opinion. 

Sol:
a) We see, the correctness of RSA algorithm is deduced from Euler's theorem only in the case where x and or are prime together, then we have: 

$$X^\phi(n) \equiv 1 mod n$$

However, in the general case, we have: 
$$X^{\phi(n) + 1} \equiv X mod n (2)$$

Indeed, we will prove (2). We have $n = pq$
We will prove: $$X^{\phi(n) + 1} \equiv X (mod p) (3)$$
$$X^{\phi(n) + 1} \equiv X (mod q) (4)$$

Then from (3), (4) combined with the Chinese remainder theorem, we will have something to prove (2)

Indeed, (3) and (4) are always true in all cases, even if X is not coprime with n

Proof (3): If X is divisible by P, then $X^{\phi(n) + 1} \equiv 0 (mod p)$
$$X^{\phi(n)} \equiv X (mod p)$$

If X is not divisible by P, we have $\phi(n) + 1 \equiv (p-1)(q-1) + 1 \Rightarrow \phi(n) + 1 \equiv 1 mod (p-1)$

According to the Fermat's little theorem, we have: 
$$X^{(p-1)(q-1)} \equiv 1 (mod p) \Rightarrow X^{\phi(n)} \equiv 1 (mod p)$$

Thus (3) is true for all X
Similarly (4) is true for all X

$\Rightarrow X^{\phi(n) + 1} \equiv X (mod n) (q.e.d)$

b) I agree with Alice opinion. It is true that the extended GCD algorithm is a loop algorithm that must perform 8-9 operations each time, but the operations can be divided into blocks of similar nature and are easier to remember. Specifically, the 3 blocks are: 

In case $r \neq 0$: 

- Block 1 includes reassignments to $n_1$ and $n_2$ : $n_1 = n_2, n_2 = r$

- Block 2 includes reassignments to $a_1$ and $a_2$ : $t = a_2, a_2 = a_1 - q * a_2, a_1 = t$

- Block 3 includes reassignments to $b_1$ and $b_2$ : $t = b_2, b_2 = b_1 - q * b_2, b_1 = t$

So it can be seen that all 3 blocks perform reassignments of values has to 2 variables, moreover, blocks 2 and 3 have similar reassignment processing structures. In terms of hardware, block 2 and block 3 can have the same hardware design, in terms of software block 2 and block 3 can use the same procedure. Although block 1 has an internal value assignment structure that is not similar to block 2 and 3, the assignment in block 1 is very simple and easy to remember

Ex: In a multinational enterprise with a system of many servers installed in a very large area, people used the Needham-Schroeder protocol to establish a symmetric encryption key security channel between two certain servers when necessary. Suddenly, people discovered case where confidential data, although encrypted during transmission still fell into hands of competing company. The likely cause was that old session key was accidentally lost into the hands of a bad person

a) When discussing system upgrades, an expert A suggested using a timestamp mechanism but was not supported by some other experts because of the characteristics of a large number of servers with widespread coverage. Let's try to clarify this objection.

b) Expert B recommends making sure to change the session key to a new one every hour (at the beginning of each hour). Let one analyze the possibility of immplementing this solution.

c) Expert C believes that it is possible to upgrade the public symmetric key generation protocol without using timestamps, based on the additional use of hash values in the challenge-response mechanism (between Alice and Bob). Let's try to analyze and clarify this opinion

d) Expert D proposed an improved solution using counters to overcome the attack. Can you describe this solution in detail ?

Sol:

a) 
- Using additional timestamps can avoid replay attacks in case an attacker captures an old session key. However, if timestamps are used as a tool, there may be missynchronization. For example, one user participating in the process has a timer that is skewed compared to everyone else's, then whenever this user sends a packet to the server, the server then compares the timestamp and see the difference, through which server will think that an attacker is performing a replay attack and will not accept the packet from that uer, an in fact it is actually the user who is sending the message.

b) In case of hourly session key exchange (beginning of each new hour). We need to pay attention to the following issue: 

+ It is really necessary to establish a new session key at the beginning of each time frame, i.e setting up 24 new session keys with a partner every day ? For example, that company does not need to exchange data with too much frequency. In a day, if a company only needs to communicate with one company 2-3 times, but we regularly create 24 session keys, that is redundant

+ Second problem: the Needham-Schroeder protocol establishs session keys through a trusted intermediary (C). A company has a very large area, which means it needs to exchange a lot of information with many partners. Generating session keys periodically at the beggining of each time frame will create pressure for third party C to process at the same time. It may cause overload for thirdparty C. If processed by having multiple partners C, it will encounter additional problems with third-party and partner management. 

+ There are communication process that can last for hours, with huge amounts of data. Hence generating the key hourly sessions will cause conflicts, when staring a new time frame, the question is whether to use the old session key on the new time key frame ?

c) 

A -> B : {Alice || $k_s$}$k_{BC}$

B -> A : {$r_2$ || h($r_2$)}$k_s$

A -> B: {$r_2 - 1$ || h($r_2 - 1$)}$k_s$

with h being a common hash function in the company and the secret, the above method is possible when the enemy holds the old key but does not hold the hash function, he will not be able to respond accurately to B $\Rightarrow$ Attacker fails. However, this solution requires the hash function to be secret. 


d) The protocol using additional counter variables will be implement as follows: 

A -> C : Alice || Bob

C -> A : {Alice || Bob || Counter<sub>AC</sub> || k<sub>s</sub> || {Alice || Counter<sub>AB</sub> || k<sub>s</sub>}<sub>k<sub>BC</sub></sub>}<sub>k<sub>AC</sub></sub>

A -> B : {Alice || Counter<sub>AB</sub> || k<sub>s</sub>}<sub>k<sub>BC</sub></sub>

B -> A : {r<sub>>1</sub>}<sub>k<sub>s</sub></sub>

A -> B : {r<sub>1</sub> - 1}<sub>k<sub>s</sub></sub>

After performing the above linking process, counter<sub>AC</sub> will be increased by 1, counter<sub>AB</sub> will also be increased by 1. During storage, counter is treated as a symmetric variable used by both parties and it must be kept secret so that it can not be stolen by an attacker 

We see the above protocol is first improved in the Needham-Schroeder so the parties can authenticate each other during the information transfer process

We will further prove that the above protocol is resilient against replay attack and in case the attacker has some session key k<sub>s</sub>

Indeed, if an attacker wants to forge a message C -> A, then A can be completely checked with counter<sub>AC</sub>. In addition, an attacker without the key k<sub>AC</sub> can not expose and get the value of counter<sub>AC</sub>. Next, if the imposter has the session key k<sub>s</sub> and wants to establish a fake conversation between A and B, it will not work because A -> B needs additional information counter<sub>AB</sub>, if the attacker does not have the key k<sub>BC</sub> then it is not possible to see counter<sub>AB</sub>, through which B can completely detect the fake enemy and not establish the link. 
 

<!--
chosen-plaintext attack:
- Attacker chooses his own plaintext and sign or encrypt it. 
- In other words, the attacker can create plaintext and turn it into ciphertext to 
  analyze pattern or statistic to crack 
known-plaintext attack:
- The attacker some how can steal the plaintext form victim and ciphertext 
  correspond it
- From this, attacker can analyze which key for this cipher
4)	Show the meaning and purpose of CAPTCHA and how it works.
- Is a type of challenge–response test used in computing to determine whether the 
  user is human
- Protect the server from the attack of automated computers on the internet instead of 
  humans via (sending prove of captcha work )
- Not involve any thing like protect from replay attack. If protect from replay-attack, 
  server should send something like nonce-string-sequence
Part B:
2) 
a) This selection not good because, K can choose with small values like (3,5,7)
lead to attacker can easily guess
b) 
- Assume that the distance (average) between 2 prime number in log(n) 
function where n is upper-lower bound of N. 
then the probability of prime generate is 
k*(log2(10**200)-log2(10**199)) = k*3.3
then average time will be 
k*3.3*0.15/2 = 0.2475*k

Part C:
1)this protocol is better than PROT_0 because it has challenge-responce mechanism 
which prevent terminal attack and replay attack since R is only valid once
After step 4: S and A are communicate via session-key: ks which is more secure 
2)
The purpose of this protocol is mutually authenticate identities of A&B and 
create session-key for A&B
Issue: 	after Step 4: A and B share common session key k_s only people who have 
	session key can read the message. 
	At Step 5: we should replace r1+r2 by counting mode or something like 
	that. Then when B challenge A with r2 that force A responce B with 
	something only from r2 mapping to it. So that B can confirm that 
	responce from A and not some body can evedrop from it
-->