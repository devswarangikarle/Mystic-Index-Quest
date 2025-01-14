# Mystic-Index-Quest

In a bustling village, a clever young scholar named Mira was captivated by the secrets of numbers. One day, while examining a collection of N enchanted gems, she decided to define a special index known as a “Mystic Index.” For Mira, a mystic index is a position in the arrangement of gems where the number of gems divisible by a mystical number K to the left of that index is less than or equal to the number of gems divisible by K to the right. Intrigued by this idea, Mira embarked on a journey to uncover how many mystic indexes were hidden among her enchanted gems. Can you assist Mira in discovering the total number of mystic indexes within her collection?

Input
The first line of the input contains two integers N and K.
The second line of the input contains N space seperated integers.

Constraints
1 ≤ N ≤ 105
1 ≤ K ≤ 100
1 ≤ Ai ≤ 105
Output
Print the number of mystic indexes in the given array.

# Input reading
N, K = map(int, input().split())
A = list(map(int, input().split()))

# Step 1: Preprocess to create the `div_by_k` array
div_by_k = [1 if a % K == 0 else 0 for a in A]

# Step 2: Compute the prefix sum array
prefix = [0] * (N + 1)
for i in range(1, N + 1):
    prefix[i] = prefix[i - 1] + div_by_k[i - 1]

# Step 3: Count Mystic Indexes
mystic_count = 0
for i in range(1, N + 1):
    left_count = prefix[i - 1]
    right_count = prefix[N] - prefix[i - 1]
    if left_count <= right_count:
        mystic_count += 1

# Output the result
print(mystic_count)

