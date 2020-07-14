## Create a coded test for web testing

TestProject supports C# and Java for coded test.
We are using java when we consider our expertise.
Coded test is based on SDK given by TestProject.
You can refer to the below link for details.

[Test Project Java SDK](https://docs.testproject.io/testproject-sdk/java-sdk)

### Test Class

In order to create a test that can be executed by TestProject, the class has to implement WebTest interface.
It has to implement execute() method. This method should return ExecutionResult.PASSED or ExecutionResult.FAILED as test result. This class's basic skeleton code is like below.

```java
public class BasicTest implements WebTest {

    public ExecutionResult execute(WebTestHelper helper) throws FailureException {
        // Get driver initialized by TestProject Agent
        // No need to specify browser type, it can be done later via UI
        WebDriver driver = helper.getDriver();

        // Navigate to TestProject Demo website
        driver.navigate().to("https://example.testproject.io/web/");

        // Example code for using Page Object Model
        // Login using provided credentials
        LoginPage loginPage = PageFactory.initElements(driver, LoginPage.class);
        loginPage.login(name, password);

        // Complete profile forms and save it
        ProfilePage profilePage = PageFactory.initElements(driver, ProfilePage.class);
        profilePage.updateProfile(country, address, email, phone);

        // return test result according to profile saving result.
        return profilePage.isSaved() ? ExecutionResult.PASSED : ExecutionResult.FAILED;
    }
}
```

### Test Project

![Project Structure](https://github.com/ocean-network-express/OTSK-TAS-RESOURCE/blob/master/images/Project%20Structure.PNG)


* **Project Name** 
 > one.tas.{_applicationName_}.{_projectName_}
 > - one.tas is a prefix for all ONE's test script
 > - applicationName is application's name to be tested
 > - projectName is test set's name with the meaning or purpose of test

* **Main contents of test project**
1. one.tas.ecom.sanity : for common utility classes
1. one.tas.ecom.sanity.pages : for page object classes
1. one.tas.ecom.sanity.tests : for test classes. one class per one test case
1. lib/io.testproject.sdk.java.jar : TestProject SDK library for java
1. build.gradle : gradle build script
