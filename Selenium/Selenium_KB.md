## Proxy Auth

driver.get("http://UserName:Password@Example.com");

FirefoxProfile myprofile = profile.getProfile("profileToolsQA");
 
WebDriver driver = new FirefoxDriver(myprofile);

## Desired Capabilities

### Firefox

    System.setProperty("webdriver.gecko.driver", "D:\\\\ToolsQA\\trunk\\Library\\drivers\\geckodriver.exe");
    
    DesiredCapabilities capabilities = DesiredCapabilities.firefox();
    capabilities.setCapability("marionette", true);
    WebDriver driver = new FirefoxDriver(capabilities);

### Chrome

    System.setProperty("webdriver.chrome.driver", "C:\\Users\\abc\\Desktop\\Server\\chromedriver.exe");
    WebDriver driver = new ChromeDriver();
 
### Safari
// Set Safari browser extension

// Then:
    
    WebDriver driver = new SafariDriver();

### IE
    
    String service = "D:\\ToolsQA\\trunk\\Library\\drivers\\IEDriverServer.exe";
    System.setProperty("webdriver.ie.driver", service);
    
    InternetExplorerDriver  driver = new InternetExplorerDriver();

#### SendKeys Slowness on IE Browser
Simply replace the current IEDriverServer.exe(if your machine is 64-bit machine) with IEDriverServer.exe of 32 bit
    
#### SSL
    driver.navigate().to("javascript:document.getElementById('overridelink').click()");  

OR

    DesiredCapabilities capabilities = DesiredCapabilities.internetExplorer();
    capabilities.setCapability(CapabilityType.ACCEPT_SSL_CERTS, true);
    InternetExplorerDriver driver = new InternetExplorerDriver(capabilities); 

## Commands

### Browser Commands

    String driverExecutablePath = "D:\\Drivers\\chromedriver.exe";
    System.setProperty("webdriver.chrome.driver", driverExecutablePath);
    // Create a new instance of the FireFox driver 
    WebDriver driver = new ChromeDriver(); 
     
    String appUrl = "http://www.DemoQA.com";
    driver.get(appUrl);
    driver.manage().window().maximize();
    
    driver.getTitle();
    int titleLength = driver.getTitle().length(); 
    
    driver.getCurrentUrl();
    
    driver.getPageSource();
    int pageSourceLength = pageSource.length(); 
    
    driver.close(); -> Close current window
    driver.quit(); -> Close all windows

### Navigate Commands

    driver.navigate().to(appUrl);
    driver.navigate().forward();
    driver.navigate().back();
    driver.navigate().refresh();
    driver.close();

