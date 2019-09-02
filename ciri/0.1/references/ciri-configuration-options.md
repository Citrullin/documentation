# cIRI configuration options

**This table contains the configuration options for the cIRI.**

You can choose to configure cIRI by specifying the configuration options in the following ways:
* As flags in the command line
* As parameters in the conf.yaml (cIRI configuration file)

### Command line flags

| **Configuration options** |   **Description**| **Accepted values** | **Default values**|**Notes** |
| :------------------------ | :--------------- | :--------- | :--------| :------------|
|<a name="--config"></a>`--config`| Path to the configuration file.| string  | | --config ciri/conf.yml |
|<a name="--help"></a>`--help`| Displays the usage.|  | |  |
|<a name="--log-level"></a>`--log-level`| Valid log levels: "debug", "info", "notice", "warning", "error", "critical", "alert" and "emergency".| string  | | -l debug |
|<a name="--spent-addresses-db-path"></a>`--spent-addresses-db-path`| Path to the spent addresses database file.| string  | | --spent-addresses-db-path ciri/db/spent-addresses-mainnet.db |
|<a name="--tangle-db-path"></a>`--tangle-db-path`| Path to the tangle database file.| string  | | --tangle-db-path ciri/db/tangle-mainnet.db |
|<a name="--tangle-db-revalidate"></a>`--tangle-db-revalidate`| Reloads milestones, state of the ledger and transactions metadata from the tangle database.| bool  | | --tangle-db-revalidate false |
|<a name="--auto-tethering-enabled"></a>`--auto-tethering-enabled`| Whether to accept new connections from unknown neighbors (which are not defined in the config and were not added via addNeighbors).| bool  | | --auto-tethering-enabled false |
|<a name="--max-neighbors"></a>`--max-neighbors`| The maximum number of neighbors allowed to be connected.| number  | | --max-neighbors 5 |
|<a name="--mwm"></a>`--mwm`| Number of trailing ternary 0s that must appear at the end of a transaction hash. Difficulty can be described as 3^mwm.| number  | | --mwm 14 |
|<a name="--neighboring-address"></a>`--neighboring-address`| The address to bind the TCP server socket to.| string  | | --neighboring-address "0.0.0.0" |
|<a name="--neighboring-port"></a>`--neighboring-port`| The TCP receiver port.| number  | | --neighboring-port 1500 |
|<a name="--neighbors"></a>`--neighbors`| URIs of neighbouring nodes, separated by a space.| string  | | -n "tcp://148.148.148.148:14265 tcp://[2001:db8:a0b:12f0::1]:14265" |
|<a name="--p-send-milestone"></a>`--p-send-milestone`| Probability of sending a milestone transaction when the node looks for a random transaction to send to a neighbor. Value must be in [0,1].| float  | | --p-send-milestone 0.02 |
|<a name="--recent-seen-bytes-cache-size"></a>`--recent-seen-bytes-cache-size`| The number of entries to keep in the network cache.| number  | | --recent-seen-bytes-cache-size 1500 |
|<a name="--reconnect-attempt-interval"></a>`--reconnect-attempt-interval`| The interval (in seconds) at which to reconnect to neighbors.| number  | | --reconnect-attempt-interval 60 |
|<a name="--requester-queue-size"></a>`--requester-queue-size`| Size of the transaction requester queue.| number  | | --requester-queue-size 10000 |
|<a name="--tips-cache-size"></a>`--tips-cache-size`| Size of the tips cache. Also bounds the number of tips returned by getTips API call.| number  | | --tips-cache-size 5000 |
|<a name="--http-port"></a>`--http-port`| HTTP API listen port.| number  | | --http-port 14265 |
|<a name="--max-find-transactions"></a>`--max-find-transactions`| The maximal number of transactions that may be returned by the 'findTransactions' API call. If the number of transactions found exceeds this number an error will be returned| number  | | --max-find-transactions 100000 |
|<a name="--max-get-trytes"></a>`--max-get-trytes`| Maximum number of transactions that will be returned by the 'getTrytes' API call.| number  | | --max-get-trytes 10000 |
|<a name="--remote-limit-api"></a>`--remote-limit-api`| Commands that should be ignored by API.| string  | | --remote-limit-api "attachToTangle, addNeighbors" |
|<a name="--alpha"></a>`--alpha`| Randomness of the tip selection. Value must be in [0, inf] where 0 is most random and inf is most deterministic.| float  | | --alpha 0.001 |
|<a name="--below-max-depth"></a>`--below-max-depth`| Maximum number of unconfirmed transactions that may be analysed to find the latest referenced milestone by the currently visited transaction during the random walk.| number  | | --below-max-depth 20000 |
|<a name="--coordinator-address"></a>`--coordinator-address`| The address of the coordinator.| string  | | --coordinator-address "EQS...VD9" |
|<a name="--coordinator-depth"></a>`--coordinator-depth`| The depth of the Merkle tree which in turn determines the number of leaves (private keys) that the coordinator can use to sign a message.| number  | | --coordinator-depth 23 |
|<a name="--coordinator-security-level"></a>`--coordinator-security-level`| The security level used in coordinator signatures.| number  | | --coordinator-security-level 2 |
|<a name="--coordinator-signature-type"></a>`--coordinator-signature-type`| The signature type used in coordinator signatures. Valid types: "CURL_P27", "CURL_P81" and "KERL".| string  | | --coordinator-signature-type KERL |
|<a name="--last-milestone"></a>`--last-milestone`| The index of the last milestone issued by the corrdinator before the last snapshot.| number  | | --last-milestone 1050000 |
|<a name="--max-depth"></a>`--max-depth`| Limits how many milestones behind the current one the random walk can start.| number  | | --max-depth 15 |
|<a name="--snapshot-file"></a>`--snapshot-file`| Path to the file that contains the state of the ledger at the last snapshot.| string  | | --snapshot-file external/snapshot_mainnet/file/snapshot.txt |
|<a name="--snapshot-signature-depth"></a>`--snapshot-signature-depth`| Depth of the snapshot signature.| number  | | --snapshot-signature-depth 6 |
|<a name="--snapshot-signature-file"></a>`--snapshot-signature-file`| Path to the file that contains a signature for the snapshot file.| string  | | --snapshot-signature-file external/snapshot_sig_mainnet/file/snapshot.sig |
|<a name="--snapshot-signature-index"></a>`--snapshot-signature-index`| Index of the snapshot signature.| number  | | --snapshot-signature-index 12 |
|<a name="--snapshot-signature-pubkey"></a>`--snapshot-signature-pubkey`| Public key of the snapshot signature.| trytes  | | --snapshot-signature-pubkey "TTX...YAC" |
|<a name="--snapshot-signature-skip-validation"></a>`--snapshot-signature-skip-validation`| Skip validation of snapshot signature. Must be "true" or "false".| bool  | | --snapshot-signature-skip-validation false |
|<a name="--snapshot-timestamp"></a>`--snapshot-timestamp`| Epoch time of the last snapshot.| number  | | --snapshot-timestamp 1554904800 |
|<a name="--spent-addresses-files"></a>`--spent-addresses-files`| List of whitespace separated files that contains spent addresses to be merged into the database.| string  | | --spent-addresses-files "file0 file1" |


