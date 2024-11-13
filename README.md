# SoCo_HS24-group_10-a1

## Members
Manasi Tiwari, Ana Garcia de Carvalho, Isaiah Ly


## Description
Create Classes and Objects for your Vacations

Create the summary of all your vacations

Test your vacation booking system.


## Use of Generative AI.

Generative AI was used in our project strictly to enchance our understand of course material and assignment instructions, if it was used in another way, it has been outlined in code comments or here:

Prompt_1: this is my call func: beach resort = make(BeachResort, "Maldives", 100, 7, True) and my code above. My imports aren’t working. What’s wrong?

Prompt_2: i want to have an input in python file but more than once.

Prompt_3: how to run tests for only cruise in vacation booking tests --> did not get the right answer so I specified with: my test func are done with def find_tests and def run_tests. 
Changed it again. Asked chatgpt and it says to use sys.argv and we asked google and got an answer with geeksforgeeks.

_______________________________________________________________
Used Gemini AI to check an error when creating the VacationSummaryTool, the error was occurring due to a utilization of the VacationPackage within the VacationSummaryTool which was later resolved. 
"I am getting an error: Traceback (most recent call last):

  File "/Users/isaiahly/Documents/soco_hs24-group_10-a1/vacation_booking.py", line 31, in <module>

    '_parent': VacationPackage}

               ^^^^^^^^^^^^^^^

NameError: name 'VacationPackage' is not defined"
________________________________________________________________


## Further explaination of code structure and understanding

### Class and Object creation Step 1: # 

~ Objective: Design one parent class and three child classes with a single inheritance
that inherit directly from the parent class. The classes will describe
different vacations types. Write your code in vacation booking.py
Explaination:
I defined three vacation packages using subclasses: BeachResort, AdventureTrip, and LuxuryCruise, with attributes specific to each, like has_private_suite, includes_surfing, and difficulty_level. I updated the code definitions, starting with BeachResort, followed by AdventureTrip, while Ana did LuxuryCruise. We used separate files for better organization.
- While writing the BeachResort I realised that my import was wrong since I couldn't access the VacationPackage dictionary. So I asked ChatGPT what was wrong with my imports and it helped me realize my mistake that i corrected and was able to access the different Attributes of VacationPackage.
-There are three different functions in BeachResort: caclculate_cost_br, describe_package_br and includes_surfing.
    - calculate_cost_br: takes 3 parameters, duration_in_days, cost_per_day and value. It calculates the cost of the vacation depending on the vacation description.
    - describe_package_br: takes 3 parameters, duration_in_days, destination and value. It describes the package according to vacation description.
    - includes_surfing: takes 1 parameter, includes_surfing. This can be True or False and will return if the vacation includes surfing
- The make funciton was first made in the script and then implemented in the different files. This was so that the call that was needed for the exercise could be used as such. The person inputing a vacation package doesn't need to know how to change between the packages, it is done automatically. They just need to write the name of the package correctly in the format: 
make(vacation_name, destination, cost_per_day, duration_in_days, x)
    - x is True or False if the BeachResort or LuxuryCruise package is called.
    - x is easy or hard if the AdventureTrip package is called.
- Because of the make function I also decided to make a dictionary for every make function that is called. This will allow me access to the dictionary values without having to call the function every time. In the end the dictionary is added to the all_vacations key in the VacationPackage.
- For AdventureTrip and LuxuryCruise a similar idea to the BeachResort was used since the structure was similar.

### Summarisation of Vacations Step 2: 
(README done by Isaiah)

~ Objective: Design a class that will print the summary and the cost of all
vacation classes that have been instantiated earlier in the program. Ensure that
the correct methods are automatically invoked based on the type of vacation
package (e.g., LuxuryCruise, BeachResort, AdventureTrip).

Implementation Details:
- VacationBookingSummary Class: This part of the code is specifically responsible for the summarisation of the vacation package details, as well as the calculation of the total cost, while automatically utilising the appropriate methods depending on the specific vacation as well providing the user with a specific detailed summary from their search term.
- Methods:
-- calculate_total_cost(): This method iterates over the vacation objects stored in the VacationPackage["all vacations"], accessible through the "all vacation" key. The calculate_total_cost() function retrieves the price of each vacation stored in VacationPackage["all vacations"] and uses the calculate_cost() method to return the total cost of all vacations in the list.
-- extract_total_vacation_summary(): The extract_total_vacation_summary() method compiles a brief description of all vacations through the describe_package() functions. This is connected to three different versions of the describe_package() function which is stored in each vacation section in the code file, each function will return a summary for the respective vacation.
- Attributes:
-- search_term(val): The attribute search_term(val) compares the input value from the user against the list of vacations, if a match is found it will extract the vacation summary by calling the function describe_package() through the extract_total_vacation_summary() method to provide a filtered summary according to the user's input.

Future Enhancements:
A possible future enhancement may include advanced filtering options beyond the use of a single keyword inputted into the search (e.g. location, duration, cost range), this may allow the user to find a particular vacation that matches their preference and make the user more satisfied.
Another future enhancement may be, the ability to compare multiple vacation packages, users could select from the list of packages their most interesting package. A specific tool could provide a summary for both or more vacations selected, increasing user satisfaction and user customization.

### Testing Cases of Code System Step 3:
~ Objective: In this step, you will write and run tests to validate the behavior of
all classes created in Step 01 and Step 02.

Explaination:

Tests 1 until 5 check the cost calculation for Luxury Cruise. 
Test 1 verifies that a ValueError is raised when the third argument (private sutie) is not a boolean value. 
It ensures that invalid inputs for the private suite option are handled correctly. 

