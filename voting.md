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

# Voting

This section describe the full voting process in details.
It is summarized on the following figure:

<img src="https://raw.githubusercontent.com/directdemocracy-vote/doc/master/vote.png" alt="Voting Process" width="561"/>

## 1 Citizens

### 1.1 Registration

The citizen `A` choose a referendum `R` and a polling station `S` she will use for that vote.
`R` includes a reference to a trustee `T` which represents the authority for `R`.
`A` creates a new pair of cryptographic keys `B` for her ballot.
`A` creates a ballot structure containing the public keys of `R`, `S`, `B` and `A` and signs it with her `B` key and `A` key: `RSba`.
The ballot also contains a publication date (*published*) set to the *deadline* of `R`.
That means, it won't be made public before this date.
`A` creates a registration structure, that is containing the public keys of `R`, `S` and `A` and sign it with her `A` key: `RSa`.
The publication date (*published*) of the registration is set to the current date, which means it can be published now.
`A` sends `RSba + RSa` to `S` and waits for an answer.
If `S` takes too long to answer or answers anything else than `RSbs + RSas`, proceed to **1.2 Registration Cancellation**.
Check the answer of `S`: check my `A` and `B` public keys and check the 4 signatures.
If any check fails, proceed to **1.2 Registration Cancellation**.
Else proceed to **1.3 Vote**.

### 1.2 Registration Cancellation

`A` publishes the `RSba` structure it sent to `S` earlier and proceed to **1.1 Registration**, likely with a different polling station.

### 1.3 Vote

`A` creates a vote structure containing her answer `V` to `R`, her `B` key and signs it with her `B` key: `Vb`.
The vote publication date (*published*) is set to the *deadline* of `R`.
That means, it won't be made public before this date.
`A` publishes `Vb`.

## 2 Stations

### 2.1 Registration Desk

If `S` receives no `RSba + RSa` message from `A` until the *deadline* of `R` is reached, proceed to **2.2 Registrations Check**.
`S` receives `RSba + RSa`. It checks that `S` correspond to itself, that `R` exists and checks the 3 signatures.
`S` also checks that `A` did not already registered with it.
Then, `S` checks the available publications to determine if `A` is allowed to vote to `R`:
First, `S` checks if there is a publication signed by `T` and endorsing `A`.
Then, `S` checks from publications signed by `T` if the *latitude* and *longitude* of `A` lies in the *area* of `R`.
If any check fails, `S` replies "no" to `A`, with possibly some explanation why it refused her and proceed to **2.1 Registration Desk**.
Otherwise `S` removes the key and signature of `A` from the `RSba` ballot, signs it so that it is now `RSbs`.
It also sign the `RSa` registration so that it becomes `RSas`.
It publishes `RSas` and `RSbs` (the later will be public at the *deadline* of `R`).
It send back `RSbs + RSas` to to `A` and proceed to **2.1 Registration Desk** to possibly handle other citizen registrations.

### 2.2 Registrations Check

At this point, the *deadline* of `R` is reached.
Each station `S` check that all the citizens who registered with them with a valid `RSas` did not register with another station.
A valid `RSas` is a `RSas` which is not cancelled by a corresponding `RSba` publication.
If a citizen `A` registered with another station, e.g., another `RSas` is found with a different `S`, then proceed to **2.3 Ballot Rejection**.
`S` should check all its citizen registrations this way and reject all wrong ballots (if any).
This should happen within a short delay after *deadline* as observers will start counting votes quickly.
It is recommended that `S` clears its database to keep no record linking citizens `A` to ballots `B` for `R` in case of any possible future attack on its database.

### 2.3 Ballot Rejection

`S` publishes the original `RSba` it received from `A` to cancel her registration, ballot and vote before the upcoming counting.

## 3 Observers & Trustees

After the *deadline* for `R` has passed, the observers, including trustees, can start checking the results.
It may be possible that some stations didn't yet finished their registrations check (see **2.2 Registrations Check**) or will never finish it.
An unfinished registrations check will cause the votes of the corresponding station not being counted until the registrations check is complete.
If a station takes too long (or forever) to complete its registrations check, its reputation will decrease accordingly.

### 3.1 List Valid Stations

For each station, the observers check that the registrations check is complete (see **2.2 Registrations Check**).
The registrations check is considered complete if all the `RSas` of this station that have another `RSas` (with the same `R` and `S` but with a different `S`) are cancelled with a `RSba` (with the same `R`, `S` and `A`).
If the registrations check is complete, add the station in the list of valid stations.

For each valid station in the list, we count all the `RSas` registrations which are valid.
A `RSas` registration is valid if it is not cancelled by a corresponding `RSba`.
Similarly, we count all the `RSbs` ballots which are valid.
A `RSbs` is valid is it is not cancelled by a corresponding `RSba`.
If the two counts do are not equal, the station is withdrawn from the list of valid stations (and is likely to get a bad reputation).

### 3.2 Votes Counting

For each valid station in the list we get all the `RSbs` and get the corresponding `Vb` if any.
If several `Vb` are found they are all disregarded.
If we find another `RSbs` with the same `B` in another valid station, the corresponding `Vb` is disregarded.
If not disregarded, the `Vb` is added to the list of valid votes and its *answer* is counted.

Observers may iterate the whole process again by looping to **3.1 and 3.2** for a while to get an increasingly precise result for the vote (while the polling stations are still proceeding with registrations checks).

After a while, the results should get stable and one can consider the counting is over.
Results can be published by observers on their web sites.
