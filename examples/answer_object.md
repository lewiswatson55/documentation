The data in the answer object can be broken down into two seperate types. The basic questions version, and the complex version.

---

## Simple Version:

0. App Version - Float - MUST BE 2.0 - BACKEND WILL DISCARD IF 1.0
   
1. Basic/Complex Version Index - 0 = Basic Version, 1 = Complex Version
   
2. Species - 0 = UC, 1 = GC
   
3. Index of Year - 0 = 2016, 1 = 2017...
   
4. Index of Month - 0 = Jan, 1 = Feb...
   
5. List of Days as Strings with Year and Month - i.e ["08/01/2016 00:00","07/01/2016 00:00"]
   
6. String of Intensity - ie. ["High"]
   
7. State as String
   
8. County as String
   
9. Protected area (same as 13 of complex version)
    
10. Occupation as String

11. List of two strings, “Yes” or “No” then String answer of additional observation - i.e ["Yes","Additional Observation Here"]

12. Submission date and time

---


## Complex Version:

0. App Version - Float MUST BE 2.0 - BACKEND WILL DISCARD IF 1.0
   
1. Basic/Complex Version Index - 0 = Basic Version, 1 = Complex Version
   
2. Species - 0 = UC, 1 = GC
   
3. Index of Year - 0 = 2016, 1 = 2017...
   
4. Index of Month - 0 = Jan, 1 = Feb...
   
5. List of Days as Strings with Year and Month - i.e ["08/01/2016 00:00","07/01/2016 00:00"]
   
6. Strongest Day - Same formatting as above, if nothing is selected list is empty.
   
7. String of Intensity - ie. ["High"]
   
8. Index of Time of Day - 0 = Day Only, 1=Only at Night, 2=Both, 3=Did Not Look
   
9.  String answer of Berried Question - i.e ["Yes, I saw berried females"]
    
10. List of true false for each of the options for the selected species. - i.e ["[true, true, false, false, false, false, false, false, true]"]

11. State as String

12. County as String

13. Protected Area - List with two elements first element is index of check button selected ie “yes” = 0, second element is the index of the protected area (if first element is NOT 0 then second element is -1), if not in list there is three elements last element being string of other answer.

14. Occupation as String

15. List of two strings, “Yes” or “No” then String answer of additional observation - i.e ["Yes","Additional Observation Here"]

16. Submission date and time

17. Not Used
18. Not Used
