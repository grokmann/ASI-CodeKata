# Kata03: How Big? How Fast?
Rough estimation is a useful talent to possess. As you’re coding away, you may suddenly need to work out approximately how big a data structure will be, or how fast some loop will run. The faster you can do this, the less the coding flow will be disturbed.

So this is a simple kata: a series of questions, each asking for a rough answer. Try to work each out in your head. I’ll post my answers (and how I got them) in a week or so.

## How Big?
- roughly how many binary digits (bit) are required for the unsigned representation of:
 - 1,000 (2^10)
 - 1,000,000 (2^20)
 - 1,000,000,000 (2^30)
 - 1,000,000,000,000 (2^40)
 - 8,000,000,000,000 (2^43)
- My town has approximately 20,000 residences. How much space is required to store the names, addresses, and a phone number for all of these (if we store them as characters)?
  - A. Estimating 50 chars for name, 100 char for address, 10 char for ph# = ~160b * 20k = 3.2Mb 

- I’m storing 1,000,000 integers in a binary tree. Roughly how many nodes and levels can I expect the tree to have? Roughly how much space will it occupy on a 32-bit architecture?
  - Kind of wrong, kind of right. Depends on the type of tree.
  - A1. 1,000,000 ~~ 2^20 ~~ 20 levels, nodes = 2^19 ~ 500k
  - A2. 1.5Mb

## How Fast?
- My copy of Meyer’s Object Oriented Software Construction has about 1,200 body pages. Assuming no flow control or protocol overhead, about how long would it take to send it over an async 56k baud modem line?
  - ~500 words/page * 8b/word = 4Kb/page * 1,200 pages = 4,800Kb/56kbits/s = 4800bytes/56bits/s = 4800*8bits/56bits/s = 38400s/56 = 685.71s = 11.4 mins

- My binary search algorithm takes about 4.5mS to search a 10,000 entry array, and about 6mS to search 100,000 elements. How long would I expect it to take to search 10,000,000 elements (assuming I have sufficient memory to prevent paging).
  - 1.5 s per ^10 ~ 9s

- Unix passwords are stored using a one-way hash function: the original string is converted to the ‘encrypted’ password string, which cannot be converted back to the original string. One way to attack the password file is to generate all possible cleartext passwords, applying the password hash to each in turn and checking to see if the result matches the password you’re trying to crack. If the hashes match, then the string you used to generate the hash is the original password (or at least, it’s as good as the original password as far as logging in is concerned). In our particular system, passwords can be up to 16 characters long, and there are 96 possible characters at each position. If it takes 1mS to generate the password hash, is this a viable approach to attacking a password?
  - No. Fixed the math on this after discussing: (96^16)/(1000 × 60 × 60 × 24 × 365) = 1.65018684889166 * 10^21 days
