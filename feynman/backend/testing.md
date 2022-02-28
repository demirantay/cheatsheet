# Backend Testing

In this feynman note file, we will be discussing about `tests` in software and engineering in general.

- `What are tests` -- So a basic textbook definition of a "test" is: a procedure intended to establish the quality, performance, or reliability of something, especially before it is taken into widespread use. In basic words you "test" something before to see if it will give you the desired output.

- `What are the difference between normal and software engineering testing` -- I am no expert on other engineering diciplines however the testing process varies greatly from one engineering dicipline to another. Most of the other diciplines tend to have a low budget on testing because it is a cumbersome and slow process which burns a lot of money for every project. However, testing in software engineering is different. Since most of the testing can be done extremly fastly for a lot of projects, the programmers put a lot of emphasis on testing.

- `What exactly are we testing in our code` -- So "testing" is a vague term and we can discuss the ideological side of it all day long. However, let's be pragmatic and see what main points we should be testing:
  - meets the requirements that guided its design and development,
  - responds correctly to all kinds of inputs,
  - performs its functions within an acceptable time,
  - is sufficiently usable,
  - can be installed and run in its intended environments
  - achieves the general result its stakeholders desire.

  If all of your tests are generally categorized into the points mentioned above you will be covered for the most part. However always know that there can be exceptions to you project. 
  
- `Why is testing so important` -- A study conducted by NIST in 2002 reports that software bugs cost the U.S. economy $59.5 billion annually. More than a third of this cost could be avoided, if better software testing was performed. Or if you do not care about money at all, think about chernobyl! The reactor exploded when it was in a testing mode. Think about all of the lives that were lost just because of bad testing.

- `What are modern ways to write tests` -- You have to realize, the the number of possible tests that you can write for your software is practically infinte. So you will just have to be pragmatic about your time and resources.

- `What are the modern testing approach` -- Broadly speaking, there are at least three levels of testing: __unit__ testing, **integration** testing, and __system__ testing. Tests are frequently grouped into these three levels.

- `Unit tests` -- Unit testing refers to tests that verify the functionality of a specific section of code, , usually at the function level. In an object-oriented environment, this is usually at the class level, and the minimal unit tests include the constructors and destructors. These types of tests are usually written by developers as they work on code (white-box style)

- `Integration tests` -- Integration testing is any type of software testing that seeks to verify the interfaces between components against a software design. Software components may be integrated in an iterative way or all together ("big bang"). Normally the former is considered a better practice since it allows interface issues to be located more quickly and fixed. But it isn't a cath 22 we can have both unit an integration tests.

- `System tests` -- System testing tests a completely integrated system to verify that the system meets its requirements. For example, a system test might involve testing a login interface, then creating and editing an entry, plus sending or printing results, followed by summary processing or deletion (or archiving) of entries, then logoff.

- `Testing types, techniques and tactics` -- Different labels and ways of grouping testing may be testing types, software testing tactics or techniques., installation testing, Compatibility testing, Smoke and sanity testing, Regression testing ... etc.

- `Where do we write tests` -- Every project requires a different place to store their tests, it even differs from language to language or framework to framework. You can place your tests wherever you would like but as we said above, when you are working on a real life project it is best to not go out of the way of industry standarts.

- `When do we write tests` -- It all depends on the software design pattern that you are using, some people use TDD where they write tests ALL OF THE TIME or you can be using a basic scrum methodlogy where you will just test the code after the development sprint is finished.

- `A sample testing cycle` -- Although variations exist between organizations, there is a typical cycle for testing.
  - Requirements analysis: During the design phase, testers work to determine what aspects of a design are testable and with what parameters those tests work.
  - Test planning: Test strategy, test plan, testbed creation
  - Test development: Test procedures, test scenarios, test cases, test datasets, test scripts to use in testing software.
  - Test execution: Testers execute the software based on the plans and test documents then report any errors found to the development team
  - Test reporting: Once testing is completed, testers generate metrics and make final reports on their test effort and whether or not the software tested is ready for release.
  - Test result analysis: Or Defect Analysis, is done by the development team usually along with the client
  - Defect Retesting: Once a defect has been dealt with by the development team, it is retested by the testing team
  - Regression testing: It is common to have a small test program built of a subset of tests, for each integration of new, modified, or fixed software, in order to ensure that the latest delivery has not ruined anything
  - Test Closure: Once the test meets the exit criteria, the activities such as capturing the key outputs, lessons learned, results, logs, documents related to the project are archived and used as a reference for future projects.

- `Automated testing` -- There are automated testing tools to automate large scale integration tests. Especially projects that follow the TDD rule use automated testing a lot.

- `Testing Terms` -- 
  - __Test plan__ -- A test plan is a document detailing the approach that will be taken for intended test activities.
  - __Traceability matrix__ -- A traceability matrix is a table that correlates requirements or design documents to test documents
  - __Test case__ -- A test case normally consists of a unique identifier, requirement references from a design specification, preconditions, events, a series of steps (also known as actions) to follow, input, output, expected result, and the actual result
  - __Test script__ -- A test script is a procedure or programming code that replicates user actions.
  - __Test suite__ -- The most common term for a collection of test cases is a test suite.
  - __Test fixture or test data__ -- In most cases, multiple sets of values or data are used to test the same functionality of a particular feature.
  - __Test harness__ -- The software, tools, samples of data input and output, and configurations are all referred to collectively as a test harness.
  - __Test run__ -- A report of the results from running a test case or a test suite

