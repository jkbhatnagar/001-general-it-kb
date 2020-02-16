
---
Consider the following code snippet

    WebDriverWait wait = new WebDriverWait(driver, 30);
    wait.until(ExpectedConditions.presenceOfElementLocated(by));
This is an example of an implicit wait.

- [x] True
- [ ] False
---
In webdriver, which of the following is a valid select statement that selects a value from a drop down element?

- [ ] SelectByIndex()     
- [ ] SelectByVisibleText()  
- [ ] selectByValue()    
- [x] all above
- [ ] none of above  
---
In WebDriver, which command can be used to enter values onto text boxes? Select the best answer.

- [ ] type()     
- [ ] selenium.type()    
- [ ] driver.type("text")    
- [ ] sendKeys()     
- [x] sendKeys("text")
---
The following codes both print: "Welcome to TestingExcellence.com"

    System.out.println(driver.getTitle());
    System.out.println(driver.findElement(By.tagName(“title”)).getText())

- [x] True    
- [ ] False   
---
In webdriver, deselectAll() is a valid command.

- [x] True
- [ ] False
---
Which WebDriver method is used to change focus to an alert, a frame or a browser window?

- [ ] changeFocus()   
- [ ] setFocus()  
- [x] switchTo()
- [ ] changeTo()
---
In webdriver, which command takes you forward by one page on the browser’s history?

- [ ] navigate.forward()     
- [ ] Navigate.forward()     
- [x] navigate().forward()
- [ ] Navigate.forward
- [ ] navigate_forward()
---
Selenium IDE is supported by which browser?

- [ ] Internet Explorer      
- [x] Mozilla Firefox        
- [ ] Google Chrome      
- [ ] Safari     
- [ ] All Of Above       

---
Consider the following html snippet

- Firefox
- Google Chrome
- Internet Explorer
- Opera
- Safari

Which CSS selector is a valid statement to select Opera?

- [ ] css = li.contains("Opera")     
- [ ] css = ul.li(4)     
- [x] css = ul > li:nth-of-type(4)
- [ ] css = ul > li:nth-of-type(3)       
- [ ] css = ul.li:nth-child(4)       
---
In webdriver, which methods navigates to a URL?

- [ ] goToUrl("url")
- [ ] navigate.to("url")
- [ ] getUrl("url")
- [x] get("url")
---
In webdriver, what is the method that counts the number of elements?

- [ ] driver.getCountOfElements()    
- [ ] driver.findElement(By.id("search")).getCount()     
- [x] driver.findElements(By.id("search")).size()
- [ ] driver.findElements(By.id("search")).length()  
---
In webdriver, which of the following commands retrieves the text of a html element?

- [ ] selectText()   
- [x] getText()
- [ ] getElementText()   
- [ ] getText(WebElement)    
---
Consider the following HTML code snippet

1    |   2
---- | ----
3    |	 4
    driver.findElement(By.xpath(“//table/tr[1]/td”)).getText();

- [x] The above statement returns 1      
- [ ] The above statement returns 3
- [ ] The xpath query is incorrect       
- [ ] webdriver statement is incorrect       
--- 
What is the output of the following statement?

Name 1 (id='name')
Name 2 (class='name')

    driver.findElement(By.cssSelector(“#name”));

- [x] Output is Name 1
- [ ] Output is Name 2
- [ ] CSS selector syntax is incorrect
 
---
In webdriver, selectAllOptions() is a valid command.
 
- [ ] True
- [x] False
---
Implicit wait time is applied to all elements in your script and Explicit wait time is applied only for particular specified element.

- [x] True
- [ ] False
---
In webdriver, which method closes the open browser?

- [x] quit()     
- [ ] terminate()        
- [ ] shutdown()     
- [ ] close()        
---
To delete a cookie we need to call the deleteCookie method, passing in two parameters.Marks 1
- [ ] A) The first parameter is the name of the cookie, and the second parameter is where it was created.
- [ ] B) The first parameter is where it was created, and the second parameter is the name of cookie.
- [ ] C) None of these
- [ ] D) Time spent on the document outside the meeting

