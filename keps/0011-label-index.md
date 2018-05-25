
## Summary

This proposal presents solutions to make the queries by label selectors in the list API efficient.

## Motivation

Today, only namespace index is supported in the cache. Controllers such as ReplicaSet, when selecting pods, need
to select all the pods first by namespace and then select the ones wanted. While running a large number of pods (xxx), 
we observed that listing all pods and then filtering takes xxx seconds. This proposal presents solutions to improve this.


### Goals

Make the queries by label selectors in the list API efficient

### Proposal

1. Add label based index to facilitate lookup by label.

Since objects are created/deleted dynamically, we also need to update the index efficiently.
Detals follow:

2. Calculate the count for each index and evaluate the most selective first.

3. Provides the ability in API for users to mark which labels to index or build all the index for all labels as the first step.
  
4. `Optional` Add index in API-server cache to improve queries directly going to API-server.

### Graduation Criteria

Provide performance testing results to prove the performance boost.










