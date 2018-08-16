Graphs
===
# Minimum Height Trees
## Solution 1
    
    Keeping removing leaves until no more than 2 nodes left in the graph.
    This method is based on that there is a/two longest route(s) from leaves to the root.
    Removing the leaves iteratively, the root will be the last one to be remove (because onlynodes 
    with only one in-degree can be removed.)
```Java
    public List<Integer> findMinHeightTrees(int n, int[][] edges) {
        // There is only one node in the tree.
        if(n==1) return Collections.singletonList(0);
        
        List<Set<Integer>> adList =  new ArrayList<>();
        // Generate Adjacent List
        for(int i = 0; i<n; i++){
            adList.add(new HashSet<Integer>());
        }
        for(int[] i :edges){
            adList.get(i[0]).add(i[1]);
            adList.get(i[1]).add(i[0]);
        }
        
        // Find nodes with only one in-degree(i.e leaves)
        List<Integer> leaves = new ArrayList<>();
        for(int i = 0; i<n; i++){
            if(adList.get(i).size()==1){
                leaves.add(i);
            }
        }
        
        // Remove the leaves
        while(n>2){
            List<Integer> newLeaves = new ArrayList<>();
            for(int i : leaves){
                int j = adList.get(i).iterator().next();
                adList.get(j).remove(i);
                if(adList.get(j).size()==1) newLeaves.add(j);
                n--;
            }
            leaves = newLeaves;
        }
        return leaves; 
    }
```