### cIRI Configuration file
| **Configuration options** |   **Description**| **Accepted values** | **Default values**|**Notes** |
| :------------------------ | :--------------- | :--------- | :--------| :------------|
|<a name="log-level"></a>`log-level`| Valid log levels: "debug", "info", "notice", "warning", "error", "critical", "alert" and "emergency".| string  | | -l debug |
|<a name="spent-addresses-db-path"></a>`spent-addresses-db-path`| Path to the spent addresses database file.| string  | | spent-addresses-db-path ciri/db/spent-addresses-mainnet.db |
|<a name="tangle-db-path"></a>`tangle-db-path`| Path to the tangle database file.| string  | | tangle-db-path ciri/db/tangle-mainnet.db |
|<a name="tangle-db-revalidate"></a>`tangle-db-revalidate`| Reloads milestones, state of the ledger and transactions metadata from the tangle database.| bool  | | tangle-db-revalidate false |
|<a name="auto-tethering-enabled"></a>`auto-tethering-enabled`| Whether to accept new connections from unknown neighbors (which are not defined in the config and were not added via addNeighbors).| bool  | | auto-tethering-enabled false |
|<a name="max-neighbors"></a>`max-neighbors`| The maximum number of neighbors allowed to be connected.| number  | | max-neighbors 5 |
|<a name="mwm"></a>`mwm`| Number of trailing ternary 0s that must appear at the end of a transaction hash. Difficulty can be described as 3^mwm.| number  | | mwm 14 |
|<a name="neighboring-address"></a>`neighboring-address`| The address to bind the TCP server socket to.| string  | | neighboring-address "0.0.0.0" |
|<a name="neighboring-port"></a>`neighboring-port`| The TCP receiver port.| number  | | neighboring-port 1500 |
|<a name="neighbors"></a>`neighbors`| URIs of neighbouring nodes, separated by a space.| string  | | -n "tcp://148.148.148.148:14265 tcp://[2001:db8:a0b:12f0::1]:14265" |
|<a name="p-send-milestone"></a>`p-send-milestone`| Probability of sending a milestone transaction when the node looks for a random transaction to send to a neighbor. Value must be in [0,1].| float  | | p-send-milestone 0.02 |
|<a name="recent-seen-bytes-cache-size"></a>`recent-seen-bytes-cache-size`| The number of entries to keep in the network cache.| number  | | recent-seen-bytes-cache-size 1500 |
|<a name="reconnect-attempt-interval"></a>`reconnect-attempt-interval`| The interval (in seconds) at which to reconnect to neighbors.| number  | | reconnect-attempt-interval 60 |
|<a name="requester-queue-size"></a>`requester-queue-size`| Size of the transaction requester queue.| number  | | requester-queue-size 10000 |
|<a name="tips-cache-size"></a>`tips-cache-size`| Size of the tips cache. Also bounds the number of tips returned by getTips API call.| number  | | tips-cache-size 5000 |
|<a name="http-port"></a>`http-port`| HTTP API listen port.| number  | | http-port 14265 |
|<a name="max-find-transactions"></a>`max-find-transactions`| The maximal number of transactions that may be returned by the 'findTransactions' API call. If the number of transactions found exceeds this number an error will be returned| number  | | max-find-transactions 100000 |
|<a name="max-get-trytes"></a>`max-get-trytes`| Maximum number of transactions that will be returned by the 'getTrytes' API call.| number  | | max-get-trytes 10000 |
|<a name="remote-limit-api"></a>`remote-limit-api`| Commands that should be ignored by API.| string  | | remote-limit-api "attachToTangle, addNeighbors" |
|<a name="alpha"></a>`alpha`| Randomness of the tip selection. Value must be in [0, inf] where 0 is most random and inf is most deterministic.| float  | | alpha 0.001 |
|<a name="below-max-depth"></a>`below-max-depth`| Maximum number of unconfirmed transactions that may be analysed to find the latest referenced milestone by the currently visited transaction during the random walk.| number  | | below-max-depth 20000 |
|<a name="coordinator-address"></a>`coordinator-address`| The address of the coordinator.| string  | | coordinator-address "EQS...VD9" |
|<a name="coordinator-depth"></a>`coordinator-depth`| The depth of the Merkle tree which in turn determines the number of leaves (private keys) that the coordinator can use to sign a message.| number  | | coordinator-depth 23 |
|<a name="coordinator-security-level"></a>`coordinator-security-level`| The security level used in coordinator signatures.| number  | | coordinator-security-level 2 |
|<a name="coordinator-signature-type"></a>`coordinator-signature-type`| The signature type used in coordinator signatures. Valid types: "CURL_P27", "CURL_P81" and "KERL".| string  | | coordinator-signature-type KERL |
|<a name="last-milestone"></a>`last-milestone`| The index of the last milestone issued by the corrdinator before the last snapshot.| number  | | last-milestone 1050000 |
|<a name="max-depth"></a>`max-depth`| Limits how many milestones behind the current one the random walk can start.| number  | | max-depth 15 |
|<a name="snapshot-file"></a>`snapshot-file`| Path to the file that contains the state of the ledger at the last snapshot.| string  | | snapshot-file external/snapshot_mainnet/file/snapshot.txt |
|<a name="snapshot-signature-depth"></a>`snapshot-signature-depth`| Depth of the snapshot signature.| number  | | snapshot-signature-depth 6 |
|<a name="snapshot-signature-file"></a>`snapshot-signature-file`| Path to the file that contains a signature for the snapshot file.| string  | | snapshot-signature-file external/snapshot_sig_mainnet/file/snapshot.sig |
|<a name="snapshot-signature-index"></a>`snapshot-signature-index`| Index of the snapshot signature.| number  | | snapshot-signature-index 12 |
|<a name="snapshot-signature-pubkey"></a>`snapshot-signature-pubkey`| Public key of the snapshot signature.| trytes  | | snapshot-signature-pubkey "TTX...YAC" |
|<a name="snapshot-signature-skip-validation"></a>`snapshot-signature-skip-validation`| Skip validation of snapshot signature. Must be "true" or "false".| bool  | | snapshot-signature-skip-validation false |
|<a name="snapshot-timestamp"></a>`snapshot-timestamp`| Epoch time of the last snapshot.| number  | | snapshot-timestamp 1554904800 |
|<a name="spent-addresses-files"></a>`spent-addresses-files`| List of whitespace separated files that contains spent addresses to be merged into the database.| string  | | spent-addresses-files "file0 file1" |

