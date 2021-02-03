# SoapUIDemo with GitLab Integration

## Summary
The project contains soapui project xml in the root directory. In this project demo_retrievecustomer.xml is the key of the whole project.
For development purpose or adding new test cases, import this file in soapui and start creating/executing/updating test cases

## How to run project
####clone the project and run command
*  mvn clean test - this command will run test cases bt wont generate report
*  mvn clean site - this command will run test cases and generate report

## How to see result
* Result can be find under :: target/site/surefire report
* Soapui logs can be found under : target folder as well

## Data directory
The data folder contains 3 type of file : 
* GlobalProperties.properties
* TestSuiteData.properties
* RetrieveCustomerTestCaseData.csv


### GlobalProperties.properties
This file conatins project level variable with specified value in file
APIKey
ServerEndPoint
Anything key value specified under this project will become, Project level property

### TestSuiteData.properties
It contains test suite level property or variable. 

### RetrieveCustomerTestCaseData.csv
As the name suggest this file contains test data for retrieve customer endpoint

## How do Global, Suite or test data level data/variable/property get set in project

Each test case have a grovvy script as it first test step. In this step we write groovy code to set these property

#### How to access property
* project level : ${#Project#PropertyName}
* Suite level - ${#TestSuite#PropertyName}
* TestCase level - ${#TestCase#PropertyName}


## Test Cases Automated:

we have automated 4 test cases for retrieve customer data
* VerifyStatusWithValidToken
* VerifyStatusWithInvalidToken
* VerifyResponseWithoutCustomerId
* VerifyCustomerInformation

The test case 1 VerifyStatusWithValidToken, contains groovy script of setting global and suite level data
Name of the script is
* SetProjectLevelData
* SetSuiteLevelData

Each test case contains SetData groovy which read data from RetrieveCustomerTestCaseData.csv file as per the requirement

## About Maven SoapUI Plugin

The maven soapui plugin enable us to run the soap ui project via command line without soapui test runner. In the pom we have used the soapui-maven-plugin. This plugin has following important property

* projectFile : soap ui xml project file path. this property read the project file from file. Read summary path to get more
* outputFolder: this property  will through project logs in this location
[Do not change these property]

### Reporting

In pom we have reporting plugin which generate report in the site folder under target directory







