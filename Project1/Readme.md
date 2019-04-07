# Project 1

## Description

Develop a security protocol that is used for establishing a session between two agents.

Agents:
- A Client
- B Service Delivery Server
- Authentication Server

Objectives:
- Establish a session key between A and B
- Mutual authentication between A and B

Assumptions and Restrictions
- A has a symmetric key shared with S
- B has a symmetric key shared with S
- Only S can generate session keys
- Do not use timestamps
- efficiency in the messagesstructure and their number

## Implementation details

We started by creating a simple protocol used for communication between 2 agents without any authentication server.

As protocol properties we had in mind authentication of the nounces sent between the 2 agents and the secrecy of those.

First attempt : Here we made a simple communication between 2 agents knowing their public keys 

```
1. A -> B : {Na'.A}_Kb
2. B -> A : {Nb'.B}_Ka
```

Second attempt follows Nspk protocol using a server without timestamp and lifetime

```
1. A -> S: A,B
2. S -> A: {Kab,B,{Kab,A}_Kbs}Kas
3. A -> B: {Kab,A}_Kbs, {Na',A}_Kab
4. B -> A: {Nb'.B}_Kab
```

The points of interest are that Kab to be secret between A,B and Na' and Nb' to be safely communicated between parties using Kab.

This version introduces the server but still has some issues like an replay attack since messages don't have a timestamp/lifetime.

## Referecens

http://www.cs.cmu.edu/~dga/15-712/F07/papers/Burrows90.pdf 