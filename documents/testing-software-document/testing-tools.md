# Testing Tools

## Ethical Hacking
- peneration testing
- cypersecurity methods

## GUI Testing:
- Small different can make big different
- Test Link, Button, Color
- Poor touch: icon is too small
- Low image picture
- Test if the app is using ok on different screen (mobile, tablet, pc)(Look at UI test on )
- Content need to look good

## UI Test plan
### We need a testing life cycle plan
### A set of supporting tools: 
- [Build A Selenium Python Test Suite From Scratch Using Unittest](https://www.techbeamers.com/selenium-python-test-suite-unittest/#:~:text=Selenium%20Python%20Unittest%20Framework%20Test%20Loader%20%E2%80%93%20It%E2%80%99s,TestSuite%20object%20that%20carries%20those%20cases%20and%20suites.)
- Automation test
- [beautiful soup python](https://beautiful-soup-4.readthedocs.io/en/latest/)
- [selenium-ide](https://www.selenium.dev/selenium-ide/): selenium ide for automation testing
- Capture Replay Models


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
#### <b>kind of applications:</b> web/ embedded.etc.]
#### <b>justify:</b>
### Reference:





## 1. Automation Testing:
- Using a set of command 
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
#### <b>kind of applications:</b> web/ embedded.etc.] 
- automated testing can be use for any thing on embeded system, web app, desktop app 
- any on-going development application 
- intergration testing (test as we go)
- can also test on stable version just to make sure no unexpected incident is happen
#### <b>justify:</b>
### Reference:

## 2. Data flow Testing


## 3. Model Based Testing


## 4. Mutation Testing


## 5. User Interface(UI)Testing

### Introduction:
- GUI Testing is the method of testing the graphic user interface (GUI) of a system 
are meet the system's requrements (functional and non-functional).
- Key element of UI testing:
```
+ Design is inconsistent (header and footer are the same through multiple pages)
+ Do not overuse any element (drop shadow)
+ Lack of text hierachy
+ Unaligned element
+ Bad design structure
+ Using Low images
+ Bad render of different screen-size
```

### Example/Explain:
#### Automated UI Testing using PyAutoGUI
- Using the PyAutoGUI package, we can conduct regression UI testing on the target (regression tetsing + UI testing).
- The PyAutoGUI will allow us to carry out automated UI testing: it works across Windows, MacOS X and Linux which provides the ability to simulate mouse cursor moves and clicks as well as keyboard button presses.
- Code example retrieved from (1) and written in Python: the code will test if FireFox is working properly
  (open new tab, open a web site, type in a website...). We can store the script and execute as many time as we want
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
Once the above code has been executed, we can search for Firefox and then launch it.


#### Explain the importance of UI Testing:
- GUI Testing is very important. Good user interface can help a website make more clients while 
bad website design can lost their customer.
- Example: Returning a hp product on hp.com is too hard so that I will never come and purchase their product.
### Pro/Con
#### Advantage: 
- Testing the functionality of the GUI (button, hyperlink)
#### Disadvantage:
- can't test the non-functionality (if website attract user, ...)
- Not have a clearly framework to implement User Experience Testing (UX)
### Applications use the testing technique:
#### <b>Kind of applications:</b> 
- web clients and server (web applications, web pages, web server)
- desktop applications
#### <b>Justify</b>
- GUI Testing is testing on interaction between users and an application with GUI. Therefore, the
task will focus on making sure if the button, the link is working and the color frame of application 
is sutable for the purpose of the applications.
### References
- Costas Andreous (2019) Automate UI Testing with PyAutoGUI in Python: A quick and easy way 
to regression test your UIs https://towardsdatascience.com/automate-ui-testing-with-pyautogui-in-python-4a3762121973 (1)

## 6. Integration Testing


## 7. Grammar-based testing


## 8. Regression Testing


## 9. Stress Testing


## 10. Performance Testing

