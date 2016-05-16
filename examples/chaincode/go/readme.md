##Read Me for Non-deterministic Chaincode ##

###Purpose###
The purpose of this modified Chaincode_Example02 is to create non-deterministic results for the purpose of testing.  That is to say results that would mimic and even **exaggerate** someof the realworld examples that would cause a non-deterministic result.  Things like lag between VPs, garbled text, malicious fault injection, etc.

###How does it work?###
The Non-deterministic version of the chaincode takes the time in nanoseconds on the VP and it uses it to seed the Rand function in order to get a non-deterministic number, for although all VPs will be executing the same code, it is a given that they will do so at a different nanosecond, and thus have a different seed for the Rand function, producing a different number for each VP.

###How can I tell what number ends up getting used?###
The seed number will appear in the VP Log, search for "Seed Number" if you want to retrieve the exact seed number used on a particular VP.

###What is Semi-nondeterministic chaincode?###
The idea behind the sieve version of pbft was to sieve out nondeterminism, for that to happen the majority of VPs would need to have the same value and the minority value will be sieved out.

This is accomplished by performing a modulo operation on the nanosecond value previously used as a seed and generating one of two values depending on whether the number is odd or even on the given VP.  This doesn't guarantee the right mix, it may take a few tries to reach the desired effect, but here too you can search the log for "Seed Number" to find which of two values was used for a particular machine.
