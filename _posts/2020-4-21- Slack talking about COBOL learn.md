

# Notes for which we continue learning after IBM open project course
 1 The SEARCH verb (sequential and binary variations) is used quite often in Cobol programs. 
 Interview question: "Explain table handling in Cobol."  Hint: Use the SEARCH verb and the REDEFINES clause in the DATA DIVISION.  
 
 2) Study 88 level items in the DATA DIVISION, what they are and how to use them. Also involves the SET verb.
 
 3) INSPECT and INSPECT REPLACING (older IBM pre-COBOL II compilers used EXAMINE), is used quite often.
 4) Making 2 fields print on the same line together (e.g. first and last name) without blank space in between, is also a concept.  Hint:  use the STRING verb. 
 5) Study the UNSTRING verb.  
 6) Look at the COBOL Language Reference Manual, and study all the available reserved words in Chapter 20. Learn their purpose and what they do. IBM Cobol Language Reference Manual v6.3 http://publibfp.boulder.ibm.com/epubs/pdf/igy6lr30.pdf.  
 7) Study the Cobol intrinic functions available, Chapter 21 of the same manual. 
 8  Don't ever use the GO TO verb, no need to use it. 
 9) Don't ever use the ALTER (GO TO) verb, and pray you don't run into any programs that do.
 10) Avoid tying your program up in "NOT"s (for non-English speakers, this is a play on words; the word "not" vs. the word "knot"), i.e. don't ever use NOT in conditional statements, or at least very sparingly.  You can use CONTINUE (nop in other languages) to accomplish the same thing with positive, rather than negative logic. 
 11)  Study the case structure verb, EVALUATE, EVALUATE TRUE, and EVALUATE variable-name.  Be sure to use WHEN OTHER as a final condition in an EVALUATE statement. 
 12) Next, you should familiarize yourself with JCL.  Study the examples.  z/OS MVS JCL Reference v2r3, https://www-01.ibm.com/servers/resourcelink/svc00100.nsf/pages/zOSV2R3SA231385/$file/ieab600_v2r3.pdf 
 13) Then after all that, study the DFSORT manual (and also ICETOOL).  Sorting (using DFSORT or a 3rd party software product, e.g. SYNCSORT is very common) is heavily used in commercial (real world) environments. If you only learn one general use utility, this is the one to learn.  DFSORT Application Programming Guide, v2r3, https://www-01.ibm.com/servers/resourcelink/svc00100.nsf/pages/zOSV2R3sc236878/$file/icea100_v2r3.pdf  Most of you here probably already know how to program in other languages better than I.  What will be most beneficial to you, is to learn many of the unique things about Cobol (the above items are a start), and understand why Cobol is well suited to process transactions, i.e. processing files containing lines of data to process, whether to update another output "flat" file or a database.  
 Lots of things to study, learn and try.  And ask questions in this forum for the benefit of all, perhaps to motivate others here to learn another thing or two that they didn't already know!  Good luck! (edited) 
