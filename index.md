### Welcome to Web Automation using Selenium
Selenium automates browsers, meaning it can mock user actions on browsers.
If you want to create robust, browser-based regression automation suites and tests, then you want to use Selenium (aka Selenium WebDriver); a collection of language specific bindings to drive a browser. It drives the browser directly using the browser’s built in support for automation.

To install Selenium means to set up a project in a development environment so you can write a program using Selenium. How you do this depends on your programming language and your development environment. The easiest way to set up a Selenium 2.0 Java project is to use Maven. Maven will download the java bindings (the Selenium 2.0 java client library) and all its dependencies, and will create the project for you, using a maven pom.xml (project configuration) file. Once you’ve done this, you can import the maven project into your preferred IDE, IntelliJ IDEA or Eclipse.

### Framework Design
Design patterns represent the best practices used by experienced object-oriented software developers. We will be using Page Object Model (POM, an object repository design pattern) to create Object Repository for Web UI elements. Under this model, every web page should have corresponding page class. And page class will have all web elements defined along with methods which perform operations on these web elements. 

Page Factory is an inbuilt page object model concept for Selenium WebDriver. It is an optimized way to create object repository in POM concept. In PageFactory, Annotations (e.g @FindBy) are used to give descriptive names for Web Elements to improve code readability. It also works on lazy loading concept, i.e when an operation is performed on an element the wait for its visibility starts from that moment, thus addressing test flakiness.


### Choosing different tools to use Selenium with Java  
Check what you need to install by typing console commands  
1) javac -version -> if it fails install java jdk  
2) mvn -version -> if it fails install maven  

3) An IDE, IntelliJ / Eclipse  
4) POM file with dependencies like selenium-java, maven-compiler-plugin(compiler plugin to configure java version for code compilation), maven-surefire-plugin(test runner/ report plugin), webdrivermanager(handles selenium webdriver binary management within a Java project in runtime) and testng(a testing framework)

### Teamcity / Maven Profiles

TeamCity is a Java-based build management and continuous integration server. We can create pipelines for our automation test suite for Smoke Tests, Functional Tests etc. Maven profiles can be used to create multiple pipelines pointing to the same pom.xml. It can be invoked like mvn test -P FunctionalTests where FunctionalTests will be one of the profile name

### Locators, Actions - few useful way of using locators/ methods

@FindBy(id = "journeySearchFindTrains")    
public WebElement btnFindTrains;  *Here we get access to an element  

@FindBys(@FindBy(className = "ticketType-title"))  
public List \<WebElement\> TicketTitles;  *Here we get access to a list  

@FindBy(xpath = "//li[contains(@class, 'journey-item') and contains(@class, 'journey-item--isSelected')]")   
public WebElement selectedJourney;    *Get a highlighted row by checking for the presence of multiple classes  

public void waitForHomePageLoad() throws InterruptedException {  
  (new WebDriverWait(driver, 10)).until(new ExpectedCondition<Boolean>() {  
    public Boolean apply(WebDriver d) {  
      return d.findElement(By.id("journeySearchFindTrains")).getText().equals("Find trains");  
    }  
 });  
}  *Explicitly waiting for 10 sec or until a page is loaded  


### Tests

