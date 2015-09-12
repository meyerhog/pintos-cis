To add alarm-mega I had to edit several files and create a new file.  It is explained below.

/pintos/src/tests/threads/alarm-mega.ck
Added this file by duplicating alarm-multiple.ck and renaming it to alarm-mega.ck with the cp command.
Then I changed the value that is sent to the check_alarm function to 70.

/pintos/src/tests/threads/tests.c
I edited this file to include one more item in the constant array called "tests" (tests[]).
This array contains multiple structs called test that contain a constant char* for the name and then the function name that is of type test_func.
I added this one line of code (without outside quotes): "{"alarm-mega", test_alarm_mega},"
This adds a new test struct to the array (tests) with the name alarm-mega and a function called test_alarm_mega which a variable defined in tests.h.

/pintos/src/tests/threads/Make.tests
I added the name of the test (alarm-mega) to be included in the list of test names.

/pintos/src/tests/threads/Rubric.alarm
Added alarm-mega to the list and made the number in front of it the same as alarm-multiple so that they have the same "Functionality and robustness".

/pintos/src/tests/threads/tests.h
Added the function name that I gave in the tests.c file to the header file to be given a type of test_func and be labled as an external function.
Added this line: "extern test_func test_alarm_mega;"

/pintos/src/tests/threads/alarm-wait.c
Defined the function test_alarm_mega that is called when we run alarm-mega.
It was similar to the function test_alarm_multiple. It does not have any parameters and does not return anything.
It then calls the test_sleep function defined in this file and sends it the number of threads and iterations.
test_alarm_multiple called the method with 5 threads and 7 iterations so I made test_alarm_mega call with also 5 threads but 70 iterations.

