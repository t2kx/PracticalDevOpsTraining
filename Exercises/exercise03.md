# Exercise 3


## Learnings

1. Basics about test projects
1. Mocking dependencies using *Fakes*
1. Hosting Web API in tests using OWIN
1. Creating an automated Web Test


## Add Test Project

1. Add a test project to your Visual Studio solution.<br/>
   ![Add test project](img/visual-studio-add-test.png)

1. Remove generated `UnitTest1.cs`.

1. Switch to latest version of .NET (4.6.1) in the Books.Test project properties page just like you did for the Books project in exercise 1

1. Add a reference to the Web API project from your new test project.<br/>
   ![Add reference](img/add-references-test-project.png)

1. Add references to the following framework assemblies:
   * `System.ComponentModel.Composition`
   * `System.ComponentModel.Composition.Registration`
   * `System.Reflection.Context`

1. Add a reference to the Books project.

1. Install necessary NuGet packages by running the following commands in Visual Studio's *Package Manager Console* (you can use *Manage NuGet Packages for Solution* instead if you prefer GUI over PowerShell):
   * `Install-Package Microsoft.AspNet.WebApi.Owin -Project Books.Test`
   * `Install-Package Microsoft.Owin.Host.SystemWeb -Project Books.Test`
   * `Install-Package Microsoft.AspNet.WebApi.OwinSelfHost -Project Books.Test`


## Add and Run Tests

1. **Microsoft Fakes** help you isolate the code you are testing by replacing other parts of the application with stubs or shims. These are small pieces of code that are under the control of your tests. By isolating your code for testing, you know that if the test fails, the cause is there and not somewhere else. Stubs and shims also let you test your code even if other parts of your application are not working yet.

1. [Optional] Learn more about Microsoft Fakes (https://msdn.microsoft.com/en-us/library/hh549175.aspx)

1. Add *Fakes* assembly for `Books` reference:<br/>
   ![Add Fakes](img/add-fakes-assembly.png)
   
1. Replace `Fakes/Books.fakes` with the following code:
   ```
    <Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
        <Assembly Name="Books"/>
        <StubGeneration>
            <Clear/>
            <Add TypeName="INameGenerator"/>
        </StubGeneration>
        <ShimGeneration>
            <Clear/>
        </ShimGeneration>
    </Fakes>
   ```

1. Copy `.cs` files from [Assets/Exercise-3-Tests](Assets/Exercise-3-Tests) into your test project. Make yourself familiar with the two test files.

1. Build your test project. There should not be errors.

1. Open Visual Studio's *Test Explorer* and run all tests.<br/>
   ![Test Explorer](img/visual-studio-test-explorer.png)


## Add Web Test

1. Add a new *Web Performance and Load Test Project*.<br/>
   ![Add Web Test Project](img/visual-studio-add-web-test.png)

1. Rename test to `GetBooksTest`<br/>
   ![Rename test](img/rename-getbookstest.png)

1. Add web request to our *Get Books* Web API.<br/>
   ![Add request to Web Test](img/add-request-to-web-test.png)

1. Open the request's properties and change the URL appropriately.<br/>
   ![Change URL in request's properties](img/request-test-properties.png)

1. Parameterize web server. This is important if you have lots of requests. With parameters, tests become much easier to maintain.<br/>
   ![Parameterize Web Server](img/parameterize-web-server.png)

1. Make yourself familiar with the web test after server parameterization.<br/>
   ![Test after parameterization](img/parameterized-web-server.png)

1. Start an instance of your OWIN web server (press *Ctrl+F5* to start it without debugger).

1. Run the web test.<br/>
   ![Run web test](img/run-test.png)
   
1. Verify that test was successful.<br/>
   ![Verify test results](img/test-results.png)


## Add Load Test

1. Add load test to web test project.<br/>
   ![Add load test](img/add-load-test.png)

1. Select the following test settings (select default values for settings not mentioned here):
   * Select *On-premise Load Test* (we will move to the cloud later)
   * 100 test iterations
   * 5 seconds sampling rate
   * Constant load of 10 users
   * Add the `GetBooksTest` to the load test

1. Run load test.<br/>
   ![Run load test](img/run-load-test.png)

1. Analyze load test results.<br/>
   ![Analyze results](img/analyze-load-test-results.png)
