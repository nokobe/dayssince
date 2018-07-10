# Project Title

dayssince calculates either the number of days since a given date or, given an offset, a new date.
In either case the default reference date is today or a reference date can be provided

## Getting Started

Just copy/install the script. Note the dependancy on Date::Calc

### Prerequisites

This perl program is dependant on the Date::Calc package

What things you need to install the software and how to install them

### testsuite

There is a simple test suite to check that the program is running properly

Note that becase of a "leading zero" issue, some of the tests give a false failure.

eg:

$ ./testsuite
	FAIL: Test 6: ./dayssince +1 GOT ==> 11/7/2018 EXPECTED ==> 11/07/2018
	FAIL: Test 7: ./dayssince -1 GOT ==> 9/7/2018 EXPECTED ==> 09/07/2018
	FAIL: Test 8: ./dayssince +7 GOT ==> 17/7/2018 EXPECTED ==> 17/07/2018
	FAIL: Test 9: ./dayssince +180 GOT ==> 6/1/2019 EXPECTED ==> 06/01/2019
	FAIL: Test 10: ./dayssince -30 GOT ==> 10/6/2018 EXPECTED ==> 10/06/2018

### quirks

The resulting dates are presented as DD/MM/YYYY.

This is obviously not the international format, however I left it this way to better align with the way the program interprets partial dates.
eg.
	1		will be interpreted as the 1st day of this month
	1/2		will be interpreted as the 1st day of the 2nd month, this year


Sample usage:

$ date
Tue 10 Jul 2018 17:12:12 AEST

### given a reference date

$ dayssince 2   # (2/7/2018)
8

$ dayssince 2/6   # (2/6/2018)
38

$ dayssince 2/4/2017
464

### future dates can be specified

$ dayssince 8/8
-29

### calculate a new date based on a reference date (default: today)

$ dayssince +30
9/8/2018

$ dayssince 1/1/2018 +30
31/1/2018

$ dayssince 1/1/2018 -30
2/12/2017

### calculate the number of days between two dates

$ dayssince 30/6 30/7
30

$ dayssince 30/7 30/8
31

## Running the tests

./testsuite

All going well, you will see "ALL TESTS PASSED"

However, in all likelihood, some tests will (falsely) fail due to the leading zeros in some of the generated test dates.

eg:
	FAIL: Test 6: ./dayssince +1 GOT ==> 11/7/2018 EXPECTED ==> 11/07/2018

A quick eyeball of the FAILs, you can see if the results are actually correct.

## Authors

* **Mark Bates** - https://github.com/nokobe

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* This is not a long program however it is deceptively simple. Look carefully and you will see that simplicity is derived by some good programming:
* - good logical breakdown of the layers of the program
* - good separation between the interface and the underlying model
* - good data encapsulation of the date, which hides the actual implementation of the date object
* I consider these good programming practises, which were drilled into me my by programming mentor, Patrick Wong.
