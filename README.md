# Aztec Connect Prize Draw

This repo contains a `jupyter notebook` which uses the [Ape](https://www.apeworx.io/) framework to fetch deposit events fired by deposits made into the Aztec Connect system.

The notebook is relatively simple, given a start and end-date, it will compute the blocks and fetch events within this range. When these events a fetched, we do a a little cleaning (discard the `block_number` and `transaction_hash`, we don’t need them for this task. Afterwards, we group by `assetId` and `depositorAddress`, the grouping means that a user who had two 0.5 eth deposits and thereby satisfy the 1 eth deposit requirement is also counted. Similarly for dai. 

With only eligible users left in the `DataFrame`, we sample a random element, using the `cutoff_block_end` as a “seed”. We use the `cutoff_block_end` as a seed because this let other people run the code to get to the same winner, e.g., anyone can verify. N.B.: the first draw was made without this script using a fixed seed, so you cannot recreate it in the same way :(. 
  