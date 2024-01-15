# BB84 - A Quantum Key Distribution Scheme

### CSEC464 - Concept Review - Mehul Sen

## Introduction

As part of the CSCI-464: Xtreme Theory class under [Prof. Thomas Borrelli](https://www.rit.edu/directory/tjbcis-thomas-borrelli). I took part in "Lightning Talks" which attempted to make theory less abstract and provide practical importance. For my topic, I chose to research BB84, a quantum key distribution scheme.

## Quantum Key Distribution

QKD is a secure communication method which implements a cryptographic protocol involving components of quantum mechanics. It enables two parties to produce a shared random secret key, which can then be used to encrypt and decrypt messages.
Note: This is often incorrectly called Quantum Cryptography which is the science of exploiting quantum mechanical properties to perform cryptographic tasks. QKD is the best-known example of a Quantum Cryptographic task.
Example: Alice and Bob come up with a common secret key which they can use to encrypt and decrypt the files shared among each other.

![BB84-1](images\BB84-1.png)

## BB84

Developed by Charles Bennett and Gilles Brassard in 1984, it is the first quantum cryptography protocol and is provably secure. To maintain its security, it relies on two principles of quantum mechanics:

- Heisenberg's Uncertainty Principle : we cannot know both the position and momentum of a particle at quantum level, it is impossible to create an independent and identical copy of an arbitrary unknown quantum state. (No-Cloning Theorem)
- Entanglement : Quantum particles are not always independent of each other and can be entangled, when you measure one particle, the superposition of the other instantly collapses.

It has a complexity of BQP (Bounded-error quantum polynomial time) which is the class of decision problems solvable by a quantum computer in polynomial time.

## Quantum Channel

A quantum channel is a communication channel which can transmit quantum information such as the state of qubit. There are 4 potential qubit states.

![BB84-2](images\BB84-2.png)

## The BB84 Protocol

1. Alice chooses a random string of bits.
2. Alice chooses a random basis to encode each bit with.
3. Alice encodes the bits using the chosen basis and sends qubits to Bob through a quantum channel.
4. Bob receives the qubit states through the common quantum channel.
5. Bob chooses a random basis to encode each receiving qubit state with.
6. Bob measures the polarization of the received qubit states.
7. After receiving the qubit states, Bob and Alice discuss their choses basis over a classical channel, remove the different basis.
8. Resulting shared secret is the **Sifted Key** which can be used to encrypt and decrypt the data.

![BB84-3](images\BB84-3.png)

## Security of BB84

Each randomly chosen basis by Bob has a 50% likelihood of being correct and 50% likelihood of being incorrect. The size of the sifted key would be roughly half of the initially used bits.
In the event that Eve tries to intercept the quantum channel between Alice and Bob, since she cannot make identical copies of the qubits, she would have to communicate individually with Alice, and then with Bob. This would mean that Bob’s likelihood of choosing the same basis as Alice will be reduced to 25% with the probability of being incorrect becoming 75%. With this they can easily detect if their communication is being intercepted.
One drawback for BB84 is that the bits chosen by Alice have to be random, if not, Eve is able to imitate Alice and successfully conduct a MITM attack.

## References

- [Quantum Key Distribution - Wikipedia](https://en.wikipedia.org/wiki/Quantum_key_distribution)
- [Report on Post-Quantum Cryptography - NIST](https://csrc.nist.gov/csrc/media/publications/nistir/8105/final/documents/nistir_8105_draft.pdf)
- [BB84 - Wikipedia](https://en.wikipedia.org/wiki/BB84)
- [BB84 Protocol - Youtube](https://youtu.be/44G9UuB2RWI)
- [BB84 Information - Fandom](https://cryptography.fandom.com/wiki/BB84)