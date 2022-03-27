
# Goal

Erigon2 is the modification of Erigon1 (currently available) aimed primarily at solving two problems described below, and, secondarily, at
resolving any issues that arise from solving the primary problems.

## Snapshot sync (boostrapping)
First primary problem is the Erigon's inability to perform snapshot sync, which is bootstrapping the node without having to replay all
historical transactions from the Genesis. Solving this does not simply improve user experience, but also makes it easier for the
developers of Erigon to support large blockchains. Without snapshot sync, testing any potentially disruptive changes requires full
replay since Genesis. This becomes more impractical as the supported blockchain grow. With snapshot sync, we have a convention that
testing is only performed for the blocks above certain height, and all blocks below that have pre-computed history available for
download as snapshots.

## Granularity of history
In Erigon1, history of the blockchain state, and all other indices related to that history, are granular up to a block. However,
from user's perspective, transaction granularity makes much more sense. Blocks exist only as optimisation neccesary to order
transactions without requiring them to refer to one another. When state history and related indices have block granularity,
the peformance of accessing such history deteriorates as number of transactions in a typical block grows. This is because an index only
narrows down the search to the closest block, and the search for specific transaction has to be done sequentially by replaying
transactions one by one from the start of the block.
Erigon2 aims at recording state history at transaction granularity. All related indices would also be at transaction granularity.
This means that indices will narrow down the search to specific transaction, and the peformance of this search would be independent
of how many transactions there are in a typical block.

