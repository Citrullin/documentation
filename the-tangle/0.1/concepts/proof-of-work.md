# Proof of work

**Proof of work (PoW) is the answer to a mathematical problem that's difficult to calculate, but easy to verify. In IOTA, proof of work protects the network from spam transactions.**

PoW is calculated using trial and error, therefore it requires the use of computational power.

Originally, PoW was introduced as a concept to reduce large amounts of email spam. This concept is known as [hashcash](https://en.wikipedia.org/wiki/Hashcash), and is a method of preventing email spam by requiring a proof of work for the contents of every email.

## Proof of work in IOTA

Similar to hashcash, each IOTA transaction must include a PoW before it can be validated. This PoW provides spam protection for an IOTA network by increasing the time and computational power it takes to create a valid transaction.

If an IRI node receives a transaction without the PoW, that transaction is ignored to reduce the effect that spam transactions have on the network.

PoW can be done by clients or it can be outsourced to an IRI node (known as remote proof of work) by calling the [`attachToTangle` endpoint](root://iri/0.1/references/api-reference.md#attachToTangle).

Clients may want to use remote PoW if the device they're using to create transactions doesn't have the necessary computational power to calculate PoW in a reasonable amount of time.

### Proof of work for transactions

To calculate the PoW for a transaction, the following contents of the transaction are converted from trytes to trits, then those trits are hashed:

* **Bundle hash:** Hash that is calculated using the address, obsolete tag, timestamp, value, and index of all transactions in the bundle
* **Signature:** Signature of the transaction (if it debits IOTA tokens)
* **Trunk transaction and branch transaction:** Two previous transactions that the transaction references and approves

If the hash ends in the correct amount of 0s ([minimum weight magnitude](#minimum-weight-magnitude)), it's considered valid.

If the hash doesn't end in the correct amount of 0s, the value of the transaction's `nonce` field is incremented and the hash is hashed again.

This process continues until a hash is found that ends in the correct amount of 0s.

The `nonce` field of a transaction contains a string of 27 trytes that IRI nodes use to validate the PoW, for example:

```javascript
{
...
nonce: "POWSRVIO9GW99999FMGEGVMMMMM"
...
}

```

Because the hash is created using the contents of the transaction, if any of the contents change, the hash will change and make the proof of work invalid.

**Note:** The function that calculates PoW is called the [PearlDiver](https://github.com/iotaledger/iri/blob/fcf2d105851ee891b093e2857592fa05258ec5be/src/main/java/com/iota/iri/crypto/PearlDiver.java).

### Minimum weight magnitude

The minimum weight magnitude (MWM) is a variable that defines the number of 0s that a transaction hash must end in.

Although the MWM is set in the node software (IRI) of each IRI node in an IOTA network, clients and IRI nodes can choose to change the MWM. However, if each IRI node used a different MWM, transactions would be valid only for those with the same MWM. This situation would decrease the rate of transaction confirmations.

**Note:** Every increment of the MWM increases the difficulty of the PoW by 3 times.