### Find WebElements

    driver.findElement(By.id("submit"));
    driver.findElement(By.name("firstname"));
    driver.findElement(By.className("button"));
    driver.findElement(By.tagName("button"));
    driver.findElement(By.linkText("Partial Link Test"));
    driver.findElement(By.partialLinkText("Partial");
    driver.findElements(By.xpath("//a"))

findElement()
- On Zero Match: throws NoSuchElementException
- On One Match: returns WebElement
- On One+ Match: returns the first appearance in DOM 

findElements()
- On Zero Match: return an empty list
- On One Match: returns list of one WebElement only
- On One+ Match: returns list with all matching instance

### WebElement Commands

//INPUT and TEXTAREA 

    element.clear();
    driver.findElement(By.id("UserName")).sendKeys("ToolsQA");

Div, Link and Button, or any element

    driver.findElement(By.linkText("ToolsQA")).click();
    boolean staus = driver.findElement(By.id("UserName")).isDisplayed();
    driver.findElement(By.id("userName")).isEnabled();
    boolean staus = driver.findElement(By.id("Sex-Male")).isSelected();

    submit( ) : void– This method works well/better than the click() if the current element is a form, or an element within a form. This accepts nothing as a parameter and returns nothing.
    If this causes the current page to change, then this method will wait until the new page is loaded.
    
    WebElement element = driver.findElement(By.id("SubmitButton")).submit();
    String linkText = element.getText();
    String tagName = element.getTagName();
    element.getCssValue();
    
    getAttribute(String Name) : String– This method gets the value of the given attribute of the element. This accepts the String as a parameter and returns a String value.
    String attValue = element.getAttribute("id");
    
    getSize( ) : Dimension – This method fetch the width and height of the rendered element. This accepts nothing as a parameter but returns the Dimension object.
    Dimension dimensions = element.getSize();
    System.out.println(“Height :” + dimensions.height + ”Width : "+ dimensions.width);
    
    getLocation( ) : Point
    Point point = element.getLocation();
    System.out.println("X cordinate : " + point.x + "Y cordinate: " + point.y);
    
    int totalLinkSize1 = driver.findElements(By.tagName("a")).size();
    int totalLinkSize2 = driver.findElements(By.xpath("//a")).size();

Radio Button

     List  oRadioButton = driver.findElements(By.name("toolsqa"));
     boolean bValue = false; 
     bValue = oRadioButton.get(0).isSelected();
     if(bValue = true){
        oRadioButton.get(1).click();
     }else{
        oRadioButton.get(0).click();
     }


    List oCheckBox = driver.findElements(By.name("tool"));
    // This will tell you the number of checkboxes are present
    int iSize = oCheckBox.size();
    // Start the loop from first checkbox to last checkboxe
    for(int i=0; i < iSize ; i++ ){
        // Store the checkbox name to the string variable, using 'Value' attribute
        String sValue = oCheckBox.get(i).getAttribute("value");
        // Select the checkbox it the value of the checkbox is same what you are looking for
        if (sValue.equalsIgnoreCase("toolsqa")){
            oCheckBox.get(i).click();
            // This will take the execution out of for loop
            break;
        }
    }

    WebElement oCheckBox = driver.findElement(By.cssSelector("input[value='Tools QA']"));

DROP DOWN Select Lists
    
    import org.openqa.selenium.support.ui.Select
    
    Select oSelect = new Select(driver.findElement(By.id("Country")));
    oSelect.selectByVisibleText("2010");
    oSelect.selectByIndex(4);
    oSelect.selectByValue("2014");
    oSelect.deselectAll();
    oSelect.deselectByIndex(int arg0);
    deselectByValue(String arg0)
    deselectByVisibleText(String arg0)
    
    oSelect.isMultiple();
    
    List <WebElement> elementCount = oSelect.getOptions();
    int iSize = elementCount.size();
    
    for(int i =0; i<iSize ; i++){
        String sValue = elementCount.get(i).getText();
        System.out.println(sValue);
    }
    

Wait Commands

implicit waits

    driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);     
    driver.get("http://url_that_delays_loading");

ExpectedConditions

    WebDriverWait wait = new WebDriverWait(driver, 10);
    WebElement element = wait.until(ExpectedConditions.elementToBeClickable(By.id(>someid>)));


FluentWait

    Wait wait = new FluentWait(driver)
    .withTimeout(30, SECONDS) 
    .pollingEvery(5, SECONDS) 
    .ignoring(NoSuchElementException.class);
 
    WebElement foo = wait.until(new Function() { 
        public WebElement apply(WebDriver driver) { 
            return driver.findElement(By.id("foo")); 
        } 
    });

OR

    // To return Boolean from Fluent Wait

     FluentWait<WebDriver> wait = new FluentWait<WebDriver>(driver);
     wait.pollingEvery(250,  TimeUnit.MILLISECONDS);
     wait.withTimeout(2, TimeUnit.SECONDS);
     
     Function<WebDriver, Boolean> function = new Function<WebDriver, Boolean>()
     {
         public Boolean apply(WebDriver arg0) {
             WebElement element = arg0.findElement(By.id("colorVar"));
             String color = element.getAttribute("color");
             
             if(color.equals("red"))
             {
             return true;
             }
             return false;
         }
     };
    
    wait.until(function);

OR

    // To return WebElement or Null from Fluent Wait

    FluentWait<WebDriver> wait = new FluentWait<WebDriver>(driver);
    wait.pollingEvery(250,  TimeUnit.MILLISECONDS);
    wait.withTimeout(2, TimeUnit.MINUTES);
    wait.ignoring(NoSuchElementException.class); //make sure that this exception is ignored
    
    Function<WebDriver, WebElement> function = new Function<WebDriver, WebElement>()
    {
        public WebElement apply(WebDriver arg0)
        {
            System.out.println("Checking for the element!!");
            WebElement element = arg0.findElement(By.id("target"));
            if(element != null)
            {
                System.out.println("Target element found");
            }
        return element;
        }
    };
    
    wait.until(function);
    }

