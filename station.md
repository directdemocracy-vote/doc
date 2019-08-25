# Station

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
