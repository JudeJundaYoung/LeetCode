Union_Find
=

## Surrounded Regions

```Java
class Solution {
    int[] group;
    static int BOUND_GROUP = 0;
    
    public int find(int i){
        return (group[i]==i)? i:find(group[i]);
    }
    
    public void unite(int i1, int i2){
        int g1 = find(i1);
        int g2 = find(i2);
        if(g1==BOUND_GROUP){
            group[g2] = g1;
        }
        else{
            group[g1] = g2;
        }
    }
    
    public void solve(char[][] board) {
        int m = board.length;
        if(m==0) return;
        int n = board[0].length;
        if(n==0) return;
        group = new int[m*n];
        
        for(int i = 0; i<m*n; i++){
            group[i] = i;
        }
        
        for(int i = 0; i<m; i++){
            for(int j = 0; j<n; j++){
                if(board[i][j]=='X') continue;
                if(i==0||j==0||i==m-1||j==n-1) unite(BOUND_GROUP, j*m+i);
                else{
                    if(board[i-1][j]=='O') unite(i-1+j*m,i+j*m);
                    if(board[i][j-1]=='O') unite(i+(j-1)*m,i+j*m);
                    if(board[i+1][j]=='O') unite(i+1+j*m,i+j*m);
                    if(board[i][j+1]=='O') unite(i+(j+1)*m,i+j*m);
                    
                }
            }
        } 
        for(int i = 0; i<m; i++){
            for(int j = 0; j<n; j++){
                if(find(j*m+i)!=BOUND_GROUP){
                    board[i][j] = 'X';
                }
            }
        }
    }
}
```
