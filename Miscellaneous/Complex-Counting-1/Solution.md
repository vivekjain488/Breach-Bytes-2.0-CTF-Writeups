MOD = int(1e9 + 7)

def count_divisible_by_5(N):
    <br>dp = [0] * 5
    <br>dp[0] = 1  # Empty subset
    
    for i in range(1, N + 1):
        new_dp = dp[:]  # Create a copy to update current state
        for j in range(5):
            new_dp[(j + i) % 5] = (new_dp[(j + i) % 5] + dp[j]) % MOD
        dp = new_dp
    
    return dp[0]

# Test for N = 1000
N = 1000
<br>print(count_divisible_by_5(N))
