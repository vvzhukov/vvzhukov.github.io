{: .box-note}
Used to prerp for the Internship interview @ Google, summer 2021.
Language: Python 3

**Data structures**
Hash set, map: [implementation](https://docs.google.com/document/d/1vG6sD1L0phvNqfElF2qiq7Uto1XT_dMiLXJZXNCS-n8/edit)  
Stacks: [implementation using 2 stacks](https://docs.google.com/document/d/11fkHGH_O2q8k5SyfD6nLWw43k3esZCiL_esMsHVZFP8/edit)  
Queues: [priority queue implementation](https://docs.google.com/document/d/1A1j0g4stoAHPws4NJNdPAJvOi_y2SuKV2ExIs4O36kE/edit) collections.deque, heapq.heapify  
Binary trees: [implementation, BST](https://docs.google.com/document/d/1SsGOBHjdXXhQpD_3kJhCEnu_flM5pKnRjeaNVCeXAdk/edit). [Max path](https://www.geeksforgeeks.org/find-maximum-path-sum-in-a-binary-tree/)  
n-ary trees: [level traversal](https://leetcode.com/problems/n-ary-tree-level-order-traversal/discuss/148877/Python-5-lines-BFS-solution)  
Trie\-trees: [implementation](https://docs.google.com/document/d/1D-K6KWLxO77qWlLRfI-zYC16--JX2kGbyo7ViQga84c/edit)  
red/black tree: [implementation](https://setscholars.net/python-data-structure-and-algorithm-tutorial-red-black-tree/)  
splay tree,  
AVL tree: [implementation](https://www.geeksforgeeks.org/avl-tree-set-1-insertion/)  
min/max heaps: [maxh implementation](https://www.geeksforgeeks.org/max-heap-in-python/)  
  

Graphs: [implementation](https://docs.google.com/document/d/1_7qUHojwm-0aIU_F5HPxypeBkAbWfTXqdTWwDwv1a2M/edit), [distance](https://www.askpython.com/python/examples/distance-between-nodes-unweighted-graph), [search](https://www.educative.io/edpresso/how-to-implement-depth-first-search-in-python), connectivity, [cycle-detection](https://docs.google.com/document/d/1RLHLDKgwo8k-Qe36_WsL38WbKXy4Glkrgy2EagL5Www/edit), [BFS and DFS](https://docs.google.com/document/d/136fqPao_ijfl4XyiySN7CUbZBoJDHC7yJv0Tn4OCcns/edit), [deep copy](https://docs.google.com/document/d/14A7WePuerLRU2F96g1u1DVQgg-Ak-fXIfUxHUxwqqak/edit)  
[MST minimum spanning tree (Prim’s)](https://docs.google.com/document/d/1IKCB2VW64lnpncy5MwiyseE93MMNs1aBF882jfcdMwA/edit)  
[MST Kruskal’s](https://docs.google.com/document/d/1XwL2hcLuqyLdkGxFPoJjemZgVT7aweCOhg12MZAkCO4/edit)  
edge list: space O(e), linear search O(e)  
adjacency matrices: O(v^2) space, check edge connectivity = check whole row  
adjacency lists: find edge – O(d), d = degree of vertex; undir space O(2e), dir O(e)  


**Other algorithms**  

Sorting: [Quick](https://docs.google.com/document/d/1WR6jxHbo5rBaH9MRgfEWw6gTIHEszz2i7MEsGLBcA8g/edit), [Merge](https://docs.google.com/document/d/1IB-_MNrL7lSekBaU63FXx-vEDfrtcp-7HA9we5GrSY4/edit), [Counting](https://www.geeksforgeeks.org/counting-sort/), [Bucket](https://www.geeksforgeeks.org/bucket-sort-2/)  
NP-complete problems - nondeterministic polynomial-time complete. Quick verification, hard to find solution in poly-time.  
Good card shuffling algorithm ([just shuffle](https://www.tutorialspoint.com/python-program-to-shuffle-deck-of-cards), las vegas, monte carlo)  
[Random](https://stackoverflow.com/a/28721505)  
~~~

**OS**  
~~~
processes – instance of a program which is executed by one or many threads  
threads – smallest sequence of instructions which can be executed independently  
concurrency issues, locks,  
Deadlock - situation in which processes/threads block each other due to resource acquisition and none of the processes makes any progress as they wait for the resource held by the other process  
conditions: mutual exclusion, hold and wait, no preemption, circular wait  
Livelock - Livelock is a deadlock-like situation in which processes block each other with a repeated state change yet make no progress.  
Mutexes – a key that gives access to the resource  
Semaphores – generalized mutex  
Monitors – process sync tools  
Context switching works - the process of storing the state of a process or thread, so that it can be restored and resume execution at a later point.  
Scheduling – interrupt of a process, store state in a data structure called PCB (kernel memory, per-process stack)  
[Modern concurrency constructs](https://nikgrozev.com/2015/07/14/overview-of-modern-concurrency-and-parallelism-concepts/) – Green threads (emulate threads on top of JVM), protothreads (stackless threads, share same stack, ‘stack rewinding’), fibers (lightweight threads, not pre-emtied by OS kernel)

**Combinatorics**  
n-choose-k problems and their ilk = (k!)/n!(k-n)!


**Problems  

**[Transactions](http://www.harald-hoyer.de/2015/10/13/a-python-transaction-class/) ([full code](https://harald.hoyer.xyz/files/transaction.py) **class**, transactions)[1146\. Snapshot array](https://leetcode.com/problems/snapshot-array/discuss/1335346/Python-HashMap-and-Binary-Search-Clean-and-Concise) (list, snapshots **class**)  
[394\. Encode/decode string](https://leetcode.com/problems/decode-string/) (string, 3\[a\]2\[bc\])  
[1056\. Confusing number](https://www.goodtecher.com/leetcode-1056-confusing-number/) (int, 6 -> 9)  
[329\. Longest increasing path](https://leetcode.com/problems/longest-increasing-path-in-a-matrix/discuss/299059/Two-simple-Python-DP-solutions) (matrix 1->2->3…)  
[Robot room cleaner](https://www.goodtecher.com/leetcode-489-robot-room-cleaner/) (matrix with obsticles)  
[Traveling salesman](https://www.geeksforgeeks.org/travelling-salesman-problem-implementation-using-backtracking/?ref=lbp) (graph/matrix, visit all nodes for min weight)  
[The knapsack](https://www.geeksforgeeks.org/python-program-for-dynamic-programming-set-10-0-1-knapsack-problem/) (list, max score for limited w)  
[Expressive/stretchy words](https://leetcode.com/problems/expressive-words/submissions/) (string, hello - heeellloooo)  
[Text justification](https://leetcode.com/problems/text-justification/discuss/24891/Concise-python-solution-10-lines.) (string, cut text in blocks)  
[Time to notify all](https://leetcode.com/problems/time-needed-to-inform-all-employees/) (list managers, list inform times)

**Combination sum**[39\. Combination Sum](https://leetcode.com/problems/combination-sum/discuss/310038/Simple-Python-DFS-solutions-for-similar-backtrack-problems) (list, all combinations leading to sum) [40\. Combination Sum II](https://leetcode.com/problems/combination-sum-ii/discuss/310039/Simple-Python-DFS-solutions-for-8-backtrack-problems) (list, all combinations, used once) [216\. Combination Sum III](https://leetcode.com/problems/combination-sum-iii/discuss/310040/Simple-Python-DFS-solutions-for-8-backtrack-problems) (k numbers, n sum, all valid combinations) [77\. Combinations](https://leetcode.com/problems/combinations/discuss/1023998/Simple-Python-DFS-solutions-for-similar-backtrack-problems) (all combinations of k numbers from \[1:n\]) [46\. Permutation](https://leetcode.com/problems/permutations/discuss/309478/Simple-Python-DFS-solution) (all permutations of list) [47\. Permutation II](https://leetcode.com/problems/permutations-ii/discuss/309479/Simple-Python-DFS-solution) (all unique permutations of list) [267\. Palindrome Permutation II](https://github.com/xiaoningning/LeetCode-python/blob/master/267%20Palindrome%20Permutation%20II.py) (string) [78\. Subsets](https://leetcode.com/problems/subsets/discuss/310034/Simple-Python-DFS-solutions-for-8-backtrack-problems) (list, all possible subsets) [90\. Subsets II](https://leetcode.com/problems/subsets-ii/discuss/310037/Simple-Python-DFS-solutions-for-8-backtrack-problems) (list, all possible subsets, no duplicates)  
**Two sum**[3Sum](https://leetcode.com/problems/3sum/) [4Sum](https://leetcode.com/problems/4sum/) [Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/) [Two Sum III - Data structure design](https://leetcode.com/problems/two-sum-iii-data-structure-design/) [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/) [Two Sum IV - Input is a BST](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/) [Two Sum Less Than K](https://leetcode.com/problems/two-sum-less-than-k/) [Max Number of K-Sum Pairs](https://leetcode.com/problems/max-number-of-k-sum-pairs/) [Count Good Meals](https://leetcode.com/problems/count-good-meals/) [Count Number of Pairs With Absolute Difference K](https://leetcode.com/problems/count-number-of-pairs-with-absolute-difference-k/) [Number of Pairs of Strings With Concatenation Equal to Target](https://leetcode.com/problems/number-of-pairs-of-strings-with-concatenation-equal-to-target/)  
  
**Subarray, Submatrix**  
[1074\. Number of Submatrices That Sum to Target](https://leetcode.com/problems/number-of-submatrices-that-sum-to-target/discuss/344440/Simple-Python-DP-solution) (sub matrices, sum to num) [560\. Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/discuss/344431/Simple-Python-DP-solution) (list, combinations) [974\. Subarray Sums Divisible by K](https://leetcode.com/problems/subarray-sums-divisible-by-k/discuss/344436/Simple-Python-DP-solution) (list, combinations) [325\. Maximum Size Subarray Sum Equals k](https://www.goodtecher.com/leetcode-325-maximum-size-subarray-sum-equals-k/) (list, subarray) [363\. Max Sum of Rectangle No Larger K](https://leetcode.com/problems/max-sum-of-rectangle-no-larger-than-k/discuss/445540/Python-bisect-solution-(960ms-beat-71.25)) (matrix, rectangles)

  
**Rectangles**  
[84\. Largest rectangle in histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/discuss/28917/AC-Python-clean-solution-using-stack-76ms) (histogram, rectangle) - [Max rectangle area with 1 vs 0](https://leetcode.com/problems/maximal-rectangle/discuss/29065/AC-Python-DP-solutioin-120ms-based-on-largest-rectangle-in-histogram) (matrix, rectangle with 1s)  
  

**Word transformation / Move a box, keys, obstacles**  
[127\. Transform word](https://leetcode.com/problems/word-ladder/discuss/352659/Python-Simple-BFS-solution-(similar-problems-listed)) (string, from one word to another) [102\. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/discuss/1651394/Python-level-by-level-BFS-Solution) (tree traverse, level) [127\. Word Ladder](https://leetcode.com/problems/word-ladder/discuss/352659/Simple-Python-BFS-solution) (string, transformation sequence, number of words) [126\. Word Ladder II](https://leetcode.com/problems/word-ladder-ii/discuss/352661/Simple-Python-BFS-solution) (string, transformation sequence, words seqs) [301\. Remove Invalid Parentheses](https://leetcode.com/problems/remove-invalid-parentheses/discuss/327481/Python-DFS-solution-with-pruning-(28-ms-beat-99.56)-%2B-BFS-solution) (string, parenthesis) [317\. Shortest Distance from All Buildings](https://leetcode.com/problems/shortest-distance-from-all-buildings/discuss/331983/Python-BFS-solution-(52-ms-beat-98.27)) [773\. Sliding Puzzle](https://leetcode.com/problems/sliding-puzzle/discuss/412586/Standard-Python-BFS-solution-(level-by-level-traversal)) (game 15) [815\. Bus Routes](https://leetcode.com/problems/bus-routes/discuss/1651399/Python-Level-by-level-BFS-solution) (graph, least number of buses) [854\. K-Similar Strings](https://leetcode.com/problems/k-similar-strings/discuss/420506/Python-BFS-solution) (strings, min swaps) [864\. Shortest Path to Get All Keys](https://leetcode.com/problems/shortest-path-to-get-all-keys/discuss/364604/Simple-Python-BFS-Solution-(292-ms-beat-97.78)) (matrix, path, keys) [1091\. Shortest Path in Binary Matrix](https://leetcode.com/problems/shortest-path-in-binary-matrix/discuss/313229/Python-BFS-solution) (matrix, clear path) [1210\. Minimum Moves to Reach Target with Rotations](https://leetcode.com/problems/minimum-moves-to-reach-target-with-rotations/discuss/392940/Standard-Python-BFS-solution) (matrix, snake moves and rotations) [1263\. Minimum Moves to Move a Box to Their Target Location](https://leetcode.com/problems/minimum-moves-to-move-a-box-to-their-target-location/discuss/431138/Python-straightforward-BFS-solution) (matrix, store keeper box) [1293\. Shortest Path in a Grid with Obstacles Elimination](https://leetcode.com/problems/shortest-path-in-a-grid-with-obstacles-elimination/discuss/1651383/Python-level-by-level-BFS-Solution) (path with obstacles elimination)

**String window  
**[727\. Minimum window subsequence](https://github.com/GJzh/Leetcode/blob/master/python/727.%20Minimum%20Window%20Subsequence.py) (string, find window) [76\. Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/discuss/344533/Simple-Python-two-pointer-solution) (string, substring including duplicates) [1208\. Get Equal Substrings Within Budget](https://leetcode.com/problems/get-equal-substrings-within-budget/discuss/392901/Simple-Python-moving-window) (string ASCII distance) [3\. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/discuss/348137/Simple-Python-two-pointer-solution-(52ms-beat-97.94)) (string, no repeat) [159\. Longest Substring with At Most Two Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-two-distinct-characters/discuss/348157/Simple-Python-two-pointer-solution) (string, two distinct) [340\. Longest Substring with At Most K Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/discuss/348216/Simple-Python-two-pointer-solution-(72-ms-beat-94.93)) (string, k distinct) [992\. Subarrays with K Different Integers](https://leetcode.com/problems/subarrays-with-k-different-integers/discuss/348984/Different-Python-two-pointer-solutions) (subarrays, k different) [424\. Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/discuss/363071/Simple-Python-two-pointer-solution) (string, replacement) [209\. Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/discuss/344476/Simple-Python-two-pointer-solution) (array, min subarray greater k) [713\. Subarray Product Less Than K](https://leetcode.com/problems/subarray-product-less-than-k/discuss/344245/Simple-Python-solution-(beat-94.59)) (subarray, product less) [76\. Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/discuss/344533/Simple-Python-two-pointer-solution) (string, substring)

**Meeting rooms**  
[253\. Meeting Rooms II](https://medium.com/@edward.zhou/leetcode-253-meeting-rooms-ii-explained-python3-solution-3f8869612df) (find min meeting rooms num) [731\. My Calendar II](https://leetcode.com/problems/my-calendar-ii/discuss/323479/Simple-C%2B%2B-Solution-using-built-in-map-(Same-as-253.-Meeting-Rooms-II)) (list, no triple booking) [732\. My Calendar III](https://leetcode.com/problems/my-calendar-iii/discuss/302492/Simple-C%2B%2B-Solution-using-built-in-map-(Same-as-253.-Meeting-Rooms-II)) (return the intersection) [1094\. Car Pooling](https://leetcode.com/problems/car-pooling/discuss/319088/Simple-Python-solution) (list, locations, passengers) [1109\. Corporate Flight Bookings](https://leetcode.com/problems/corporate-flight-bookings/discuss/328949/Simple-Python-solution) (list, seats numbers, ) [218\. The Skyline Problem](https://leetcode.com/problems/the-skyline-problem/discuss/325070/SImple-Python-solutions) (skyline intersection)

**Trie** **problems**  
[208\. Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/discuss/320224/Simple-Python-solution) [1233\. Remove Sub-Folders from the Filesystem](https://leetcode.com/problems/remove-sub-folders-from-the-filesystem/discuss/409075/standard-python-prefix-tree-solution) [1032\. Stream of Characters](https://leetcode.com/problems/stream-of-characters/discuss/320837/Standard-Python-Trie-Solution) (check from char string if a suffix is in dic) [211\. Add and Search Word - Data structure design](https://leetcode.com/problems/add-and-search-word-data-structure-design/discuss/319361/Simple-Python-solution) (map, add, search) [676\. Implement Magic Dictionary](https://leetcode.com/problems/implement-magic-dictionary/discuss/320197/Simple-Python-solution) (search word in dict) [677\. Map Sum Pairs](https://leetcode.com/problems/map-sum-pairs/discuss/320237/Simple-Python-solution) (design map with prefix sum) [745\. Prefix and Suffix Search](https://leetcode.com/problems/prefix-and-suffix-search/discuss/320712/Different-Python-solutions-with-thinking-process) (search words by prefix and suffix) [425\. Word Squares](https://www.goodtecher.com/leetcode-425-word-squares/) (find all word squares you can build)

**Buy and sell**  
[121\. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/discuss/306438/Python-O(n)-solution-with-thinking-process) (list, day to buy, day to sell) [122\. Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/discuss/306427/Different-O(n)-Python-solutions-with-thinking-process) (list, buy and sell many times) [309\. Best Time to Buy and Sell Stock with Cooldown](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/discuss/306235/Different-DP-Python-solutions-with-thinking-process) (buy, sell, cooldown) [188\. Best Time to Buy and Sell Stock IV](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/discuss/306282/Different-DP-Python-solutions-with-thinking-process) (at most k transactions) [714\. Best Time to Buy and Sell Stock with Transaction Fee](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/discuss/444413/Different-Python-solutions-with-thinking-process-to-solve-the-series-of-stock-problems) (with fee)

**Binary tree / path sum**  
[257\. Binary Tree Paths](https://leetcode.com/problems/binary-tree-paths/discuss/309004/Different-DFS-Python-solutions) (all root-to leaf paths) [129\. Sum Root to Leaf Numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers/discuss/328123/Simple-Python-Solution%3A-top-down-DFS) (sum of root-to-leaf numbers) [1022\. Sum of Root To Leaf Binary Numbers](https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers/discuss/328033/Top-down-Python-DFS-Solution) (all paths sums) [988\. Smallest String Starting From Leaf](https://leetcode.com/problems/smallest-string-starting-from-leaf/discuss/328119/Simple-Python-Solution%3A-top-down-DFS) (smallest lexico) [112\. Path Sum](https://leetcode.com/problems/path-sum/discuss/328124/Simple-Python-Solution%3A-top-down-DFS) (find sum)  
[113\. Path Sum II](https://leetcode.com/problems/path-sum-ii/discuss/328125/Simple-Python-Solution%3A-top-down-DFS) (return list of nodes sum up to sum) [437\. Path Sum III](https://leetcode.com/problems/path-sum-iii/discuss/328128/Simple-Python-Solution%3A-top-down-DFS-%2B-DP) (path along to the root)

[378\. Kth Smallest Element in a Sorted Matrix](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/discuss/1004232/Python-solution-with-thinking-process) [668\. Kth Smallest Number in Multiplication Table](https://leetcode.com/problems/kth-smallest-number-in-multiplication-table/discuss/1714072/Simple-Python-Binary-Search-(similar-problem-listed)) [410\. Split Array Largest Sum](https://leetcode.com/problems/split-array-largest-sum/discuss/326747/Python-solutions-with-thinking-process) [1011\. Capacity To Ship Packages Within D Days](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/discuss/390359/Simple-Python-Binary-Search) [1231\. Divide Chocolate](https://leetcode.com/problems/divide-chocolate/discuss/409956/Simple-Python-Binary-Search-(similar-problem-listed)) [875\. Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/discuss/390523/Simple-Python-Binary-Search) [774\. Minimize Max Distance to Gas Station](https://leetcode.com/problems/minimize-max-distance-to-gas-station/discuss/390526/Simple-Python-Binary-Search) [1201\. Ugly Number III](https://leetcode.com/problems/ugly-number-iii/discuss/390530/Simple-Python-Binary-Search) [1482\. Minimum Number of Days to Make m Bouquets](https://leetcode.com/problems/minimum-number-of-days-to-make-m-bouquets/discuss/1714075/Simple-Python-Binary-Search-(similar-problem-listed)) [2141\. Maximum Running Time of N Computers](https://leetcode.com/problems/maximum-running-time-of-n-computers/discuss/1698346/Python-Binary-search-solution-(similar-problems-listed))

**Calculator**  
[224\. Basic Calculator](https://leetcode.com/problems/basic-calculator/discuss/429098/Python3-solution-after-tokenization-(60ms-beat-99.75)) [227\. Basic Calculator II](https://leetcode.com/problems/basic-calculator-ii/discuss/429100/Python3-solution-after-tokenization-(56ms-beat-99.92)) [282\. Expression Add Operators](https://leetcode.com/problems/expression-add-operators/discuss/310707/Clean-Python-DFS-solution) [772\. Basic Calculator III](https://leetcode.com/problems/basic-calculator-iii/discuss/429132/Python3-solution-after-tokenization-(40ms-beat-93.59))  
  
**Prerequisites**  
[207\. Course schedule](https://leetcode.com/problems/course-schedule/discuss/311183/Different-Python-solutions-with-thinking-process), [210\. Course schedule II](https://leetcode.com/problems/course-schedule-ii/discuss/311215/Different-Python-solution-with-thinking-process). (list, graph requirements)  
**  
Code/Encode tree**  
[297\. Serialize and Deserialize Binary Tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/discuss/314218/Python-BFS-and-DFS-solutions) [428\. Serialize and Deserialize N-ary Tree](https://leetcode.com/problems/serialize-and-deserialize-n-ary-tree/discuss/358636/Simple-Python-DFS-solution)  
  
[11\. Container with most water](https://leetcode.com/problems/container-with-most-water/discuss/6131/O(N)-7-line-Python-solution-72ms) (water stayed)  
[245\. Strobogrammatic number](https://github.com/chenjienan/python-leetcode/blob/master/247.strobogrammatic-number-ii.py) (number with change)  
[687\. Longest Univalue path](https://leetcode.com/problems/longest-univalue-path/discuss/123735/Python-3-recursive-and-iterative-solution) (tree, longest path with same value)  
[938\. Range Sum of BST](https://leetcode.com/problems/range-sum-of-bst/discuss/192019/JavaPython-3-3-similar-recursive-and-1-iterative-methods-w-comment-and-analysis.) (sum of keys in binary search tree by range)  
[296: Best Meeting Point](https://baihuqian.github.io/2018-08-01-best-meeting-point/) (matrix, distances)  
[2\. Add two numbers in the linked list](https://leetcode.com/problems/add-two-numbers/discuss/1016/Clear-python-code-straight-forward) (linked list, sum)

**Sliding window**  
[Sliding window](https://www.geeksforgeeks.org/window-sliding-technique/), [239\. Sliding window max](https://leetcode.com/problems/sliding-window-maximum/discuss/65901/9-lines-Ruby-11-lines-Python-O(n)) (list, max value), [480\. Sliding Window Median](https://leetcode.com/problems/sliding-window-median/discuss/96355/Easy-Python-O(nk)) (list, median), [Sliding Window Average](https://stackoverflow.com/a/53142177) (list, avg)  
[715\. Range Module](https://leetcode.com/problems/range-module/) (module)  
[15\. 3Sum](https://leetcode.com/problems/3sum/) [1\. TwoSum](https://leetcode.com/problems/two-sum/) [16\. 3Ssum Closest](https://leetcode.com/problems/3sum-closest/) [18\. 4Sum](https://leetcode.com/problems/4sum/)  
[Jump game 1](https://leetcode.com/problems/jump-game/) (array, first idx) [Jump game 2](https://leetcode.com/problems/jump-game-ii/) (array, min number of jumps) [Jump game 3](https://leetcode.com/problems/jump-game-iii/) (array, custom start) [Jump game 4](https://leetcode.com/problems/jump-game-vii/) (string, min max)  
  
Backtracking problems: [Combinations/permutations/subset/combination sum](https://leetcode.com/problems/combination-sum/discuss/429538/General-Backtracking-questions-solutions-in-Python-for-reference-%3A)  
[Min cash flow](https://www.geeksforgeeks.org/minimize-cash-flow-among-given-set-friends-borrowed-money/)  
2079\. [Watering plants](https://leetcode.com/problems/watering-plants/discuss/1589981/Python-Easy-Solution-BEATS-~-100-Faster-and-100-Memory-Usage) (1 worker) 2105. [Watering plants II](https://leetcode.com/problems/watering-plants-ii/discuss/1624252/Python3-2-pointers) (2 workers)

**Flipping matrix**  
[Flip row or column and get all zeroes](https://walkccc.me/LeetCode/problems/2128/) [Flip binary matrix to get high score](https://www.geeksforgeeks.org/maximum-score-after-flipping-a-binary-matrix-atmost-k-times/)

**Frequent  
**[Min amplitude after 3 changes](https://leetcode.com/problems/minimum-difference-between-largest-and-smallest-value-in-three-moves/discuss/802386/Python-3-lines-well-explained-Greedy-O(nlogn)) (int list, change 3 times, max diff)  
[Ways to split string](https://leetcode.com/problems/number-of-good-ways-to-split-a-string/discuss/755264/Python-O(N)-Sliding-Window) (string, split: left = right)  
[Max time for given digits](https://leetcode.com/problems/largest-time-for-given-digits/discuss/822874/Python-Check-all-permutations-explained) (list, max time from it)  
[Server loads balancing / stone game](https://leetcode.com/problems/last-stone-weight-ii/discuss/402213/Python-solution-based-on-0-1-Knapsack) (list, split by 2, combine)  
[Most booked hotel rooms](https://leetcode.com/discuss/interview-question/421787/) (which room is booked the most?)  
[Min domino rotations](https://leetcode.com/problems/minimum-domino-rotations-for-equal-row/discuss/451567/Python-easy-solution) (domino rotations)  
[Time to type a string](https://leetcode.com/discuss/interview-question/356477) (string, based on positions)  
[Max lvl sum of a binary tree](https://leetcode.com/problems/maximum-level-sum-of-a-binary-tree/discuss/360968/JavaPython-3-Two-codes-language%3A-BFS-level-traversal-and-DFS-level-sum.) (smallest level with the max sum)  
[Min Number of Chairs](https://leetcode.com/discuss/interview-question/356520) (lists, arrive, leave, get number of seats)  
[K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/discuss/294389/Easy-to-read-Python-min-heap-solution-(-beat-99-python-solutions-)) (list of points, k closest to origin)  
[Odd Even Jump](https://leetcode.com/problems/odd-even-jump/discuss/217981/JavaC%2B%2BPython-DP-using-Map-or-Stack) (list, odd/even jumps)  
[License Key Formatting](https://leetcode.com/problems/license-key-formatting/discuss/96497/Python-solution) (string, reformat)  
[Unique Email Addresses](https://leetcode.com/problems/unique-email-addresses/discuss/1488812/Python-short-solution-explained) (list, email filter)  
[Fruit Into Baskets](https://leetcode.com/problems/fruit-into-baskets) (list, baskets)  
[Min Days to Bloom](https://leetcode.com/problems/minimum-number-of-days-to-make-m-bouquets/discuss/686316/JavaC%2B%2BPython-Binary-Search) (list, k adjusted, l bouquets)  
[Fill Matrix](https://leetcode.com/discuss/interview-question/341295/Google-or-Online-Assessment-2019-or-Fill-Matrix) (two diagonals and columns are equal)  
[Decreasing Subsequences](https://leetcode.com/discuss/interview-question/350233/Google-or-Summer-Intern-OA-2019-or-Decreasing-Subsequences) (list, split it in decreasing subsequences)  
[Max Distance](https://leetcode.com/discuss/interview-question/350363/Google-or-OA-2018-or-Max-Distance) (binary strings, max editing distance) [solution](https://leetcode.com/playground/oqEJBL39)  
[Stores and Houses](https://leetcode.com/discuss/interview-question/350248/Google-or-Summer-Intern-OA-2019-or-Stores-and-Houses) (2 lists, closest house to the store)  
[Pairs of integers](https://leetcode.com/discuss/interview-question/1586927/Google-or-OA) (list, form equal pairs)  
[Longest substring with last == first](https://leetcode.com/discuss/interview-question/1586927/Google-or-OA) (string, substring last = first)  
[Alphabet board path](https://leetcode.com/problems/alphabet-board-path/discuss/1816966/Python-Easy-to-Understand) (matrix, alpha, UDLR)  
[Solve series of equations](https://docs.google.com/document/d/1pZPnTWoGkgEavVu1i1V44A4IS5jo6VHbyUr4rx3U6d8/edit) (A = B+1, B = 1)  
[444\. Sequence reconstruction](https://www.goodtecher.com/leetcode-444-sequence-reconstruction/) ((321) = (1,2)+(1,3)+(2,3))  
[221\. Maximum Square](https://leetcode.com/problems/maximal-square/discuss/600149/Python-Thinking-Process-Diagrams-DP-Approach) (matrix, max square area)  
[295\. Median in list](https://leetcode.com/problems/find-median-from-data-stream/) (list, **class** to find median)  
[818\. Race car](https://leetcode.com/problems/race-car/discuss/124312/Javascript-Python3-C%2B%2B-.-BFS-solutions) (speed (A\*2/R-1), position)  
[Temperature sliding window](https://docs.google.com/document/d/1CqICUQLKxDZvHSRZd_-kKGTniycfzopeOnn6py5K5HA/edit) (monotonic queue, max temperature, sliding window)  
[366\. Find Leaves of binary tree](https://zhenyu0519.github.io/2020/03/21/lc336/) (any tree, convert tree to list)  
[Jobs, max cpus, duration](https://leetcode.com/discuss/interview-question/1471821/Google-screening-round-Job-scheduling) (list, check if job can be executed)  
[Calculate max ancestors](https://leetcode.com/discuss/interview-question/1673287/Google-or-Virtual-Onsite-or-Maximum-Ancestor-for-Leaves) (tree, Max ancestors)  
[Combinations of a RGBY](https://leetcode.com/discuss/interview-question/1850189/Googleor-Phone-screen) (list, top k sum combinations)

**Language**  
Max int variable  
  
List comprehension _newList_ **_\=_** **_\[_** _expression(element)_ **_for_** _element_ **_in_** _oldList_ **_if_** _condition **\]**_   
Iterators - iterator protocol: \_\_iter\_\_() and \_\_next\_\_(). [Custom iterator](https://www.programiz.com/python-programming/iterator)  
Lambda functions – anonymous functions, called by ‘\_’ (lambda x: x + 1)(2); high level functions: high\_ord\_func = lambda x, func: x + func(x); high\_ord\_func(2, lambda x: x \* x)  
  
  
Prep google docs:  
1\. Font to consolus  
2\. Tools -> prefs -> turn off auto

  
During interview:

0\. Overexplain staff  
1\. **Ask clarification questions** to make sure you understand the problem correctly  
2\. **Discuss any assumptions** you're planning to make to solve the problem  
3\. **Analyze various solutions** and tradeoffs before starting to code  
4\. Plan and implement your solution  
5\. **Test your solution**, including corner and edge cases
