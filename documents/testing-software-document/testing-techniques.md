# Testing Tools

## Abstract:

- The paper is basic introduction to software testing methodologies. Majority of the code is
is from other researcher (some was written by myself)
- Paper is written using PyCharm in markdown style and render by [md2pdf](https://md2pdf.netlify.app/)

<hr>

## 1. Automation Testing:
### A. Introduction:
- Using a set of commands that enable the system to continuous test the target system with the ability to record the result

### B. Example/Explain:
#### Automate UI testing with PyAutoGUI in Python:
- In the GUI Tets (section number 6) I demonstrate the automated testing using the PyAutoGUI package
#### Automate UI testing with Selenium and Beautiful Soup in Python:
  - we can also be using [Selenium](https://selenium-Python.readthedocs.io/), and [Beautiful Soup 4](https://beautiful-soup-4.readthedocs.io/en/latest/) to perform autonomous test tasks
    - I use Selenium and Beautiful Soup for web scrapping and generating data for reports and research... 
The purpose is different, but I realize I can use those packages for finding specific elements (container, images link, button, data ...)
. Then assign tasks (click, keyboard enter) that Selenium allows us to do. Finally, store the script and schedule an appropriate execution time
#### Automate UI testing with Selenium and Unittest in Python:
- Unittest is inherited from the PyUnit, Python Unittest package has 5 components: Test loader, test case, test suite, test runner, and test report 
- code demonstrate of using Unittest and Selenium to test if an image link is clickable
- the script using selenium web driver and Unittest.TestCase to perform a couple of autonomous tasks: test the search box, test image link, test language setting, and test if some element is present
- code retrieved from (2)
```python
import unittest
from selenium import webdriver
from selenium.common.exceptions import NoSuchElementException
from selenium.webdriver.common.by import By

class HomePageTest(unittest.TestCase):
    @classmethod
    def setUp(inst):
        # create a new Firefox session """
        inst.driver = webdriver.Firefox()
        inst.driver.implicitly_wait(30)
        inst.driver.maximize_window()

        # navigate to the application home page """
        inst.driver.get("http://www.google.com/")

    def test_search_box(self):
        # check search box exists on Home page
        self.assertTrue(self.is_element_present(By.NAME,"q"))

    def test_language_settings(self):
        # check language options on Home page
        self.assertTrue(self.is_element_present(By.ID,"_eEe"))

    def test_images_link(self):
        # check images link on Home page
        images_link = self.driver.find_element_by_link_text("Images")
        images_link.click()
        # check search field exists on Images page
        self.assertTrue(self.is_element_present(By.NAME,"q"))
        self.search_field = self.driver.find_element_by_name("q")
        # enter search keyword and submit
        self.search_field.send_keys("Selenium Webdriver framework architecture diagram")
        self.search_field.submit()

    @classmethod
    def tearDown(inst):
        # close the browser window
        inst.driver.quit()

    def is_element_present(self, how, what):
        """
        Helper method to confirm the presence of an element on page
        :params how: By locator type
        :params what: locator value
        """
        try: self.driver.find_element(by=how, value=what)
        except NoSuchElementException: return False
        return True

if __name__ == '__main__':
    unittest.main(verbosity=2)
```
### C. Advantages/Disadvantage
#### Advantage:
- Reliable: eliminating human error
- Repeatable: test the software under repeated execution of the same operations
- Cost reduction: more tests with less human resources
- reusable: test design one and run at every development step

#### Disadvantage:
- Proficiency is required to write the automation test scripts.
- Debugging the test script is a major issue.
- Test maintenance is costly in the case of playback methods (in the situation when we change the graphic user interface) (3)

### D. Applications: 
#### Kind of applications:
- Automated testing can be performed on any system: embedded system, web app, desktop app 
- On any ongoing development application 
- On integration testing step(test as we go)
- Can also test on the stable version just to make sure no unexpected incident has happened
#### Justify:
Since automated testing is not costly (designed one and reuse every time). It can be used at every development miles stone 
to make sure the overall development is working well.
### E. Reference:
- [Build A Selenium Python Test Suite From Scratch Using Unittest](https://www.techbeamers.com/selenium-Python-test-suite-unittest/#:~:text=Selenium%20Python%20Unittest%20Framework%20Test%20Loader%20%E2%80%93%20It%E2%80%99s,TestSuite%20object%20that%20carries%20those%20cases%20and%20suites.) (2)
- [Beautiful Soup Python](https://beautiful-soup-4.readthedocs.io/en/latest/) (3)
- [Selenium Python](https://selenium-python.readthedocs.io/)

<hr>

## 2. Data flow Testing

### A. Introduction:
- Data Flow testing follows the flow of the application ()control flow graph and focuses on the points at which variables receive values and the points at which these values are used.

### B. Example/Explain:
- Using Tkinter package (for Local drawing), and pycfg.py (automate CFG task). 
CFG helps us find independent paths (Cyclomatic Complexity), which leads to the number of test cases required to test the program
- The script simply a while loop
- whiletest.py content
```python
# whiletest.py
a= 10
while(a <= 0):
    if a == 5:
        print(a)
    a += 1
print("exited")
```
- put the 2 files in the same folder or we can navigate them 
```linux
Python path_to/pycfg.py path_to/whiletest.py -d
```
- run this script to test the 'whiletest.py' control flow
```python
from pycfg.pycfg import PyCFG, CFGNode, slurp
import argparse
import tkinter as tk
from PIL import ImageTk, Image

if __name__ == '__main__':
   parser = argparse.ArgumentParser()
    
    # replace 'Pythonfile' with 'whiletest.py'
   parser.add_argument('Pythonfile', help ='The Python file to be analyzed')
   args = parser.parse_args()
   arcs = []

   cfg = PyCFG()
   cfg.gen_cfg(slurp(args.Pythonfile).strip())
   g = CFGNode.to_graph(arcs)
   g.draw(args.Pythonfile + '.png', prog ='dot')

   # Draw using tkinter.
   root = tk.Tk()
   root.title("Control Flow Graph")
   img1 = Image.open(str(args.Pythonfile) + ".png") # PIL solution
   img1 = img1.resize((800, 600), Image.ANTIALIAS)
   img = ImageTk.PhotoImage(img1)
   
   background ="gray"

   panel = tk.Label(root, height = 600, image = img)
   panel.pack(side = "top", fill ="both", expand = "yes")
   nodes = g.number_of_nodes()     # no. of nodes.
   edges = g.number_of_edges()     # no. of Edges.
   complexity = edges - nodes + 2     # Cyclomatic complexity

   frame = tk.Frame(root, bg = background)
   frame.pack(side ="bottom", fill ="both", expand = "yes")
      
   tk.Label(frame, text ="Nodes\t\t"+str(nodes), bg = background).pack()
   tk.Label(frame, text ="Edges\t\t"+str(edges), bg = background).pack()
   tk.Label(frame, text ="Cyclo Complexity\t"+
         str(complexity), bg = background).pack()

   root.mainloop()

```
- output will be generated using tinker in the picture format
- output: 
<img src='images/control-flow-testing.jpg'>
### C. Advantages/Disadvantage
#### Advantage:
According to (4), Data Flow testing helps us to pinpoint any of the following issues:
- A variable that is declared but never used within the program.
- A variable that is used but never declared.
- A variable that is defined multiple times before it is used.
- Deallocating a variable before it is used.
- User can clearly see what need to test -> easy to test
- Prevent crashing

#### Disadvantage:
- Time consuming and costly process
- Requires knowledge of programming languages to draw flow-cart software
- Drawing chart manually (hand made diagram) can create mistake

### D. Applications: 
#### Kind of applications:
- Backend, logic application (command line, script), embedded
#### Justify:
- Since the testing method focus on the logic of the application. I believe the test is used for more backend applications than front-end
### E. Reference:
- Data Flow Testing, retrieved from [https://www.geeksforgeeks.org/data-flow-testing/](https://www.geeksforgeeks.org/data-flow-testing/) (4)

<hr>

## 3. Model-Based Testing
### A. Introduction:
- Model-based testing is about automatically generating test procedures from models. (5)
- Model-based testing (MBT) can be applied to the software internal development process, and it can also be automated and built-in. (5)
- Model-based testing is a powerful technique that adds a systematic methodology to traditional techniques. 
### B. Example/Explain:
#### Automate UI testing with PyAutoGUI in Python:
- A case study from Microsoft "Chat System" (5), a system requirement for model-based testing
```
R1. Users must receive a response for a logon request.
R2. Users must receive a response for a logoff request.
R3. Users must receive a response for a list request.
R4. List response must contain the list of logged-on users.
R5. All logged-on users must receive a broadcast message.
R6. Messages from one sender must be received in order.
```
- These are the default action declarations, whereas the “event” keyword is used to declare an event action. code below show what this looks like in the chat system.
```csharp
// Cord code
config ChatConfig
{
  action void LogonRequest(int user);
  action event void LogonResponse(int user);
  action void LogoffRequest(int user);
  action event void LogoffResponse(int user);
  action void ListRequest(int user);
  action event void ListResponse(int user, Set<int> userList);
  action void BroadcastRequest(int senderUser, string message);
  action void BroadcastAck(int receiverUser, 
    int senderUser, string message);
  // ...
}
```
- Automated generate code to test each model
- The test-code generator is highly customizable and can be configured to generate test cases that target different test frameworks, such as NUnit.
```csharp
# test code generate by computer for model-base testing
#region Test Starting in S0
[Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute()]
public void TestSuiteS0() {
  this.Manager.BeginTest("TestSuiteS0");
  this.Manager.Comment("reaching state \'S0\'");
  this.Manager.Comment("executing step \'call LogonRequest(2)\'");
  Chat.Adapter.ChatAdapter.LogonRequest(2);
  this.Manager.Comment("reaching state \'S1\'");
  this.Manager.Comment("checking step \'return LogonRequest\'");
  this.Manager.Comment("reaching state \'S4\'");
  // ...
    }
```
### C. Advantages/Disadvantage:
#### Advantage:
- After the testable model is completed, model-based tests can cover an incredibly large variety of scenarios with relatively little effort.
- Since the model has to be formalized to enable auto-generate test, this enables early detection of requirement inconsistencies and helps teams to be in accord in terms of expected behavior
- Low maintenance cost
- Different members of a team can work on different tasks concurrently
- The MBT process can find design and specification errors quickly (6)

#### Disadvantage:
- A mindset adjustment is often required (learning curve). 
- Take time to learn before applying (automated + model-based testing): for developers integrating testing knowledge, and for testers learning how modeling relates to testing
- Took more time to develop the first test case
- If there is a large random test, MBT requires a great deal of infrastructure (many machines), a great deal of time (measured in hours to days for high coverage) or both (6)

### D. Applications:
#### Kind of applications:
- Models can be used to represent the desired behavior of a system under test (SUT) or to represent testing strategies and a test environment. 
- Model base can also use for embedded software systems, back-end applications

#### Justify:
- Model-based testing design to test the model and system under test. 
- Since the testing method focus on the logic of the application. I believe the test is used for more backend applications than front-end

### E. Reference:
- [Model Based Testing - An Introduction to Model-Based Testing and Spec Explorer](https://docs.microsoft.com/en-us/archive/msdn-magazine/2013/december/model-based-testing-an-introduction-to-model-based-testing-and-spec-explorer) (5)
- [Model Based Testing ](https://searchsoftwarequality.techtarget.com/definition/model-based-testing#:~:text=Advantages%20and%20disadvantages%20of%20model-based%20testing%20Advantages%20to,problems%20that%20would%20not%20be%20revealed%20up%20front.) (6)

<hr>

## 4. Mutation Testing
### A. Introduction:
- Mutation testing is a structural testing technique, which uses the structure of the code to guide the testing process. It can be described as the process of rewriting the source code in small ways to remove the redundancies in the source code
- There are 3 types: value mutation, decision mutations, statement mutations
- Mutation testing are widely use in unit test
### B. Example/Explain:
- Example of value mutation
```python
# Initial Code:
# Python

mod = 1000000007
a = 12345678
b = 98765432
c = (a + b) % mod

# Changed Code:

mod = 1007
a = 12345678
b = 98765432
c = (a + b) % mod
```

### C. Advantages/Disadvantage
#### Advantage:
- Brings a good level of error detection in the program.
- Discovering ambiguities in the source code.
- Delivering the most established and dependable structure for the clients

#### Disadvantage:
- Highly costly and time-consuming.
- Not able for Black Box Testing (modification in the source code).
- Testing requires the automation tools to test the application

### D. Applications: 
#### Kind of applications:
- typically used to conduct unit tests
- can be used for web app, desktop app, embeded system, mobile app

#### Justify:
- Mutation testing is usually used in unit test and we can use unit test for both front and back end to test the functionality of a unit (7)

### E. Reference:
- [Software Testing: Mutation Testing](https://www.geeksforgeeks.org/software-testing-mutation-testing/) (7)

<hr>

## 5. User Interface(UI)Testing
### A. Introduction:
- GUI Testing is the method of testing the graphic user interface (GUI) of a system 
are meet the system's requirements (functional and non-functional).
- Key element of UI testing:
  + Design must be inconsistent (e.g.: header and footer are the same through multiple pages)
  + Do not overuse any element (e.g.: color, font…)
  + Lack of text hierarchy
  + Unaligned element
  + Bad design structure
  + Using Low images
  + Bad render of different screen-size


### B. Example/Explain:
#### Automated UI Testing using PyAutoGUI
- Using the PyAutoGUI package, we can conduct regression UI testing on the target (regression testing + UI testing).
- The PyAutoGUI will allow us to carry out automated UI testing: it works across Windows, macOS X, and Linux which provides the ability to simulate mouse cursor moves and clicks as well as keyboard button presses.
- Code example retrieved from (1) and written in Python: the code will test if Firefox is working properly
  (open a new tab, open a website, type in a website...). We can store the script and execute it as many times as we want
```python
import pyautogui as gui, time
def testfirefox():
    screenWidth, screenHeight = gui.size()
    gui.moveTo(0,screenHeight)
    gui.click()
    gui.typewrite('Firefox', interval=0.25)
    gui.press('enter')
    time.sleep(2)
    gui.keyDown('alt')
    gui.press(' ')
    gui.press('x')
    gui.keyUp('alt')
    gui.click(250,22)
    gui.click(371,51)
    gui.typewrite('https://medium.com/financeexplained')
    gui.press('enter')
def identifyloc():
    while True:
        currentMouseX, currentMouseY = gui.position()
        print(currentMouseX,currentMouseY)
        time.sleep(3)
testfirefox()
```
Once the above code has been executed, the os can search for Firefox and then launch the website. 
We can write more code to test (button, link, functionality...) depending on our test plan.
#### Manually Testing:
- We can also manually click on buttons and links to test it manually: costly

#### Explain the importance of UI Testing:
- GUI Testing is very important. A good user interface can help a website make more clients while 
bad website design can lose their customer.
- Example: Returning a hp product on hp.com is too hard so I will never come and purchase their product.

### C. Advantages/Disadvantage
#### Advantage: 
- Testing the functionality of the GUI (button, hyperlink)
#### Disadvantage:
- can be costly due to User Experience (UX) tests reply on humans
- can't test the non-functionality (if website attracts user, ...)
- Not have a clear framework to implement User Experience Testing (UX)

### D. Applications:
#### Kind of applications: 
- web clients and/or server (web applications, web pages, webserver)
- desktop applications
#### <b>Justify:</b>
- GUI Testing is testing on the interaction between users and an application with GUI. Therefore, the
the task will focus on making sure if the button, the link is working and the color frame of the application 
is suitable for the applications.

### E. Reference
- Costas Andreous (2019) Automate UI Testing with PyAutoGUI in Python: A quick and easy way 
to regression test your UIs https://towardsdatascience.com/automate-ui-testing-with-pyautogui-in-Python-4a3762121973 (1)

<hr>

## 6. Integration Testing

### A. Introduction:
- Integration testing is the testing of various modules of the software under development together as a group. 
This determines whether or not they function together seamlessly as part of the system or whole. There are 2 types:
  + Big Bang Approach
  + Incremental Approach: which is further divided into the following: 
   Top Down Approach, Bottom Up Approach, Sandwich Approach – Combination of Top Down and Bottom Up
### B. Example/Explain:
- Integration testing is done on groups of these modules to make sure they work together and interact properly. While unit testing is one of the earliest tests performed in a project, integration testing is usually done later in the project timeline.
- Individual model may work well in unit test, but wont work when put together with other units. I experience this before.
Therefore, automated integration tests greatly increase the likelihood that bugs will be found as soon as possible during development so they can be addressed immediately.

### C. Advantages/Disadvantage
#### Advantage:
- Successful integration of modules: Most projects are big enough that development is broken down into numerous parts or modules. Integration testing verifies that all the parts communicate well and work together to achieve the purpose of the software.
- Data integrity: verify and validate data is not change or corruption when data move from 1 module to another
- User-based scenarios. One of the most important reasons to conduct integration tests is to create critical user-based scenarios and make sure they play out correctly. Individual components of the software will need to communicate properly when grouped, adapting and responding to multiple possible results. (8)
- Third-party testing. Integration testing also verifies that groups of modules or units of coding interact properly with Application Programming Interface (API) tools.
- (8)
#### Disadvantage:
- Test cases need to be prepared and testing data created
- A test environment must be set up (cost)
- Unit testing must have been completed already (can't begin test early).
- Greater difficulty in locating faults.
- Potential for overlooking a component.
- Critical, high-level components are tested last.
- (8)

### D. Applications:
#### Kind of applications:
- web app, desktop app, embeded system, mobile app
#### Justify:
- the intergration between a database, API, procedures, back end and front on most system must be test to ensure they work together without fault. 
### E. Reference:
- [What is Integration Testing](https://www.codecademy.com/resources/blog/what-is-integration-testing/) (8)

<hr>

## 7. Grammar-based testing
### A. Introduction:
- Grammar testing is discussed in the context of grammar engineering (i.e., software engineering for grammar). 
Grammar recovery is concerned with the derivation of a language's grammar from some available resources such as a semi-formal language reference.
- Several programs (like parsers, interpreters, and compilers) that work on structured input can be tested using grammar. 
These applications process their input in different stages like tokenizing, building parse tree, converting to AST and 
evaluating the AST. The simplest way to provide specify the input is in form of context-free grammar (10).
- A context-free grammar or CFG is a set of recursive rewriting rules (also called productions) used to generate 
patterns of strings. 
- 
### B. Example/Explain:
#### Example from (10)
- GramTest: a tool for grammar-based test case generation.
- The key aspect of the grammar-based test case generation algorithm in Gramtest is 
to follow all the production rules of the given BNF grammar and then generate strings 
that conform to the grammar. The production rules themselves form a tree, the root of 
the tree is the starting rule for generating all the strings in the grammar. 
- For example, consider the following BNF grammar describing all the course codes at a university:
```bash
<coursecode>   ::= <acadunit> <coursenumber>
<acadunit>     ::= <letter> <letter> <letter>
<coursenumber> ::= <year> <semesters> <digit> <digit>
<year>         ::= <ugrad> | <grad>
<ugrad>        ::= 0 | 1 | 2 | 3 | 4
<grad>         ::= 5 | 6 | 7 | 9
<semesters>    ::= <onesemester> | <twosemesters>
<onesemester>  ::= <frenchone> | <englishone> | <bilingual>
<frenchone>    ::= 5 | 7
<englishone>   ::= 1 | 3
<bilingual>    ::= 9
<twosemesters> ::= <frenchtwo> | <englishtwo>
<frenchtwo>    ::= 6 | 8
<englishtwo>   ::= 2 | 4
<digit>        ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
<letter>       ::= A | B | C | D | E | F | G | H | I | J | K | L | M | N |
                   O | P | Q | R | S | T | U | V | W | X | Y | Z
```
- Explain:
  - In this grammar the root is:
  ```bash
  <coursecode> ::= <acadunit> <coursenumber>
  ```
  - rule is starting from the root to the terminal
  - when we reach the terminal, we generating a corresponding string (only for that terminal)
  - when we run Gramtest on this input it generates the following strings
  ```bash
  Truc-Huynh:target truchuynh$ 
  java -jar gramtest-0.1-SNAPSHOT-jar-with-dependencies.jar
  -file ../src/test/resources/coursecodes.bnf
  ``` 
  - output
  ```bash
  Generating tests ...
  ZZX0989
  ZZW0989
  ZZW0988
  ZZV0988
  ZZV0987
  ZZU0987
  ZZU0986
  ZZT0986
  ZZT0985
  ZZS0985
  ZZS0984
  ZZR0984
  ZZR0983
  ZZQ0983
  ZZQ0982
  ZZP0982
  ZZP0981
  ...
  ```
  - Save all the test cases in the "generated-tests" folder.
  ```bash
  Truc-Huynh:target truchuynh$ ls generated-tests/
  1.txt    17.txt    25.txt    33.txt    41.txt    5.txt    58.txt    66.txt    74.txt    82.txt    90.txt    99.txt
  10.txt    18.txt    26.txt    34.txt    42.txt    50.txt    59.txt    67.txt    75.txt    83.txt    91.txt
  100.txt    19.txt    27.txt    35.txt    43.txt    51.txt    6.txt    68.txt    76.txt    84.txt    92.txt
  11.txt    2.txt    28.txt    36.txt    44.txt    52.txt    60.txt    69.txt    77.txt    85.txt    93.txt
  ...
  ```
### C. Advantages/Disadvantage
#### Advantage:
- automate the testing process
- Makes it possible to express and validate structured textual data
- Combine with auto mation testing to create automated fuzzing and testing 
(for example: Gramtest allows you to generate test cases based on arbitrary user defined grammars)
#### Disadvantage:
- A mindset adjustment is often required (learning curve). 
- Take time to learn before applying
  (10)
### D. Applications:
#### Kind of applications:
- parsers, interpreters, and compilers
- profilers, slicing tools, pretty printers, (re-) documentation tools, language reference manuals, browsers and IDEs, software analysis tools...
#### Justify:
- For such applications, due to a large number of control flow paths in the early processing, random 
fuzzing does not yield good test cases. Generating tests that exploit the structured nature of the input can provide 
better results. (10)

### E. Reference:
[GramTest: a tool for grammar-based test case generation](https://srcclr.github.io/test-lean/chapters/13-grammar.html) (10)
[How does grammar-based test case generation work?](https://www.veracode.com/blog/managing-appsec/how-does-grammar-based-test-case-generation-work)

<hr>

## 8. Regression Testing
### A. Introduction:
- Regression testing is a software testing method that is re-run to ensure that a software update does not affect the product's current functioning.
- Regression Testing run the previous test case on the existing application
- There are 3 types of regression testing:
  - Retest all
  - Regression Test
  - Prioritization of Test Cases
### B. Example/Explain:
#### Personal experience:
- Testing the functionality of the whole application after each update is necessary. Sometimes, I experience
apply a patch to software or update dependency then my apps don't work properly. Then, I have to roll back to the
previous version to make the app work (reverse).
- My method of regression is storing the script of each test suite and executing them in order. Regression testing is extremely important and should be treated with high priority.
#### test — Regression tests package for Python
- The test package contains all regression tests for Python as well as the modules test.support and test.regrtest. test.support is used to enhance your tests while test.regrtest drives the testing suite.
- basic boilerplate is often used:
```python
import unittest
from test import support

class MyTestCase1(unittest.TestCase):

    # Only use setUp() and tearDown() if necessary

    def setUp(self):
        ... code to execute in preparation for tests ...

    def tearDown(self):
        ... code to execute to clean up after tests ...

    def test_feature_one(self):
        # Test feature one.
        ... testing code ...

    def test_feature_two(self):
        # Test feature two.
        ... testing code ...

    ... more test methods ...

class MyTestCase2(unittest.TestCase):
    ... same structure as MyTestCase1 ...

... more test classes ...

if __name__ == '__main__':
    unittest.main()
```

### C. Advantages/Disadvantage
#### Advantage:
- Make sure the application runs smooth and function right after each update
- when a new feature is added to the software application and for defect fixing as well as performance issue fixing
- Regression is necessary to locate issues that have arisen as a result of a code modification
- Ensure that the modification hasn't impacted anything that was previously functioning.
#### Disadvantage:
- Test case can be time-consuming & cost consuming since we have to test the whole system again at every update
- Minimize test suite while achieving maximize test coverage can be a big problems

### D. Applications:
#### Kind of applications:
- Any applications (web, desktop, embedded, mobile)
#### Justify:
- It is always good to test the functionality of any applications after an update. I experience this.
### E. Reference:
[What is Regression Testing?](https://www.guru99.com/regression-testing.html) (11)
[test — Regression tests package for Python](https://docs.Python.org/3/library/test.html#:~:text=The%20test%20package%20can%20be%20run%20as%20a,running%20all%20regression%20tests%20in%20the%20test%20package.)


<hr>

## 9. Stress Testing
### A. Introduction:
### B. Example/Explain:
#### Example
```
```
### C. Advantages/Disadvantage
#### Advantage:
#### Disadvantage:
### D. Applications:
#### Kind of applications:
#### Justify:
### E. Reference:

<hr>

## 10. Performance Testing
### A. Introduction:
### B. Example/Explain:
#### Example
```
```
### C. Advantages/Disadvantage
#### Advantage:
#### Disadvantage:
### D. Applications:
#### Kind of applications:
#### Justify:
### E. Reference:

<hr>

