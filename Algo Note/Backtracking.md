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
![[Pasted image 20231125235904.png | 900x450]]


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

### Psuedocode
```
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

procedure printSubset(subset: list of int)
    print("[")
    for i from 0 to length(subset) - 1 do
        print(" ", subset[i], " ")
    end for
    print("]\n")
end procedure

// Example usage:
flag = false
input_set = [1, 2, 3, 4, 5]
target_sum = 9
subsetSum(0, target_sum, input_set, [])

// The flag variable can be checked to determine if a subset with the target sum was found
if flag is false then
    print("No subset found with the target sum.")
end if

```