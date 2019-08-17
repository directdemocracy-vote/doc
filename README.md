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
It should be published on the internet, so that everyone can see it.

### Public votes

A public vote is simply the content of a referendum and the choise of an answer signed by a citizen.
A public vote should be published on the internet so that everyone can see it.
Thefore public votes are not anonymous.

### Results

Any organization can publish results by counting the votes published on the internet.
The organization may filter out votes coming from citizen with a low trust level according to a reputable truster.
Such results can be checked by anyone.

## Anonymous voting

This more complex system is similar to the public voting system.
It guarantees the anonymity and verifiability of votes, but relies on a few extra trusted compoents:

1. Anonynizers
2. Ballot boxes

### Anonymizers

When a citizen wants to vote, she securely sends her vote card and the referendum to the anonymizer with her signature.
The anonymizer sign and publish the vote card and referendum.
That means the anonymizer handles the anonymous vote of this citizen on that referendum.
If not already done, the anonymizer generate a private key specific to that referendum.
The anonymizer securely sends back to the citizen a vote token which it signs.
The vote token is actually a private key
