# Code Review Notes

## LoanCalculatorIT.java
- I think some test cases are overkill like for example calculateLoan_negativeInterestPercentageAndNumberOfMonths, do we really need to test this case if we've already separately tested cases where interest percentage and number of monts are negative

## TestConstants.java
- SQL_FILE_CLEAN_UP_DATA_PATH rm unused

## LoanCalculatorControllerTest.java
- I dont see the point of this test, we're just asserting what we are mocking in the test itself ?

## Generally tests are much larger than I would assume, but it cant be helped if there are a lof of fields to assert on 

## Db credentials should be moved outside of application.yaml to any type of secret keeper

## LoanCalculationResultEntityRepository rm unused

## When creating entities, we create them with the no args constructor and then set all fields with setters. This is bad because our object should have all fields and this approach makes it easy to forget to set a certain field and create an invalid object. I would rather use all args constructor here. If we want to address the fact that we have a no args constructor available in the domain (because hibernate needs it), then I would rather add another layer of mapping to have different classes for our entities to be used in the domain and different classes for persistence
