# Features and Limitations of the Voting System

A perfect voting system doesn't exists.
The system we propose has a number of limitations explained in this section.
However, such limitations should not affect too much the democratic process.

## Malicious Polling stations

A malicious polling station may misbehave, but this will be visible by all.
If that happens, all the votes handled by this stations will be discarded.
All the honest citizens who voted through this polling station will loose their vote.
And the polling station will likely get a bad reputation from most of the trustees.
This will lower the likelihood it will be used by citizens in upcoming votes.
A polling station handling a large number of votes is however unlikely to misbehave.
This is because to have a large number of votes, a polling station should have a high reputation.
And a high reputation is only possible if the station never misbehaved.
If it misbehaves once, it will immediately loose its reputation and almost all its voters for the upcoming votes.

## Malicious Citizens

A malicious citizen can vote several times to the same referendum, but her votes won't be counted.
She cannot either cause a misbehavior in a honest polling station.
So, she cannot force the discard of other's votes.
However, her suspicious activity is likely to cause her a bad reputation from trustees and thus to prevent her from voting in upcoming votes.

## Malicious Observers and Trustees

Malicious observers and trustees will quickly get a bad reputation from the community of trustees.
With a bad reputation, they will be disregarded by most people.
A referendum referring to a trustee with a bad reputation will be unlikely to attract voters, hence its results will not be relevant.
An observer displaying a wrong result for a vote will be quickly spotted by trustees and its reputation will decrease, thus rendering it irrelevant.

## Vote Anonymity

It is not possible to find out what a citizen voted from the publications of the system unless the citizen decides to cancel her vote or her station decides to reject it.
In the later case, the station will get a bad reputation if disclosing the citizen vote is not justified by a publicly verifiable cheating attempt of the citizen.

A station may be able to find out the relationship between a voter and her actual vote.
It may publish this information but without any proof, which has no value and would decrease its reputation if it signs the publication.
It also may publish this information with a proof, but that would involve revealing publicly its https private key.
In such a case, its reputation will decrease.
Finally, it may communicate this information and proof to a third party.
That cannot be detected publicly.
But that means it would share its private https key to the third party.
Hence we may consider the station and third party are actually the same entity (sharing the https key of the station).
This is the main limitation of the directdemocracy system: citizen should trust the station they choose, based on its reputation.


# Voting

This section describe the full voting process in details.
It is summarized on the following figure:

<img src="https://raw.githubusercontent.com/directdemocracy-vote/doc/master/vote.png" alt="Voting Process" width="561"/>

## 1 Citizens

### 1.1 Registration

The citizen `A` choose a referendum `R` and a polling station `S` she will use for that vote.
`R` includes a reference to a trustee `T` which represents the authority for `R`.
`A` creates a new pair of cryptographic keys `B` for her ballot.
`A` creates a ballot structure containing the public keys of `R`, `S` and `B` and signs it with her `B` key: `RSBb`.
The ballot also contains a publication date (*published*) set to `F`, which is the *deadline* of `R`.
That means, it won't be made public before this date.
`A` creates a registration structure, that is containing the public keys of `R`, `S` and `A` and sign it with her `A` key: `RSAa`.
The publication date (*published*) of the registration is set to the current date, which means it can be published now.
`A` sends `RSBb + RSAa` to `S` and waits for an answer.
If `S` takes too long to answer or answers anything else than `RSBbs + RSAas`, proceed to **1.2 Cancellation**.
Check the answer of `S`: `R`, `S`, `B` and `A` public keys and check the 4 signatures.
If any check fails, proceed to **1.2 Cancellation**.
Else proceed to **1.3 Vote**.

### 1.2 Cancellation

`A` publishes a cancellation signed by her `A` and `B` keys: `ABab` and proceed to **1.1 Registration**, likely with a different polling station. This cancels any `RSBbs` and `RSAas` possibly published by `S`.

### 1.3 Vote

`A` creates a vote structure containing her answer `V` to `R`, her `B` key and signs it with her `B` key: `VBb`.
The vote publication date (*published*) is set to `F`.
That means, it won't be made public before this date.
After some random time but before `F`, `A` publishes `VBb`.

## 2 Stations

### 2.1 Registration Desk

