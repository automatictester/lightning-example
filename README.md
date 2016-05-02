# lightning-example
This repo contains [Lightning](https://github.com/automatictester/lightning) usage example.

Prerequisites:
- Java 7 or above
- Git
- Maven 3

Steps:
- Clone repo with usage example: `git clone https://github.com/automatictester/lightning-example.git`
- Go to cloned directory: `cd lightning-example`
- Run JMeter tests with jmeter-maven-plugin: `mvn clean verify`. JMeter test results are stored in `target/jmeter/results/example.csv`
- Run Lightning: `java -jar bin/lightning-standalone-3.0.0.jar verify -xml src/test/resources/lightning.xml --jmeter-csv target/jmeter/results/example.csv`. You should get output similar to this:

```
Test name:            JMeter home page - average response time
Test type:            avgRespTimeTest
Transaction name:     JMeter home page
Expected result:      Average response time <= 1000
Actual result:        Average response time = 73.6
Transaction count:    10
Longest transactions: [205, 61, 61, 60, 60]
Test result:          Pass

Test name:            JMeter home page - failed tests
Test type:            passedTransactionsTest
Transaction name:     JMeter home page
Expected result:      Number of failed transactions <= 0
Actual result:        Number of failed transactions = 0
Transaction count:    10
Test result:          Pass


============= EXECUTION SUMMARY =============
Tests executed:    2
Tests passed:      2
Tests failed:      0
Tests errors:      0
Test set status:   Pass
Execution time:    77ms
##teamcity[buildStatisticValue key='JMeter home page - average response time' value='73.6']
##teamcity[buildStatisticValue key='JMeter home page - failed tests' value='0']
```

In `reports` folder you will find JUnit XML report and `lightning-jenkins.properties` file for Jenkins Build Name Setter plugin.

Feel free to play with JMeter test plan `src/test/jmeter/example.jmx` and Lightning config file `src/test/resources/lightning.xml`. Once you familiarised yourself with the tool, create your own JMeter tests, Lightning configuration and plug it into your CI/CD server. Check Lightning [wiki](https://github.com/automatictester/lightning/wiki) for more info.