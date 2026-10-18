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

# REVESRE A STACK
def reverseStack(self, stack):
        def solve(left,right,stack):
            if left>=right:
                return stack
            stack[left],stack[right]=stack[right],stack[left]
            return solve(left+1,right-1,stack)
        return solve(0,len(stack)-1,stack)

# CHECK IF THEIR EXISTS SUBSEQUENCE WITH SUM K
def checkSubsequenceSum(self, nums, k):
        def solve(i,current_sum):
            if i==len(nums):
                return current_sum==k
            if solve(i+1,current_sum+nums[i]):
                return True
            if solve(i+1,current_sum):
                return True
            return False
        return solve(0,0)

# COUNT ALL SUBSEQUENCES WITH SUM K
def countSubsequenceWithTargetSum(self, nums, k):
        count=0
        def solve(i,curr_sum):
            nonlocal count    #TREATS count as a local 
            if i==len(nums):
                if curr_sum==k:
                    count+=1
                return
            solve(i+1,curr_sum+nums[i])
            solve(i+1,curr_sum)
        solve(0,0)
        return count

# GENERATE BINARY STRINGS WITHOUT CONSECUTIVE 1's
def generateBinaryStrings(self, n):
        ans=[]
        def solve(s):
            if len(s)==n:
                ans.append(s)
                return 
            #ADD 0
            solve(s+"0")
            #ADD 1
            if len(s)==0 or s[-1]!="1":
                solve(s+"1")
        solve("")
        return ans

# COMBINATION SUM
def combinationSum(self, nums, target):
        ans = []
        def solve(i,remaining,curr):
            if remaining==0:
                ans.append(curr.copy())
                return 
            if i==len(nums) or remaining>target or remaining<0:
                return 
            #PICK THE CURRENT ELEMENT 
            curr.append(nums[i])
            solve(i,remaining-nums[i],curr)
            #POP
            curr.pop()
            #SKIP THE NUMBER
            solve(i+1,remaining,curr)
        solve(0,target,[])
        return ans
