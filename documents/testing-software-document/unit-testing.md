# Unit Testing

## Unit Testing:
- Informal unit testing by the programmer
– Methodical unit testing by the SQA group

### There are two types of methodical unit testing
– Non-execution-based testing
– Execution-based testing

### Test Case Selection:
- There is no time to test all but the tiniest fraction of all possible test cases, totaling perhaps 10**100 or more
- We need a systematic way to construct test case
- There are two extremes to testing Test to specifications (also called black-box, data-
driven, functional, or input/output driven testing)
– Ignore the code — use the specifications to select test cases
- Test to code (also called glass-box, logic-driven, structured, or path-oriented testing)
– Ignore the specifications — use the code to select test cases

## Errors: 
- Errors are created by human daily
- While correctness attempts to establish that the program is error free, testing 
attempts to find if there are any errors in it. 
- Thus, completeness of testing does not necessarily demonstrate that a program is 
error free. 
- Testing, debugging, and the error removal processes together increase our 
confidence in the correct functioning of the program under test.

## Software reliability:
- Software reliability [ANSI/IEEE Std 729-1983]: is the probability of 
failure free operation of software over a given time interval and under given 
conditions.
- Software reliability is the probability of failure free operation  of software 
in its intended environment.

## Test Debug cycle:
<img src='images/test-debug-cycle.JPG'>

## Test plan:
- A test cycle is often guided by a test plan
- Ex: The **sort program** is to be tested to meet the requirements given earlier. Specially, the following needs to be done:
  - Execute sort at least two input sequences, one with an 'A' and the other with 'D' as request characters.
  - Execute the program on an empty input sequences
  - Test the program for robustness against wrong input
  - All failures of the test program should be recorde in a suitable file using the Company Failure Report Form

## Test case and test set:
- A test case is a pair consisting of test data to be input to the program and the 
expected output. The test data is a set of values, one for each input variable.  
- A test set is a collection of zero or more test cases.

## Testing vs. Verification:
- Program verification aims at proving the correctness of programs by showing 
that it contains no errors. This is very different from testing that aims at 
uncovering errors in a program
- Program verification and testing are best considered as complementary techniques. 
In practice, program verification is often avoided, and the focus is on testing.
- Testing is not a perfect technique in that a program might contain errors 
despite the success of a set of tests.
- Verification promises to verify that a program is free from errors. However, the 
person/tool who verified a program might have made a mistake in the verification 
process; there might be an incorrect assumption on the input conditions; incorrect 
assumptions might be made regarding the components that interface with the 
program, and so on