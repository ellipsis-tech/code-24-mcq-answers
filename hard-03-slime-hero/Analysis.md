# Analysis
We can solve this problem using DFS. We start our DFS at the room that we want to start at. We iterate through the current room's neighbours and recurse to them if they are strictly have more enemies than the current room. Because the amount is strictly increasing, we won't go in a cycle or visit a room more than once while adding the amount of enemies along the way

We can improve our solution by reducing the redudancy from duplicate recursion using dynamic programming and memoization. Our solution works similarly to before, where for each junction v we perform a DFS to compute how many junctions would be powered if we provided electricity to v. However, we memoize this DFS; when the DFS is called on a junction v, we first check if v is in our memoization table and return the result if it's present. Otherwise, we recurse and perform DFS as usual, but store the result in the memoization table before returning the result. This memoization implies that among our N DFS calls, an edge will never be traversed twice, because after the first traversal, the result will be memoized, making further traversals unnecessary. This implies our N DFS calls will take in total O(N) time, making this approach sufficiently fast for the large test set.

This also applies to the enemy count