PREDICATE

    https://www.toolsqa.com/selenium-webdriver/advance-webdriver-waits/

PageLoadTimeout

    driver.manage().timeouts().pageLoadTimeout(100, SECONDS);

SetScriptTimeout

    driver.manage().timeouts().setScriptTimeout(100,SECONDS);

Sleep Command

    thread.sleep(1000);

## Custom JS Waits - https://www.toolsqa.com/selenium-cucumber-framework/handle-ajax-call-using-javascriptexecutor-in-selenium/

    private static void until(WebDriver driver, Function<WebDriver, Boolean> waitCondition, Long timeoutInSeconds){
        WebDriverWait webDriverWait = new WebDriverWait(driver, timeoutInSeconds);
        webDriverWait.withTimeout(timeoutInSeconds, TimeUnit.SECONDS);
        try{
            webDriverWait.until(waitCondition);
        }catch (Exception e){
            System.out.println(e.getMessage());
        }          
    }

    // Wait for Ajax call to finish

     public static void untilPageLoadComplete(WebDriver driver, Long timeoutInSeconds){
         until(driver, (d) ->
             {
             Boolean isJqueryCallDone = (Boolean)((JavascriptExecutor) driver).executeScript("return jQuery.active==0");
             
             if (!isJqueryCallDone)
                System.out.println("JQuery call is in Progress");
             
             return isJqueryCallDone;
         }, timeoutInSeconds);
     }

     // Wait for Page Load using JavaScriptExecutor in Selenium

     public static void untilPageLoadComplete(WebDriver driver, Long timeoutInSeconds){
         until(driver, (d) ->
         {
             Boolean isPageLoaded = (Boolean)((JavascriptExecutor) driver).executeScript("return document.readyState").equals("complete");
             if (!isPageLoaded)
             
                System.out.println("Document is loading");
            return isPageLoaded;
         }, timeoutInSeconds);
     }

## Window and iFrames and Alerts

    alert("This is a simple alert");

    String  handle= driver.getWindowHandle();
    Set<String> handle= driver.getWindowHandles();
    driver.switchTo().window("windowName");

### Simple Alert

if an alert is present on the webpage and you try to access any of the element in the underlying page you will get following exception:
UnhandledAlertException: Modal dialog present

    Alert simpleAlert = driver.switchTo().alert();
    String alertText = simpleAlert.getText();
    System.out.println("Alert text is " + alertText);
    simpleAlert.accept();
 
### Confirmation Alert

    var popuResult = confirm("Confirm pop up with OK and Cancel button");

    Alert confirmationAlert = driver.switchTo().alert();
    String alertText = confirmationAlert.getText();
    System.out.println("Alert text is " + alertText);
    confirmationAlert.dismiss();
		 
### Prompt Alert

    var person = prompt("Do you like toolsqa?", "Yes/No");

    Alert promptAlert  = driver.switchTo().alert();
    String alertText = promptAlert .getText();
    System.out.println("Alert text is " + alertText);
    //Send some text to the alert
    promptAlert .sendKeys("Accepting the alert");
    Thread.sleep(4000); //This sleep is not necessary, just for demonstration
    promptAlert .accept();

