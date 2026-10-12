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
