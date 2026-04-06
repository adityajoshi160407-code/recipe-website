Question 1 — Digit Gatekeeper
"Count special numbers in a range"
Imagine you have a list of numbers from L to R. For each number you apply 3 filters like a security gate:

Filter 1 — Is it divisible by K? If no, throw it away
Filter 2 — Does it contain digit 0? If yes, throw it away
Filter 3 — Add all its digits together. Is that sum a prime number? If no, throw it away

Only numbers that pass all 3 filters get counted. Show the final count.

Question 2 — Roll-Seed Lock
"Transform a number 3 times and check result"
Think of it like a combination lock with 3 turns:

Each turn follows a rule — if number is even, do one thing. If odd, do another
After exactly 3 turns, look at the result
Check two things — is it a 3 digit number? AND is its middle digit equal to seed?
If both YES → print YES, otherwise print NO


Question 3 — Mirror Corridor
"Find the nearest palindrome ahead that K can divide"
A palindrome reads the same forwards and backwards (like 121, 66, 1331).

Start from N and keep adding 1 each time
Check if the new number is a palindrome AND divisible by K
The moment you find one, stop and print how many steps you moved (X)
If nothing found in 100000 steps, print -1


Question 4 — Fare Calculator
"Calculate a cab fare step by step"
Think of it like a cab meter that adds charges one by one:

Start with base fare + 7 × distance
Late charge — if more than 15 minutes late, add 20
Long trip charge — if distance more than 10, add 10% of current fare
Seed adjustment — if seed is odd subtract it, if even add it
Round up — round the final amount up to the nearest multiple of 5 (like a cashier rounding bills)


Question 5 — Skipping Numbers
"Add numbers but skip every Nth one"
Imagine adding numbers 1, 2, 3, 4, 5... but every time you hit a multiple of (seed+2) you skip it entirely.

Keep adding until your total reaches at least N
The moment it does, stop
Print what number you stopped at (m) and what the total sum is


Question 6 — Contest Score Judge
"Calculate exam score with penalties and give verdict"
Think of it like a quiz show scoring system:

Calculate score — correct answers give 3 points, partial give 1, wrong deduct 2
Floor rule — if score goes below 0, make it 0 (can't go negative)
Too many answers penalty — if total answers exceed 50, deduct 10 more points
Floor again — if it goes below 0 after penalty, make it 0 again
Verdict — 60 or above is PASS, below 60 is FAIL


Question 1 — Digit Gatekeeper
Outer loop        → O(R - L)        iterates through range
Digit loop        → O(log x)        digits in a number = log10(x)
Prime check       → O(√(digitSum))  digitSum max = 9×7 = 63, so √63 ≈ 8
Since digit sum is always max 63 (7 digits × 9), prime check is effectively constant.
Final: O((R - L) × log x)
Worst case: R - L = 10⁶, log(10⁶) = 6 → ~6 million operations

Question 2 — Roll-Seed Lock
Loop runs exactly 3 times   → O(3) = O(1)
String operations           → O(1)  (3 digit number max)
All checks                  → O(1)
Final: O(1) — Constant time
No loops depend on input size at all.

Question 3 — Mirror Corridor
Outer loop        → O(100000) worst case  if no palindrome found
Palindrome check  → O(log n)              digits in number
Final: O(100000 × log n)
Worst case is always bounded at 100000 iterations regardless of input, so effectively O(1) constant in terms of input size.

Question 4 — Fare Calculator
All steps are simple arithmetic   → O(1)
No loops at all                   → O(1)
Final: O(1) — Constant time
Just 4 inputs and a fixed sequence of math operations.

Question 5 — Skipping Numbers
While loop runs until sum >= N
In worst case (seed=0, divisor=2) roughly half numbers are skipped
So we need ~2x more numbers to reach N
Sum grows roughly as m²/2
To reach sum N, m grows as √(2N)
Final: O(√N)
Worst case: N = 10⁶ → √(2×10⁶) ≈ ~1414 iterations

Question 6 — Contest Score Judge
All operations are simple math    → O(1)
No loops at all                   → O(1)
Final: O(1) — Constant time
Just 3 inputs and fixed arithmetic rules.
