# question-no-3362
Solution to the question no 3362 on leet code 

3362. Zero Array Transformation III
You are given an integer array nums of length n and a 2D array queries where queries[i] = [li, ri].

Each queries[i] represents the following action on nums:

Decrement the value at each index in the range [li, ri] in nums by at most 1.
The amount by which the value is decremented can be chosen independently for each index.
A Zero Array is an array with all its elements equal to 0.

Return the maximum number of elements that can be removed from queries, such that nums can still be converted to a zero array using the remaining queries. If it is not possible to convert nums to a zero array, return -1.

Explanation:
Sort the queries by start time so we can process them in order as time progresses.

Use two priority queues:

available: stores deadlines of queries that are ready to be assigned (max-heap).

assigned: stores deadlines of currently assigned queries (min-heap).

For each time i:

Remove expired assigned queries (those with deadline < current time).

Add new available queries whose start time ≤ current time.

Try to assign up to nums[i] queries from available (with deadline ≥ current time).

If not enough valid queries are available, return -1 (not possible).

After processing, return the number of unassigned queries: queries.length - count.
