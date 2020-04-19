# directdemocracy.vote

## 1 Overview

directdemocracy.vote (directdemocracy) aims at establishing world-wide [direct democracy](https://en.wikipedia.org/wiki/Direct_democracy) in order to bring peace, safety and prosperity to humanity, including saving the climate and the biodiversity.
The principle is that people become citizens by proposing referendums and voting regardless of any official acknowledgement.
Vote results from a limited number of citizens should be considered as simple survey results.
They could feed debates, influence political decisions and foster more people to become citizens.
Vote results from areas where a majority of people are citizens will become significant from a democratic point of view.
This will increase the pressure on governments to respect the democratic choices expressed by their people.
Ultimately this bottom-up initiative will enforce direct democracy everywhere in the world.

directdemocracy is a voting system with the following properties:

- open to anybody with internet access (smartphone or computer).
- fully decentralized (nobody controls it).
- verifiable (check that my vote was taken into account, check that others didn't cheat).
- relying on open-source specifications and open-source software.
- providing easy-to-use user interfaces.
- allowing anybody to propose referendums.
- robust to attacks.
- aimed at gaining confidence of both technical and non-technical people.

## 2 Components

The voting system relies on 3 types of organizations:

1. [trustee](trustee.md): webservice granting endorsements to citizens and other organizations.
2. [station](station.md): (polling station) webservice for the anonymization of votes.
3. [publisher](publisher.md): webservice for storing, displaying [publications](publication.md).

Citizens and organizations own a pair of [private/public cryptographic keys](cryptography.md) allowing them to sign and be identified uniquely.

The system relies on 7 types of [publication](publication.md):

1. [citizen](citizen.md): self-signed.
2. [organization](organization.md): self-signed.
3. [endorsement](endorsement.md): signed by a citizen or a trustee.
4. [area](area.md): geographic area for a referendum.
5. [referendum](referendum.md): self-signed.
6. [ballot](ballot.md): self-signed and possible also signed by a station.
7. [registration](registration.md): signed by a citizen and a station.

## 3 Workflows

### 3.1 Web of Trust

**Organizations:** trustees, publishers.

**Publications:** citizen, endorsement.

The web of trust aims at establishing a [web of trust](https://en.wikipedia.org/wiki/Web_of_trust) between [citizens](citizen.md), with the help of [endorsements](endorsement.md) and [trustees](trustee.md).
The goal of this web of trust is to ensure that each endorsed card correspond to a unique citizen who can take part in a vote.

1. Each citizen should publish a citizen card with her personal information.
2. Each citizen should endorse several other citizens they personally know to create a web of endorsements.
3. Trustees should use the resulting web of endorsements to endorse all the cards corresponding to a unique citizen.

Similarly, citizens and trustees may endorse stations, publishers and trustees.

### 3.2 Referendum Setup

**Organizations:** publishers.

**Publications**: referendums.

### 3.3 Voting Process

**Organizations:** stations, publishers.

**Publications:** registration.

The voting process is described in details [here](voting.md). It is summarized on the following figure:

<img src="https://raw.githubusercontent.com/directdemocracy-vote/doc/master/vote.png" alt="Voting Process" width="561"/>

### 3.4 Verification and Counting

**Organizations:** publishers.

**Publications:** ballot, registration, vote.

Anyone, including [publishers](publisher.md), can verify the information published by anonymized citizens, trustees, stations, etc. to detect possible frauds in the system.
For example, for each [station](station.md) and each [referendum](referendum.nd), the number of published [registrations](registration.md) should match the number of published [ballots](ballot.md).
Also, the published [ballots](ballot.md) should match the published [votes](vote.md).
More details about verification and counting are provided [here](voting.md).