Test 2 is an intentionally incorrect test to verify that the test framework flags the error properly. 
It checks if "fail" is updated correctly, if the output doesn't match the expected result. 

Test 3 checks if the cost is correct with the boolean value True (includes a private suite). This test makes sure that when a private suite is included, the cost is multiplied by 1.5.

Similar to test 3, test 4 checks if the cost is computed correctly if it doesn't include a private suite. Like this, we make sure that that normal cost is applied (no multiplier).

Test 5 verifies that a ValueError is raised when the cost per day given is of non-valid type (in this test: float).This test ensures that only valid types (int) are accepted (for costs).

Tests 6 until 9 check the cost calculation for Beach Resort.
Test 6, like test 3, checks  if the cost is calculated correctly if boolean Value is True. This test makes sure that when surfing is included, the 100CHF has been added. 

Test 7 checks if the correct cost is generated if there no surfing. This ensures that no extra fee has been added.

Test 8, similar to Test 7, checks cost calculation when None (treated as False) is passed for the surfing option.
It ensures that the function handles None values correctly and calculates the cost properly.

Test 9 verifies that a ValueError is raised when an invalid (in tis case negative) number of days is passed. 
This test ensures that only valid, positive integers are acceptet for the number of days. 

Tests 10,11 and 12 check the cost calculation for Adventure Trip.
Test 10 chekcs if the cost is correctly computed, if the third field is set to "hard" (cost is doubled). This kind of test makes sure that the function behaves correctly based on the difficulty level. Test 11, on the other hand, checks if the cost is computed correctly if the difficulty level is set to "easy". 

Test 12 verifies that a ValueError is raised when an invalid difficutly level (e.g., "medium") is passed.
This kind of test ensures that only the valid difficulty levels "easy" and "hard" are accepted.

Tests 13, 14 and 15 check the package description for the three different types of vacations. 
All three tests check if the description of the respective vacation (luxury cruise, beach resort or adventure trip) is correct. This tests ensure that the package description is represented correctly based on the input values.

Test 16 checks if the correct dictionary is returned when creating a Luxury Cruise package. 
This ensures that all fields (destination, cost, duration) are correctly constructed.

Test 17 checks that the total cost of all booked vacations is calculated correctly.
This test ensures the sum of cost from all types of vacations is correctly computed.

Test 18 checks if the total cost of all booked vacations of a specific type of vacation is calculated correctly (in this case: Luxury Cruise). Ensures that the "filter" works and the correct sum for Luxury Cruises is returned.

Test 19 is a purposely incorrect test to verify that "error" is updated correctly when an exception occurs. This kind of test ensures that errors are flagged appropriately during the execution.

Tests 20 and 21 are like test 16, but in this case checking for the other type vacations AdventureTrip and BeachResort. This ensures us that the package is constructed properly.

Test 22 checks that the list of all booked vacations is correctly updated and formatted. 
This ensures that the summary includes all vacations with correct details.

Test 23 checks if the correct string is being returned for different kind of vacation packages. 
This kind of test ensures that the string description for each vacation is correct based on its attributes.

Rest of step 03: 
the function find_tests(prefix, vacation_name = None) searches through all functions globals and returns a list of the (test) functions that match a specific prefix. It takes a specific preifx (e.g., test_) and an optional string which could filter the tests even more, for example: test_at (looks at the tests for Adventure Trip). By default vacation_name is None, so in the general case we only look at the prefix "test_". So first, we need to initialize an empty list called "tests", where later the test functions will be stored. Then we iterate over the global variables and functions defined in the current scope.If the function name starts with the given prefix, it adds that function (func) to the list "tests". If vacation_name isn't None (default value overwritten), it applies an additional filter: it returns the tesets that start with the combined prefix + vacation_name. At the end, we return the list of functions that match the prefix (+ vacation_name if not None). This function selects all test functions that match a specific pattern, it allows us to filter the tests by vacation type (like "lc" for Luxury Cruise) if necessary.

The function run_tests(all_tests) runs a set of test functions, tracks the time of each test to execute and checks whether a test passes, fails or raises an error. It returns a dictionary of the test results. To achieve this, we first need to inititalize the results dictionary (results =  {"pass": 0, "fail": 0, "error": 0}). Like this, we can keep count of how many tests pass, fail and encounter an error. Then, the function iterates over a list of test functions "all_tests". To be able to track the time of each test function, we set the start time before evaluating the test function. Then, we enter the try block, which executes the test by calling the function and when the test is done, the end time is recorded. time_taken calculates then the duration of the tests in seconds by subtracting the start_time from the end_time. If the test function executes without any fails or errors, we print that the test passed and the duration, also the "pass" counter is incremeted by 1 (because the test was correct). But if an AssertionError occurs (assert statement failed), we print that the test failed and also how long it took to execute. In this case, we increment the "fail" counter by 1. For any other exceptions, we print that the test raised an error, the duration and increment the "error" counter by 1. After all tests have been run, we return the dictionary results(containing how many tests passed, failed and or raised errors).

The get_pattern() function is the first step in the program, checking for the --select keyword in the terminal input. If found, it picks the next word, which is the test keyword (like cruise), and checks if it belongs to one of three lists (lux, bea, adv). Depending on which list the keyword is in, the function determines which specific tests to run.
If the keyword isn’t in any of the lists, the function returns an empty string. This behavior allows the main program to check the return value: if it's an empty string, it means no specific tests were chosen, and it can run all tests. If the return value is not empty, the find_tests() function is called to find the relevant tests.

# personal_projects
