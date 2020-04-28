In this case, the Boolean condition is evaluated before the loop is executed. However, if you wish for the loop to be executed at least once before the condition is evaluated, you can alter the sentence to read:

Example 15. PERFORM UNTIL WITH TEST AFTER

PERFORM UNTIL COUNTER = 10 WITH TEST AFTER

ADD 1 TO COUNTER GIVING COUNTER
MOVE COUNTER TO MSG-TO-WRITE

WRITE PRINT-REC

END-PERFORM.
——————————————————————————————————————————————————————
This would be similar to a "do while" loop in Java:
Example 16. Java while loop
——————————————————————————————————————————————————————
do{
//counter++
//move counter to msg-to-write
//write print-rec
}
While(counter != 10);
——————————————————————————————————————————————————————
