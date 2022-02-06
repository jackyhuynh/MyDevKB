# Testing Tools

## Ethical Hacking
- penetration testing
- cybersecurity methods


## Example:
### Introduction:
- GUI Tets
### Example/Explain:
#### Automate UI testing with PyAutoGUI in Python:
- Using the PyAutoGUI
```
```
### Pro/Con
#### Advantage:
#### Disadvantage:
### Applications use the testing technique 
#### <b>kind of applications:</b>
#### <b>justify:</b>
### Reference:

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
- Test maintenance is costly in the case of playback methods (in the situation when we change the graphic user interface)

### Applications use the testing technique 
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
- [Beautiful Soup python](https://beautiful-soup-4.readthedocs.io/en/latest/)

## 2. Data flow Testing


## 3. Model-Based Testing


## 4. Mutation Testing


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

## 6. Integration Testing


## 7. Grammar-based testing


## 8. Regression Testing


## 9. Stress Testing


## 10. Performance Testing


