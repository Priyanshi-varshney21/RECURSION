# RECURSION
# POW(x,n)
def myPow(self, x, n):
        if n < 0:
            x = 1 / x 
            n = -n
        ans = 1.0
        while n > 0:
            if n % 2 == 1:
                ans *= x
            x *= x
            n //= 2
        return ans

# GENERATE PARENTHESIS
def generateParenthesis(self, n):
        ans=[]
        def solve(s,open,close):
            if open==n and close==n:
                ans.append(s)
                return 
            if open<n:
                solve(s+"(",open+1,close)
            if close<open:
                solve(s+")",open,close+1)
        solve("",0,0)
        return ans

# POWER SET
def powerSet(self, nums):
        ans=[]
        def solve(i,s):
            if i==len(nums):
                ans.append(s.copy())
                return 
            #INCLUDE 
            s.append(nums[i])
            solve(i+1,s)
            #EXCLUDE
            s.pop()
            solve(i+1,s)
        solve(0,[])
        return ans
# COUNT GOOD NUMBERS
def countGoodNumbers(self, n: int) -> int:
        MOD=10**9+7
        def power(x,n):
            if n==0:
                return 1
            half=power(x,n//2)
            ans=(half*half)%MOD
            if n%2==1:
                ans=(half*x)%MOD
            return ans
        even =(n+1)//2
        odd=n//2
        return (power(5,even)*power(4,odd))%MOD
