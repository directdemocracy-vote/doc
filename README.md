# suffragio

suffragio aims at establishing world-wide [direct democracy](https://en.wikipedia.org/wiki/Direct_democracy) in order to bring peace, safety and prosperity to humananity, including saving the climate and the biodiversity.
The principle is that people will become citizens by proposing referundums and voting regardless of any official acknowledgement.
Vote results from a limited number of citizens could be considered as simple survey results.
They could feed debates, influence political decisions and incitate more people to become citizens.
Vote results from areas where a majority of people are citizens will become significant from a democratic point of view.
This will increase the pressure on governments to respect the democratic choices expressed by their people.
Ultimately this bottom-up initiative will enforce direct democracy everywhere in the world.

suffragio is a voting system with the following properties:

- open to anybody with internet access (smartphone or computer).
- fully decentralized (nobody can control it).
- verifyable (check that my vote was taken into account, check that others didn't cheat).
- relying on open-source specifications and open-source software.
- providing easy-to-use user interfaces.
- allowing anybody to propose referendums.
- robust to attacks.
- aimed at gaining confidence of both technical and non-technical people.

It provides a voting system relying on 6 types of participant:

1. [citizen](citizen.md): anybody with internet access.
2. [author](author.md): (referendum author) anybody with internet access.
3. [truster](truster.md): anybody with computer science knowledge and computer network resources.
4. [station](station.md): (polling station) anybody with computer science knowledge and computer network resources.
5. [publisher](publisher.md): anybody with computer science knowledge and computer network resources.
6. [host](host.md): with anybody computer science knowledge and computer network resources.

Each participant has a pair of [private/public cryptographic keys](cryptography.md) allowing her to sign and be identified.

The system relies on 6 types of [publication](publication.md):

1. [card](card.md) (signed by a citizen)
2. [endorsement](endorsement.md) (signed by a citizen or a truster).
3. [referendum](referendum.md) (signed by an author).
4. [vote](vote.md) (signed by an anonymized citizen).
5. [voter](voter.md) (signed by a station).
6. [ballots](ballots.md) (signed by a station).

### Trusters

Trusters process publications and endorse publications and participants.
Any individual or organization can become a truster.
Trusters should establish a good reputation from others' endorsements.
Citizen will not take part in referendums which rely on trusters they dont trust.
So, trusters should develop the best trust algorithms to publish good endorsements and thus achieve a good reputation.

### Referendums

A referendum is a text aiming at changing the law in a city, state, country or the whole world.
It should contain the following elements:
- The area of application (GPS coordinates of an area, usually corresponding to a city, a state, a country or the whole world).
- Title
- Description of the law to be applied in the area.
- A question (usually do you agree with this proposal?)
- A list of possible answers (usually yes/no/abstention)
- A list of accepted trusters.
- A deadline for the publication of results.
It should be published on the internet, so that everyone can see it.

### Stations

When a citizen wants to vote, she generate a new pair of private and public key specifically for this referendum.
Then she securely sends two signed packets to the station of her choice.
The first packet contains her vote card, the referendum and the station.
The second packet contains the public key and the referendum.
The station checks that both packets are received and that the citizen is entitled to vote (area, truster endorsement).
If not, it declines the request of the citizen and publish a message saying it refused to allow this citizen to vote to this referendum.
This message is also sent back to the citizen.
Otherwise, the station signs the first packet, publishes it and sent it back to the citizen.
This way, the station announces publicly that it handles the anonymous vote of this citizen on that referendum.
The station then removes the signature from the second packet, sign it, send it back to the citizen and store it temporary.

The citizen selects an answer in the referendum, sign it with the private key and publish it.
Once the vote period is over, the station publishes in a random order all the public key it signed and stored.
Citizens should also publish the same information they have received from the station.

Citizen will freely choose stations with a good reputation to cast their votes.
The reputation of stations may be affected by obvious disfunctionnings or complains of citizens about their participation not being published (and hence their vote being likely usurpated) or their anonymity not being respected.
Therefore a good reputation system should be setup to assess the reputation of stations.

### Verifications

Anyone can verify the information published by voters, trusters, stations, etc. to detect possible frauds in the system.
For example, for each station and each referendum, the number of published public keys should match the number of published vote cards/referendum packets.
If numbers do not match, something has go wrong, the vote should not be considered secure and the reputation of the station should decrease.

![Station workflow](https://raw.githubusercontent.com/suffragio/doc/master/vote.png "Station workflow")
