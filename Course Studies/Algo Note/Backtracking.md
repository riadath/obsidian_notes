# <u>Permutations of String</u>

### C++ Implementation
```C++
void permute(string &str,int l,int r){
    if(l == r){
        all_perm.push_back(str);
        return;
    }
    for(int i = l;i <= r;i++){
        swap(str[l],str[i]);
        permute(str,l+1,r);
        swap(str[l],str[i]);
    }
}
```
### Pseudocode
```
procedure permute(str: string, l: int, r: int)
    if l equals r then
        // Base case: reached the end of the string, add the permutation to the result
        all_permutations.append(str)
        return
    end if

    for i from l to r do
        // Swap characters at positions l and i
        swap(str[l], str[i])

        // Recursively permute the remaining characters
        permute(str, l + 1, r)

        // Backtrack: Undo the swap to restore the original string
        swap(str[l], str[i])
    end for
end procedure

```
### State Space Tree Example
![[Pasted image 20231125235423.png]]




# <u>Subset Sum</u>

### C++ Implementation

```cpp
bool flag = false;
void subset_sum(int i,int target, vector<int>set,vector<int> subset){
     if(target == 0){
        flag = true;
        printf("[");
        for(int i = 0;i < subset.size();i++){
            printf(" %d ",subset[i]);
        }         
        printf("]");
        return;
     }
     if(i == (int)set.size())return;

     subset_sum(i + 1,target,set,subset);

     if(set[i] <= target){
         subset.push_back(set[i]);
         subset_sum(i + 1,target-set[i],set,subset);
         subset.pop_back();
     }
}
```

### Pseudocode
```plaintext
procedure subsetSum(i: int, target: int, set: list of int, subset: list of int)
    if target equals 0 then
        // Base case: subset with the desired sum found, print it
        printSubset(subset)
        return
    end if

    if i equals length(set) then
        // Base case: reached the end of the set, no subset found
        return
    end if

    // Exclude the current element and continue searching
    subsetSum(i + 1, target, set, subset)

    // Include the current element if it does not exceed the target
    if set[i] <= target then
        subset.append(set[i])
        subsetSum(i + 1, target - set[i], set, subset)
        subset.popLast() // Backtrack: Remove the last element to explore other possibilities
    end if
end procedure

```

### State Space Tree Example
![[Pasted image 20231125235904.png]]


# N-Queen Problem

### C++ Implementation
```cpp
const int n = 7;
bool n_queen(int col,int board[n][n]){
    if(col >= n){
        return true;
    }
    for(int i = 0;i < n;i++){
        if(can_place_q(board,i,col)){
            board[i][col] = true;
            if(N_queen(col + 1,board)){
                return true;
            }
            board[i][col] = false;

        }
    }
    return false;
}

```

### Pseudocode
```
function solveNQueens(col: int, board: array of array of bool): bool
    if col >= n then
        // All queens are placed successfully, solution found
        return true
    end if

    for i from 0 to n - 1 do
        if canPlaceQueen(board, i, col) then
            // Place a queen at the current position
            board[i][col] = true

            // Recursively try to place the remaining queens
            if solveNQueens(col + 1, board) then
                return true
            end if

            // Backtrack: Undo the placement if it doesn't lead to a solution
            board[i][col] = false
        end if
    end for

    // No solution found for the current configuration
    return false
```

### State Space Tree Example
![[Pasted image 20231126000854.png]]


# Graph Coloring
### C++ Implementation
```cpp
bool graph_coloring(bool graph[N][N],int color[],int v){
    if(v == N){
        return true;
    }    
    for (int c = 1;c <= m;c++){
        if(can_color(v,graph,color,c)){
            color[v] = c;

            if(graph_coloring(graph,color,v + 1)){
                return true;         
            }

            color[v] = 0; // backtracking 
        }
    
    return false;
}
```

### Pseudocode
```
function graphColoring(graph: adjacency matrix, color: array of int, v: int): bool
    if v equals N then
        // All vertices are colored successfully, solution found
        return true
    end if

    for c from 1 to m do
        if canColorVertex(v, graph, color, c) then
            // Color the current vertex with color c
            color[v] = c

            // Recursively try to color the remaining vertices
            if graphColoring(graph, color, v + 1) then
                return true
            end if

            // Backtrack: Undo the color assignment if it doesn't lead to a solution
            color[v] = 0
        end if
    end for

    // No solution found for the current configuration
    return false
end function
```

### State Space Tree Example
![[Pasted image 20231126001520.png |700x350]]


# Hamiltonian Cycle

### C++ Implementation

```cpp
bool ham_cycle(vector<vector<bool>>graph, vector<int> &path, int pos){
    if(pos == N){
        //theres a path from end to start
        if(graph[path[pos-1]][path[0]]){
            return true;
        }else{
            return false;
        }
    }    
    for(int i = 1;i < N;i++){
        if(can_include(i,graph,path,pos)){
            path[pos] = i;
            if(ham_cycle(graph,path,pos+1)){
                return true;
            }
            path[pos] = -1;
        }
    } 
    
    return false;
}
```

### Pseudocode
```
function hamiltonianCycle(graph: array of array of bool, path: array of int, pos: int): bool
    if pos equals N then
        // There's a path from the end to the start
        if graph[path[pos - 1]][path[0]] then
            return true
        else
            return false
        end if
    end if

    for i from 1 to N - 1 do
        if canIncludeVertex(i, graph, path, pos) then
            path[pos] = i
            if hamiltonianCycle(graph, path, pos + 1) then
                return true
            end if
            path[pos] = -1 // Backtrack: Remove the current vertex from the path
        end if
    end for

    return false
end function

```

### State Space Tree Example
![[Pasted image 20231126004449.png|300x200]] 
![[Pasted image 20231126004540.png]]