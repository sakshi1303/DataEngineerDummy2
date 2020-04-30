1. Keep code modules as separate as possible . Go for reusability only once you have verified that you are repeating yourself. 

2. Partitioning is the key when creating any data model . Whether  it is the fact table or stage table or error logging table there should always be a key on which the whole table is partitioned . In fact try and see if you have the capacity to go for sub partition as well. 

3. Always have a testing module ready . 

4. Test for a small dataset first or one record and then check the record count for whole dataset.Else it will result in wastage of time.  

5. Point 4 is not an excuse for whole dataset testing. 

6. Always try a combination of things before making any judgement. There is no right or wrong answer. Situation is different for each scenario. 

7. In any ETL pipeline , delta  load is the key , you should have a defined process for loading only those records which are either failed or missed. 

8. Performance is of most importance. All other problems are solved easily once you factor in high performance. There is a great pushback from business community about being functionally correct. However, we still need to focus on performance because it improves overall productivity.

9. A table should either have huge number of rows or huge number of columns but never both. This is the first step in performance resolution .

10. Complex SQL queries should be used , however it should be limited to 4 or 5 tables. Anything more than that you should either change your data model or create a staging/temporary table to apply further logic. 

11. Real art is chunking the data into smaller logical parts , there is no science behind it. Those which should be logically different must be kept differently. Using parallelism is a waste of time. Use multithreading. 

11. Oracle Parallel doesnot work properly. Instead use your own multithreading programming method to enhance the performance. 

12. Testing is key , more tests/testcases you do , better will be your performance. 

13. Do not depend on testers for testing , as a developer it will be beneficial for you if you do end to end testing so that issues do not resurface. 