### iFrame

    //Switch back to the main window
    driver.switchTo().defaultContent();

    //Switch by Name
    driver.switchTo().frame("frameName");
    
    //Switch by Index
    driver.switchTo().frame(0);

    //Switch by frame ID
    driver.switchTo().frame("IF1");
    
    //Switch by WebElement
    WebElement iframeElement = driver.findElement(By.id("IF1"));
    driver.switchTo().frame(iframeElement);
     
    //By executing a java script
    JavascriptExecutor exe = (JavascriptExecutor) driver;
    Integer numberOfFrames = Integer.parseInt(exe.executeScript("return window.length").toString());
    System.out.println("Number of iframes on the page are " + numberOfFrames);
    
    //By finding all the web elements using iframe tag
    List<WebElement> iframeElements = driver.findElements(By.tagName("iframe"));
    System.out.println("The total number of iframes are " + iframeElements.size());

Once you switch to the frame, you can access the html elements that are inside the frame. Any attempt to access the elements which are inside iFrame without switching to that ifFrame will result in WebDriver exception.

    org.openqa.selenium.NoSuchElementException

if you are inside frame 0 you cannot switch to frame 1. Because frame 1 is not a part of frame 0, but its a part of main page. Any attempt to directly switch to frame 1 from frame 0 will give an exception. 

    org.openqa.selenium.NoSuchFrameException

    driver.switchTo().defaultContent();
    driver.switchTo().frame(1);
  
## Execute JavaScript

((JavascriptExecutor) driver).executeScript("arguments[0].click()", element);


## Page Factory

    [FindsBy(How = How.Id, Using = “username“)]
    private IWebElement UserName { get; set; }
    
    var homePage = new HomePage();
    PageFactory.InitElements(driver, homePage);

	PracticeFormPageObject pageObject = PageFactory.initElements(driver, PracticeFormPageObject.class);

## Action Class

performing complex user web interactions like double-click, right-click, etc. and it is the only choice for emulating Keyboard and Mouse interactions.

    import org.openqa.selenium.interactions.Actions; // Class for builder pattern
    import org.openqa.selenium.interactions.Action;  // Interface for single action
    
    Actions actions = new Actions(webdriver object);
    WebElement element = driver.findElement(By strategy to identify element);
    actions.keyDown(element, Keys.SHIFT);
    actions.sendKeys(“TextToBeConvertAndSendInUpperCase”);
    actions.keyUp(Keys.SHIFT);
    actions.perform();
    
    actions.keyDown(element,Keys.CONTROL)
    actions.keyUp(element,Keys.CONTROL)
    
    actions.keyDown(currentAddress, Keys.CONTROL).sendKeys(“a”).keyUp(Keys.CONTROL).perform();
    actions.keyDown(Keys.CONTROL).sendKeys(“c”).keyUp(Keys.CONTROL).perform();
    actions.keyDown(permanentAddress, Keys.CONTROL).sendKeys(“v”).keyUp(Keys.CONTROL).perform();
    
    
    OR
    
    Action action = actions.build();
    action.perform();

### Right Click
    actions.contextClick(webElement).perform(); 

### Double Click
    actions.doubleClick(btnElement).perform(); 

### Drag and Drop
    actions.dragAndDrop(sourceElement,targetElement).perform(); 
    actions.dragAndDropBy(source, xOffset, yOffset).perform(); 

### Mouse Movement
    actions.moveToElement(element).perform(); 
    actions.moveToElement(slider,50,0).perform();

## @CacheLookup

@CacheLookup, as the name suggests helps us control when to cache a WebElement and when not to. This annotation, when applied over a WebElement, instructs Selenium to keep a cache of the WebElement instead of searching for the WebElement every time from the WebPage. This helps us save a lot of time.

If we know that element is always present on the page, it is best to use the following declaration:

    [FindsBy(How = How.Id, Using = “account”)][CacheLookup]
    public IWebElement MyAccount { get; set; }

## Tooltip

Title for Text boxes and Buttons etc

    String tooltipText = webElement.getAttribute(“title”);
    
    or
    
    actions.moveToElement(element).perform(); 
    WebElement toolTip = driver.findElement(By.cssSelector(".tooltiptext")); 
    String toolTipText = toolTip.getText();

## Robot Class

