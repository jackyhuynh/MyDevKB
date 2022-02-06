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

