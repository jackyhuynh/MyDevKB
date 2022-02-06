# Testing Tools

## Ethical Hacking
- penetration testing
- cybersecurity methods

### Introduction:

### Example/Explain:
#### Example
```
```

### Pro/Con
#### Advantage:
#### Disadvantage:
### Applications:
#### <b>kind of applications:</b>
#### <b>justify:</b>
### Reference:

<hr>

## 1. Automation Testing:
- Using a set of commands that enable the system to continuous test the target system with the ability to record the result

### Introduction:

### Example/Explain:
#### Automate UI testing with PyAutoGUI in Python:
- In the GUI Tets (section number 6) I demonstrate the automated testing using the PyAutoGUI package
#### Automate UI testing with Selenium and Beautiful Soup in Python:
- we can also be using [Selenium](https://selenium-python.readthedocs.io/), and [Beautiful Soup 4](https://beautiful-soup-4.readthedocs.io/en/latest/) to perform autonomous test tasks
- I use Selenium and Beautiful Soup for web scrapping and generating data for reports and research... 
The purpose is different, but I realize I can use those packages for finding specific elements (container, images link, button, data ...)
. Then assign tasks (click, keyboard enter) that Selenium allows us to do. Finally, store the script and schedule an appropriate execution time
#### Automate UI testing with Selenium and Unittest in Python:
- Unittest is inherited from the PyUnit, Python Unittest package has 5 components: Test loader, test case, test suite, test runner, and test report 
- code demonstrate of using Unittest and Selenium to test if an image link is clickable
- the script using selenium web driver and Unittest.TestCase to perform a couple of autonomous tasks: test the search box, test image link, test language setting, and test if some element is present
- code retrieved from (2)
```
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
### Pro/Con
#### Advantage:
- Reliable: eliminating human error
- Repeatable: test the software under repeated execution of the same operations
- Cost reduction: more tests with less human resources
- reusable: test design one and run at every development step

#### Disadvantage:
- Proficiency is required to write the automation test scripts.
- Debugging the test script is a major issue.
- Test maintenance is costly in the case of playback methods (in the situation when we change the graphic user interface) (3)

### Applications use the testing technique: 
#### <b>kind of applications:</b>
- Automated testing can be performed on any system: embedded system, web app, desktop app 
- On any ongoing development application 
- On integration testing step(test as we go)
- Can also test on the stable version just to make sure no unexpected incident has happened
#### <b>justify:</b>
Since automated testing is not costly (designed one and reuse every time). It can be used at every development miles stone 
to make sure the overall development is working well.
### Reference:
- [Build A Selenium Python Test Suite From Scratch Using Unittest](https://www.techbeamers.com/selenium-python-test-suite-unittest/#:~:text=Selenium%20Python%20Unittest%20Framework%20Test%20Loader%20%E2%80%93%20It%E2%80%99s,TestSuite%20object%20that%20carries%20those%20cases%20and%20suites.) (2)
- [Beautiful Soup python](https://beautiful-soup-4.readthedocs.io/en/latest/) (3)

<hr>

## 2. Data flow Testing

### Introduction:
- Data Flow testing follows the flow of the application ()control flow graph and focuses on the points at which variables receive values and the points at which these values are used.

### Example/Explain:
- Using Tkinter package (for Local drawing), and pycfg.py (automate CFG task). 
CFG helps us find independent paths (Cyclomatic Complexity), which leads to the number of test cases required to test the program
- The script simply a while loop
- whiletest.py content
```
# whiletest.py
a= 10
while(a <= 0):
    if a == 5:
        print(a)
    a += 1
print("exited")
```
- put the 2 files in the same folder or we can navigate them 
```
python path_to/pycfg.py path_to/whiletest.py -d
```
- run this script to test the 'whiletest.py' control flow
```
from pycfg.pycfg import PyCFG, CFGNode, slurp
import argparse
import tkinter as tk
from PIL import ImageTk, Image

if __name__ == '__main__':
   parser = argparse.ArgumentParser()
    
    # replace 'pythonfile' with 'whiletest.py'
   parser.add_argument('pythonfile', help ='The python file to be analyzed')
   args = parser.parse_args()
   arcs = []

   cfg = PyCFG()
   cfg.gen_cfg(slurp(args.pythonfile).strip())
   g = CFGNode.to_graph(arcs)
   g.draw(args.pythonfile + '.png', prog ='dot')

   # Draw using tkinter.
   root = tk.Tk()
   root.title("Control Flow Graph")
   img1 = Image.open(str(args.pythonfile) + ".png") # PIL solution
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
### Pro/Con
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
- Drawing chart manually can create human-mistake -> confusing

### Applications use the testing technique 
#### <b>kind of applications:</b>
- Backend, logic application (command line, script), embedded
#### <b>justify:</b>
- Since the testing method focus on the logic of the application. I believe the test is used for more backend applications than front-end
### Reference:
- Data Flow Testing, retrieved from [https://www.geeksforgeeks.org/data-flow-testing/](https://www.geeksforgeeks.org/data-flow-testing/) (4)

<hr>

## 3. Model-Based Testing
### Introduction:
- Model-based testing is about automatically generating test procedures from models. (5)
- Model-based testing (MBT) can be applied to the software internal development process, and it can also be automated and built-in. (5)
- Model-based testing is a powerful technique that adds a systematic methodology to traditional techniques. 
### Example/Explain:
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
```
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
```
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
### Pro/Con:
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

### Applications:
#### <b>kind of applications:</b>
- Models can be used to represent the desired behavior of a system under test (SUT) or to represent testing strategies and a test environment. 
- Model base can also use for embedded software systems, back-end applications

#### <b>justify:</b>
- Model-based testing design to test the model and system under test. 
- Since the testing method focus on the logic of the application. I believe the test is used for more backend applications than front-end

### Reference:
- [Model Based Testing - An Introduction to Model-Based Testing and Spec Explorer](https://docs.microsoft.com/en-us/archive/msdn-magazine/2013/december/model-based-testing-an-introduction-to-model-based-testing-and-spec-explorer) (5)
- [Model Based Testing ](https://searchsoftwarequality.techtarget.com/definition/model-based-testing#:~:text=Advantages%20and%20disadvantages%20of%20model-based%20testing%20Advantages%20to,problems%20that%20would%20not%20be%20revealed%20up%20front.) (6)

<hr>

## 4. Mutation Testing
### Introduction:
- Mutation testing is a structural testing technique, which uses the structure of the code to guide the testing process. It can be described as the process of rewriting the source code in small ways to remove the redundancies in the source code
- There are 3 types: value mutation, decision mutations, statement mutations
- Mutation testing are widely use in unit test
### Example/Explain:
- Example of value mutation
```
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

### Pro/Con
#### Advantage:
- Brings a good level of error detection in the program.
- Discovering ambiguities in the source code.
- Delivering the most established and dependable structure for the clients

#### Disadvantage:
- Highly costly and time-consuming.
- Not able for Black Box Testing (modification in the source code).
- Testing requires the automation tools to test the application

### Applications use the testing technique 
#### <b>kind of applications:</b>
- typically used to conduct unit tests
- can be used for web app, desktop app, embeded system, mobile app

#### <b>justify:</b>
- Mutation testing is usually used in unit test and we can use unit test for both front and back end to test the functionality of a unit (7)

### Reference:
- [Software Testing: Mutation Testing](https://www.geeksforgeeks.org/software-testing-mutation-testing/) (7)



<hr>

## 5. User Interface(UI)Testing
### Introduction:
- GUI Testing is the method of testing the graphic user interface (GUI) of a system 
are meet the system's requirements (functional and non-functional).
- Key element of UI testing:
```
+ Design must be inconsistent (e.g.: header and footer are the same through multiple pages)
+ Do not overuse any element (e.g.: color, font…)
+ Lack of text hierarchy
+ Unaligned element
+ Bad design structure
+ Using Low images
+ Bad render of different screen-size
```

### Example/Explain:
#### Automated UI Testing using PyAutoGUI
- Using the PyAutoGUI package, we can conduct regression UI testing on the target (regression testing + UI testing).
- The PyAutoGUI will allow us to carry out automated UI testing: it works across Windows, macOS X, and Linux which provides the ability to simulate mouse cursor moves and clicks as well as keyboard button presses.
- Code example retrieved from (1) and written in Python: the code will test if Firefox is working properly
  (open a new tab, open a website, type in a website...). We can store the script and execute it as many times as we want
```
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

### Pro/Con
#### Advantage: 
- Testing the functionality of the GUI (button, hyperlink)
#### Disadvantage:
- can be costly due to User Experience (UX) tests reply on humans
- can't test the non-functionality (if website attracts user, ...)
- Not have a clear framework to implement User Experience Testing (UX)

### Applications use the testing technique:
#### <b>Kind of applications:</b> 
- web clients and/or server (web applications, web pages, webserver)
- desktop applications
#### <b>Justify</b>
- GUI Testing is testing on the interaction between users and an application with GUI. Therefore, the
the task will focus on making sure if the button, the link is working and the color frame of the application 
is suitable for the applications.

### References
- Costas Andreous (2019) Automate UI Testing with PyAutoGUI in Python: A quick and easy way 
to regression test your UIs https://towardsdatascience.com/automate-ui-testing-with-pyautogui-in-python-4a3762121973 (1)

<hr>

## 6. Integration Testing

### Introduction:
- Integration testing is the testing of various modules of the software under development together as a group. 
This determines whether or not they function together seamlessly as part of the system or whole. There are 2 types:
  + Big Bang Approach
  + Incremental Approach: which is further divided into the following: 
   Top Down Approach, Bottom Up Approach, Sandwich Approach – Combination of Top Down and Bottom Up
### Example/Explain:
- Integration testing is done on groups of these modules to make sure they work together and interact properly. While unit testing is one of the earliest tests performed in a project, integration testing is usually done later in the project timeline.
- Individual model may work well in unit test, but wont work when put together with other units. I experience this before.
Therefore, automated integration tests greatly increase the likelihood that bugs will be found as soon as possible during development so they can be addressed immediately.

### Pro/Con
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

### Applications:
#### <b>kind of applications:</b>
- web app, desktop app, embeded system, mobile app
#### <b>justify:</b>
- the intergration between a database, API, procedures, back end and front on most system must be test to ensure they work together without fault. 
### Reference:
- [What is Integration Testing](https://www.codecademy.com/resources/blog/what-is-integration-testing/) (8)

<hr>

## 7. Grammar-based testing

<hr>

## 8. Regression Testing

<hr>

## 9. Stress Testing

<hr>

## 10. Performance Testing

<hr>

