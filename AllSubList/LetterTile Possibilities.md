# Question
You have n  tiles, where each tile has one letter tiles[i] printed on it. Return the number of possible non-empty sequences of letters you can make using the letters printed on those tiles.

# Example
```
Input: tiles = "AAB"
Output: 8
Explanation: The possible sequences are "A", "B", "AA", "AB", "BA", "AAB", "ABA", "BAA".
```

```
Input: tiles = "AAABBC"
Output: 188
```

# Solutions

```
class Solution {
    private int count =0;
	
	public int numTilePossibilities(String tiles) {
        if (tiles==null||tiles.length()==0){
            return count;
        }
        char[] tileArray = tiles.toCharArray();
        boolean[] bites = new boolean[tileArray.length];
        Arrays.sort(tileArray);
        trackTile(tileArray, bites);
        return count;
    }
    
    private void trackTile(char[] tileArray, boolean[] bites) {
    	for(int i=0; i<tileArray.length;i++) {
    		if (bites[i])
    			continue;
    	    bites[i]=true;
    	    count++;
    	    trackTile(tileArray,bites);
    	    bites[i]=false;
    	    while(i+1<tileArray.length && tileArray[i]==tileArray[i+1]) {
    	    	i++;
    	    }
    	}
}
}
```
