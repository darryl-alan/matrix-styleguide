# Matrix IT Style Guide

## General
* Use variables as self-documentation when possible. Let's say you're writing logic to differentiate whether the user entered an employee ID which is 10 characters long, or a personal ID which is 15 characters long, with different processing for each.
```
	// BAD, the purpose of the if condition is unclear
	if(input.length === 10){
		doSomething();
	}
	else{
		doSomethingElse();
	}


	// GOOD, gives clear meaning to the if condition
	const isEmployeeID = input.length === 10;
	if(isEmployeeID){
		doSomething();
	}
	else{
		doSomethingElse();
	}
```

## Database Schema Design
* Every table (unless it's a junction table) that should have a primary key, should use a unique, non-system-specific column as primary key. Best practice is to use either an auto increment column, or a UUID column. Do not rely on a business-related column as a primary key because what's unique today might not be unique in the future.
```
	-- BAD!
	CREATE TABLE Account ( 
		AccountNumber VARCHAR(20) PRIMARY KEY 
	)

	-- GOOD! AccountID contains UUID string
	CREATE TABLE Account ( 
		AccountID VARCHAR(36) PRIMARY KEY, 
		AccountNumber VARCHAR(20)
	) 
```
