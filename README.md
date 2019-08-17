# directdemocracy.world

directdemocracy.world aims at establishing [direct democracy](https://en.wikipedia.org/wiki/Direct_democracy) everywhere in order to bring peace, safety and prosperity to humananity, including saving the climate and the biodiversity.
The principle is that people will become citizens by organizing referundums and voting regardless of any official acknowledgement.
Vote results from a limited number of citizens could be considered as survey results.
Such results could feed debates, influence political decisions and incitate more people to become citizens.
Vote results from areas where a majority of people are citizens will become significant from a democratic point of view.
This will increase the pressure on governments to respect the democratic choices expressed by their people.
Ultimately this bottom-up initiative will enforce direct democracy everywhere in the world.

directdemocracy.world is a decentralized system running on the internet and providing both public and anonymous voting systems.

## Public voting

This simple system is relying on six components:

1. citizen cards.
2. endorsements.
3. trusters.
4. referendums.
5. public votes.
6. results.

### Citizens cards

Anybody can register to become a citizen.
The registration process simply requires that you fill-in a citizen card with your name, picture, address, etc., sign it electronically and publish it on the internet, so that everyone can see it.
No review or approval is needed.
However, your vote wont be significant if your citizen card is not trusted.

### Endorsements

As a registered citizen, you can endorse other citizens by reviewing and signing electronically their citizen card.
The review process is a questionnaire in which you will assess the accuracy of the information provided on other's citizen card.
Obviously, you should assess only people you know well and can meet in person.
Like citizen cards, endorsements are published on the internet so that everyone can see them.

### Trusters

Trusters are independent algorithms that process the endorsements published on the internet to generate a trust level for each citizen. Trust levels are signed by trusters and published on the internet so that everyone can see them.
Any individual or organization can become a truster.
Trusters should develop the best trust algorithm to establish a good reputation.

### Referendums

A referendum is a text aiming at changing the law in a city, state, country or the whole world.
It should contain the following elements:
- Area of application (cities, states, countries, world)
- Title
- Description of the law
- A question (usually do you agree with this proposal?)
- A list of possible answers (usually yes/no/abstention)
- A list of acknowledged trusters with a minimum trust level for each one.
- A deadline for the publication of results.
It should be published on the internet, so that everyone can see it.

### Public votes

A public vote is simply the content of a referendum and the choise of an answer signed by a citizen.
A public vote should be published on the internet so that everyone can see it.
Thefore public votes are not anonymous.

### Results

Any organization can publish results by counting the votes published on the internet.
The organization should filter out votes coming from citizens with a too low trust level.
Such results can be checked by anyone.

## Anonymous voting

This more complex system is similar to the public voting system.
It guarantees the anonymity and verifiability of votes, but relies on an extra trusted component: the anonymizers.
Optionally verifyers can be requested to assess the correct functionning of anonymizers.

### Anonymizers

When a citizen wants to vote, she generate a new pair of private and public key specifically for this referendum.
Then she securely sends two signed packets to the anonymizer.
The first one contains her vote card and the referendum.
The second one contains the public key.
The anonymizer checks that both packets are received and that the citizen is entitled to vote (area, necessary trust level).
If not, it declines the request of the citizen.
Otherwise, the anonymizer signs the first packet and will publishes it when the vote period is over.
That means the anonymizer handles the anonymous vote of this citizen on that referendum.
The anonymizer then removes the signature from the second packet and save the public key in its database without any reference to the citizen.
The citizen selects an answer in the referendum, add the public key, sign it with the private key and publish it.
Once the vote period is over, the anonymizer publish all the public key it stored in a random order, signed with its signature.
Anyone can then verify that the number of published public keys matches the number of published vote cards/referendum packets.
If number do not match, something has go wrong and the vote should not be considered secure.

Citizen will freely choose anonymizers with a good reputation to cast their votes.
The reputation of anonymizers may be affected by obvious disfunctionnings or complains of citizens about their participation not being published (and hence their vote being likely usurpated) or their anonymity not being respected.
Therefore a good reputation system should be setup to assess the reputation of anonymizers.

### Verifyers

When sending her public key to the anonymizer, citizens should also securely send a signed copy of this key to a number of verifyers. Verifyers should be fully independent from the anonymizer.
They can check after the results are public if an anonymizer has cheated simply by comparing the list of published public key to the ones received directly from the citizen.