For Windows pop-ups
Robot class is especially useful in managing file upload/download actions by interacting with OS pop-ups.
methods like mouseMove are dependent on screen resolution, so, the method may perform differently on different screens.

    import java.awt.Robot;
    
    Robot robot = new Robot();
    robot.<required_method>();
    
    robot.keyPress(KeyEvent.VK_SHIFT)
    robot.keyRelease(KeyEvent.VK_SHIFT)
    robot.mousePress(InputEvent.BUTTON1_DOWN_MASK)
    robot.mouseRelease(InputEvent.BUTTON1_DOWN_MASK)
    robot.mouseMove(100, 50)
    
    InputEvent.BUTTON1_DOWN_MASK :  For mouse left -click
    InputEvent.BUTTON2_DOWN_MASK  : For mouse middle button click
    InputEvent.BUTTON3_DOWN_MASK : For mouse right-click
    InputEvent.BUTTON1_MASK
    InputEvent.BUTTON2_MASK
    InputEvent.BUTTON3_MASK

## Web Locator Examples

    // Get all links on page
    java.util.List<WebElement> links = driver.findElements(By.tagName("a"));
    
    // Get all links on page
    java.util.List<WebElement> checkboxes = driver.findElements(By.xpath("//input[@type='checkbox']"));
    
    // Get all links on page
    java.util.List<WebElement> textboxes = driver.findElements(By.xpath("//input[@type='text'[@class='inputtext']"));


- XPath Locator -> View Example
- CSSSelector Locator -> View Example
- ClassName Locator -> View Example
- ID Locator -> View Example
- Name Locator -> View Example
- LinkText Locator -> View Example
- PartialLinkText Locator -> View Example
- TagName Locator -> View Example

TimeoutException - This exception will be thrown when command execution does not complete In given time.
NoSuchElementException - WebDriver software testing tool will throw this exception when element could not be found on page of software web application.
NoAlertPresentException - This exception will be generated when webdriver ties to switch to alert popup but there Is not any alert present on page.
ElementNotSelectableException - It will be thrown when webdriver Is trying to select unselectable element.
ElementNotVisibleException - Thrown when webdriver Is not able to Interact with element which Is available In DOM but It Is hidden.
StaleElementReferenceException



CSS Selectors



XPATH Selectors

A single slash at the start of Xpath instructs XPath engine to look for element starting from root node.

    /html/body/div[2]/div/div/footer/section[3]/div/ul/li[3]/a

A double slash at the start of Xpath instructs XPath engine to search look for matching element anywhere in the XML document.

    //*[@id=’social-media’]/ul/li[3]/a

build your xpath with using variables 
    
    driver.findElement(By.xpath("/html/body/div[1]/div[2]/div/div[2]/article/div/table/tbody/tr["+sRow+"]/td["+sCol+"]")).getText();
    
## Selenium Grid

    java -jar selenium-server-standalone-2.52.0.jar -port 4444 -role hub

    java -jar selenium-server-standalone-2.52.0.jar -role node -Dwebdriver.ie.driver="D:/IEDriverServer.exe" -Dwebdriver.chrome.driver="D:/chromedriver.exe" -hub http://localhost:4444/grid/register -port 5566

    java -jar selenium-server-standalone-2.52.0.jar -role node -Dwebdriver.ie.driver="D:/IEDriverServer.exe" -Dwebdriver.chrome.driver="D:/chromedriver.exe" -hub http://localhost:4444/grid/register -port 5566 -browser browserName=firefox,maxInstances=2 -browser browserName=chrome,maxInstances=2 -browser browserName=iexplore,maxInstances=2

    java -jar selenium-server-standalone-2.52.0.jar -role node -Dwebdriver.ie.driver="D:/IEDriverServer.exe" -Dwebdriver.chrome.driver="D:/chromedriver.exe" -hub http://localhost:4444/grid/register -port 5566 -browser browserName=firefox,maxInstances=2 -browser browserName=chrome,maxInstances=2 -browser browserName=iexplore,maxInstances=2 -maxSession 2  -timeout 20000



    
String

sValue.equalsIgnoreCase(sColValue)