---
"echo():" is usedMarks 1
 A) to display the value of a variable in the log file, which can be very valuable for debugging
 B) Display the value of a variable named answer in the log file, what would the first argument to the previous command look like.
 C) Both of these
 D) None of these

---
Which is the odd one out?Marks 1
 A) ID
 B) Xpath
 C) CSS selector
 D) Pattern matching
---
Which is a procedure?Marks 1
 A) Wait
 B) Exit
 C) WaitForProperty
 D) None of these.
---
The // tells the query thatMarks 1
 A) It needs to stop at the first element that it finds.
 B) This is comment
 C) The path of the file or folder
 D) All of these
---
Which command should be used to confirm that test will pass in the future, when new element is added after page loaded?Marks 1
 A) waitForElementPresent
 B) pause
 C) assertElementPresent
 D) None of these
---
By Default time of WAITFOR command is :Marks 1
 A) 15 Sec
 B) 20 Sec
 C) 25 Sec
 D) 30 Sec
---
How to execute specific command?Marks 1
 A) Highlight a command. Press Ctrl + F9
 B) Highlight a command. Press Alt + F9.
 C) Highlight a command. Press Ctrl + X.
 D) Highlight a command. Press X.
---
In Selenium variables are stored in_____________Marks 1
 A) storedVars
 B) storedVariables
 C) VariablesStore
 D) All of the above
---
Variable can be saved in which format?Marks 1
 A) dollor{variableName}
 B) storedVars["variableName"].
 C) Both of these
 D) None of these
---
Which is the following is false in case of waitFor command?Marks 1
 A) waitForAlertPresent
 B) waitForTextPresent
 C) waitForFramePresent
 D) waitForPageToLoad
---
Selenium is compatible with….Marks 1
 A) CSS1.0 and CSS 2.0,
 B) CSS1.0, CSS 2.0, and CSS 3.0 selectors.
 C) CSS 2.0, and CSS 3.0 selectors.
 D) CSS1.0, CSS 2.0, CSS 3.0 and CSS 4.0 selectors
---
In Selenium, Following Axis is related to:Marks 1
 A) Selects all the siblings after the current element
 B) Selects all elements that follow the closing tab of the current elements
 C) Selects all of the siblings before the current element
 D) Selects all elements that are before the current element
---
If you wanted to access the element that has the text "This element has an ID that changes every time the page is loaded" in it, then which of the following is used?Marks 1
 A) //div[contains(@id,"time_")]
 B) //div[contains(@id_time())]
 C) //div[parameter(@id_time())]
 D) //div[parameter(@id,"time_")]
---
Applications do not have the items needed for the tests when the tests get to commands. To get around this, we had a look at adding from waitFor commands to test. This is related toMarks 1
 A) Debugging tests
 B) Working with AJAX applications
 C) Working with multiple windows
 D) All of these
---
Which command is used to extend the time limit of WAITFOR command?Marks 1
 A) Extend waitFor (time in sec)
 B) waitFor (time in sec) extend
 C) setTimeout (time in sec)
 D) setTimeout.
---
Which two commands you use to validate a button?Marks 1
 A) VerifyTextPresent and assertTextPresent
 B) VerifyElementPresent and assertElementPresent
 C) VerifyAlertPresent and assertAlertPresent
 D) VerifyAlert and assertAlert
---
Selects all the parent, grandparent, and so on of the element is related to which axis name in Selenium?Marks 1
 A) Ancestor
 B) Preceding
 C) Parent
 D) All of these.
---
Which is not true in case of Globs, in Selenium?Marks 1
 A) Globs are used as default pattern matching technique.
 B) It is similar to regular expressions.
 C) The syntax of Globs is much wider than Regular expression
 D) B and C
---

---

---

---

