# votapopuli

votapopuli aims at establishing [direct democracy](https://en.wikipedia.org/wiki/Direct_democracy) everywhere in order to bring peace, safety and prosperity to humananity, including saving the climate and the biodiversity.
The principle is that people will become citizens by organizing referundums and voting regardless of any official acknowledgement.
Vote results from a limited number of citizens could be considered as survey results.
Such results could feed debates, influence political decisions and incitate more people to become citizens.
Vote results from areas where a majority of people are citizens will become significant from a democratic point of view.
This will increase the pressure on governments to respect the democratic choices expressed by their people.
Ultimately this bottom-up initiative will enforce direct democracy everywhere in the world.

votapopuli is a decentralized system running on the internet and providing a voting system relying on six components:

1. citizen cards.
2. endorsements.
3. trusters.
4. referendums.
5. anonymizers.
6. verifyers.

### Citizens cards

Anybody can register to become a citizen.
The registration process simply requires that you fill-in a citizen card with your name, picture, GPS location of address, etc., sign it electronically and publish it on the internet, so that everyone can see it.
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
- The area of application (GPS coordinates of an area, usually corresponding to a city, a state, a country or the whole world).
- Title
- Description of the law to be applied in the area.
- A question (usually do you agree with this proposal?)
- A list of possible answers (usually yes/no/abstention)
- A list of acknowledged trusters with a minimum trust level for each one.
- A deadline for the publication of results.
It should be published on the internet, so that everyone can see it.

### Anonymizers

When a citizen wants to vote, she generate a new pair of private and public key specifically for this referendum.
Then she securely sends two signed packets to the anonymizer of her choice.
The first packet contains her vote card, the referendum and the anonymizer.
The second packet contains the public key and the referendum.
The anonymizer checks that both packets are received and that the citizen is entitled to vote (area, necessary trust level).
If not, it declines the request of the citizen and publish a message saying it refused to allow this citizen to vote to this referendum.
This message is also sent back to the citizen.
Otherwise, the anonymizer signs the first packet, publishes it and sent it back to the citizen.
This way, the anonymizer announces publicly that it handles the anonymous vote of this citizen on that referendum.
The anonymizer then removes the signature from the second packet, sign it, send it back to the citizen and store it temporary.

The citizen selects an answer in the referendum, sign it with the private key and publish it.
Once the vote period is over, the anonymizer publish in a random order all the public key it signed and stored.
Citizens should also publish the same information they have received from the anonymizer.

Citizen will freely choose anonymizers with a good reputation to cast their votes.
The reputation of anonymizers may be affected by obvious disfunctionnings or complains of citizens about their participation not being published (and hence their vote being likely usurpated) or their anonymity not being respected.
Therefore a good reputation system should be setup to assess the reputation of anonymizers.

### Verifyers

Anyone can verify the information published by voters, trusters, anonymizers, etc. to detect possible frauds in the system.
For example, for each anonymizer and each referendum, the number of published public keys should match the number of published vote cards/referendum packets.
If numbers do not match, something has go wrong, the vote should not be considered secure and the reputation of the anonymizer should decrease.

![Anonymizer principle](https://raw.githubusercontent.com/votapopuli/doc/master/vote.png "Anonymizers principle")
