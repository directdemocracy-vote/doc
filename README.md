# directdemocracy.vote

## 1 Overview

directdemocracy (short for directdemocracy.vote) aims at establishing world-wide [direct democracy](https://en.wikipedia.org/wiki/Direct_democracy) in order to bring peace, safety and prosperity to humanity, including saving the climate and the biodiversity.
The principle is that people will become citizens by proposing referendums and voting regardless of any official acknowledgement.
Vote results from a limited number of citizens could be considered as simple survey results.
They could feed debates, influence political decisions and foster more people to become citizens.
Vote results from areas where a majority of people are citizens will become significant from a democratic point of view.
This will increase the pressure on governments to respect the democratic choices expressed by their people.
Ultimately this bottom-up initiative will enforce direct democracy everywhere in the world.

directdemocracy is a voting system with the following properties:

- open to anybody with internet access (smartphone or computer).
- fully decentralized (nobody can control it).
- verifiable (check that my vote was taken into account, check that others didn't cheat).
- relying on open-source specifications and open-source software.
- providing easy-to-use user interfaces.
- allowing anybody to propose referendums.
- robust to attacks.
- aimed at gaining confidence of both technical and non-technical people.

## 2 Components

It provides a voting system relying on 4 types of participant:

1. [citizen](citizen.md): anybody with internet access.
2. [truster](truster.md): anybody with computer science knowledge and computer network resources.
3. [station](station.md): (polling station) anybody with computer science knowledge and computer network resources.
4. [publisher](publisher.md): anybody with computer science knowledge and computer network resources.

Each participant has a pair of [private/public cryptographic keys](cryptography.md) allowing her to sign and be identified.

The system relies on 7 types of [publication](publication.md):

1. [card](card.md) (signed by a citizen)
2. [endorsement](endorsement.md) (signed by a citizen or a truster).
3. [revocation](revocation.md) (signed by a citizen or a truster).
4. [referendum](referendum.md) (signed by a citizen).
5. [vote](vote.md) (signed by an anonymized citizen).
6. [voter](voter.md) (signed by a station).
7. [votes](votes.md) (signed by a station).

## 3 Workflows

### 3.1 Web of Trust

**Participants:** citizens, trusters, publishers.

**Publications:** cards, endorsements.

The web of trust aims at establishing a web of trust between citizens, with the help of endorsements and trusters.
The goal of this web of trust is to ensure that each endorsed card correspond to a unique citizen who can take part in a vote.

1. Each citizen should publish a card with their personal information.
2. Each citizen should endorse several other citizens they personally know to create a web of endorsements.
3. Trusters should use the resulting web of endorsements to endorse all the cards corresponding to a unique citizen.

### 3.2 Referendum Setup

**Participants:** citizens, trusters, publishers.

**Publications**: referendums.

### 3.3 Vote Process

**Participants:** citizens, stations, trusters.

**Publications:** vote, voter, votes.

<img src="https://raw.githubusercontent.com/directdemocracy-vote/doc/master/vote.png" alt="Station workflow" width="561"/>

### 3.4 Verifications

**Participants:** publishers, trusters.

**Publications:** N/A.

Anyone can verify the information published by voters, trusters, stations, etc. to detect possible frauds in the system.
For example, for each station and each referendum, the number of published public keys should match the number of published vote cards/referendum packets.
If numbers do not match, something has go wrong, the vote should not be considered secure and the reputation of the station should decrease.
