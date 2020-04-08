# Features and Limitations

A perfect voting system doesn't exists.
The system we propose has a number of limitations.
However, such limitations should not affect the democratic process.

# Voting

This section describe the full voting process.

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

`A` creates a cancelled registration structure which contains the public key of `R`, `S` and `A` and sign it with `A`: `-RSa`.
The cancelled registration publication date (*published*) is set to the current date.
`A` publishes `-RSa` and proceed to **1.1 Registration**, likely with a different polling station.

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
Each station `S` check that all the citizens who registered with them in `RSas` did not register with another station.
If a citizen `A` registered with another station, e.g., another `RSas` is found with a different `S`, then proceed to **2.3 Ballot Rejection**.
Once `S` checked all its citizen registrations, it publishes `RSs` to mean it's done with registration checks.
This should happen within a short delay after *deadline* as observers will start counting votes quickly.
It is recommended that `S` clears its database to keep no record linking citizens `A` to ballots `B` for `R` in case of any possible future attack on its database.

### 2.3 Ballot Rejection

`S` publishes the original `RSba` it received from `A` to cancel her registration, ballot and vote before the upcoming counting.

## 3 Observers & Trustees

After a short delay after the *deadline* for `R` has passed, the observers, including trustees can start checking the results.

### 3.1 Matching Ballots and Votes

For each vote `Vb`, check that there is a single corresponding `RSbs`.
If there is no corresponding `RSbs`, `Vb` is disregarded.
If there are several corresponding `RSbs` (F0), `Vb` is disregarded and the oldest corresponding `RSas` is determined ;
all the other stations get invalidated.

### 3.2 Uniqueness

Check that each citizen voted only once, e.g., there is no several `RSas` with the same `R` and same `A`.
If a citizen voted several times (F1), the oldest `RSas` is determined, based on the *published* date.
If it is multiple, e.g., several `RSas` having the same oldest *published* date, (F2).

For each `S`, count the number of `RSas`, `RSbs` and `RSbas`.
if (n(`RSas`) != n(`RSbs`) - n(`RSbas`)), (F4) `S` get invalidated.

### 3.3 Invalidated Stations

When a station `S` did a bad job, it gets invalidated:
All votes related to `S` are removed from the count and trustees will likely decrease the reputation of `S`.

# Weaknesses

This section explores the cheating possibilities for each participant.

## Malicious Citizen

## Malicious Station
