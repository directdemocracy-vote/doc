# Suffragio

## Overview

Suffragio aims at establishing world-wide [direct democracy](https://en.wikipedia.org/wiki/Direct_democracy) in order to bring peace, safety and prosperity to humananity, including saving the climate and the biodiversity.
The principle is that people will become citizens by proposing referundums and voting regardless of any official acknowledgement.
Vote results from a limited number of citizens could be considered as simple survey results.
They could feed debates, influence political decisions and incitate more people to become citizens.
Vote results from areas where a majority of people are citizens will become significant from a democratic point of view.
This will increase the pressure on governments to respect the democratic choices expressed by their people.
Ultimately this bottom-up initiative will enforce direct democracy everywhere in the world.

Suffragio is a voting system with the following properties:

- open to anybody with internet access (smartphone or computer).
- fully decentralized (nobody can control it).
- verifyable (check that my vote was taken into account, check that others didn't cheat).
- relying on open-source specifications and open-source software.
- providing easy-to-use user interfaces.
- allowing anybody to propose referendums.
- robust to attacks.
- aimed at gaining confidence of both technical and non-technical people.

## Components

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

## Workflow

<img src="https://raw.githubusercontent.com/suffragio/doc/master/vote.png" alt="Station workflow" width="200"/>

## Verifications

Anyone can verify the information published by voters, trusters, stations, etc. to detect possible frauds in the system.
For example, for each station and each referendum, the number of published public keys should match the number of published vote cards/referendum packets.
If numbers do not match, something has go wrong, the vote should not be considered secure and the reputation of the station should decrease.