If `S` receives no `RSBb + RSAa` message from `A` until the *deadline* of `R` is reached, proceed to **2.2 Registrations Check**.
`S` receives `RSBb + RSAa`. It checks that `S` corresponds to itself, that `R` exists and checks the 2 signatures.
`S` also checks that `A` did not already registered with it.
Then, `S` checks the available publications to determine if `A` is allowed to vote to `R`:
First, `S` checks if there is a valid publication signed by `T` and endorsing `A`.
Then, `S` checks from publications signed by `T` if the *latitude* and *longitude* of `A` lies in the *area* of `R`.
If any check fails, `S` replies "no" to `A`, with possibly some explanation why it refused her and proceed to **2.1 Registration Desk**.
Otherwise `S`, signs both structures so that it is now `RSBbs` and `RSAas`.
It publishes `RSAas` and will publish `RSBbs` just before `F`.
It sends back `RSBbs + RSAas` to `A` and proceed to **2.1 Registration Desk** to possibly handle other citizen registrations.

### 2.2 Registrations Check

At this point, `F` is reached.
Each station `S` checks from the publications that all the citizens who registered with them with a valid `RSAas` did not register in another station with a corresponding valid `RSAas`.
A valid `RSAas` is a `RSAas` publication which is not cancelled by a corresponding `ABba` publication.
If a citizen `A` registered with another station, e.g., another `RSAas` is found with a different `S` and no corresponding `ABba`, then proceed to **2.3 Rejection**.
`S` should check all its citizen registrations this way and reject all wrong ballots (if any).
This should happen within a short delay after *deadline* as observers will start counting votes quickly.
Once done, it is recommended that `S` clears its database to keep no record linking citizens `A` to ballots `B` for `R`.
This should prevent the possible revelation of citizens' votes in case of a later malicious intrusion in the database.
Such an event would obviously compromise the reputation of the `S`.

### 2.3 Rejection

`S` publishes the original `RSBb + RSAa` it received from `A` and signs it: `(RSBb + RSAa)s`.
This cancels the corresponding registration, ballot and vote before the upcoming counting.

## 3 Observers & Trustees

After the *deadline* for `R` has passed, the observers, including trustees, can start checking the results.
It may be possible that some stations didn't yet finished their registrations check (see **2.2 Registrations Check**) or will never finish it.
An unfinished registrations check will cause the votes of the corresponding station not being counted until the registrations check is complete.
If a station takes too long (or forever) to complete its registrations check, its reputation will decrease accordingly.

### 3.1 List Eligible Citizens

List all the citizens endorsed by the referendum trustee and matching the geographic area of the referendum.
They constitute the electoral corpus for the referendum.

### 3.2 List Valid Stations

Create a list of all the stations which have published the registration of at least one eligible citizen.
For each station, the observers check that the registrations check is complete (see **2.2 Registrations Check**).
The registrations check is considered complete if all the `RSAas` of this station that have another `RSAas` (with the same `R` and `S` but with a different `S`) are cancelled either with a `ABab` or a `(RSBb + RSAa)s` publication (with the same `R`, `S` and `A`).
If the registrations check is complete, add the station in the list of valid stations.

For each valid station in the list, we count all the `RSAas` registrations which are valid.
A `RSAas` registration is valid if it is not cancelled by a corresponding `ABab`.
If a corresponding `(RSBb + RSAa)s` is found at this point, this is an abusing behavior of `S` and the reputation of `S` will decrease.
Similarly, we count all the `RSBbs` ballots which are valid.
A `RSBbs` is valid is it is not cancelled by a corresponding `ABab`.
Again, if a corresponding `(RSBb + RSAa)s` is found at this point, this is an abusing behavior of `S` and the reputation of `S` will decrease.
If the two counts do are not equal, the station is withdrawn from the list of valid stations and will get a bad reputation.

### 3.3 Votes Counting

For each valid station in the list we get all the `RSBbs` and get the corresponding `VBb` if any.
If several `VBb` are found they are all disregarded.
If we find another `RSBbs` with the same `B` in another valid station, the corresponding `VBb` is disregarded.
If not disregarded, the `VBb` is added to the list of valid votes and its *answer* is counted.

Observers may iterate the whole process again by looping to **3.2** and **3.3** for a while to get an increasingly precise result for the vote (while the polling stations are still proceeding with registrations checks).

After a while, the results should get stable and one can consider the counting is over.
Results can be published by observers on their web sites.
