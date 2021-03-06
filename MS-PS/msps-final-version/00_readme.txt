1. readfile.py
Method:
readPara(fileName): read para*.txt into a list
readData(fileName): read data*.txt into a dictionary

2. find_length_1.py
Method:
find_length_1(table0, datalist, min_sup): find all length-1 frequent items
renew_table_Sk(table0, p, min1, SDC): generate table that each sequence contains a certain item p, also satisfied with SDC.
checkSDC(t, p, SDC, min1): remove items that do not satisify with SDC.

3. build_projection.py
Method:
build_projection(table0, prefix, situation, lastprefix, SDC, min1): build the raw projected database from table t, check SDC before return.
Two situations:
1) <{prefix},{x}>
2) <{prefix, x}>

4. prefix_scan.py
Method:
prefix_scan(prefix, length, table, min0, totalLen, cp, counts, SDC, min1): for a prefix, generates all its valid sequences.
For each new generated sequence, add into a *queue* (stored as a dictionary with {length:[prefix]}), then BFS all the sequences until the queue is empty.
getKey(prefix): get the key to the previous projected database. For example, sequence <{1,2,3}{4,5}>, the key is '<{1,2,3}{4}>'
sequences(prefix, t, min0, totalLen, cp, counts): generate all valid sequences from a projected database.
Two situations:
1) ({prefix, x}) 
2) ({prefix}{x})

5. ms_prefix_scan.py
getList(S, sorted_length, min_sup, length): get the list of prefix for one selected item. Compare the count(item)/totalLen and min_sup(p)
The main process is in this file, start from line 25 to the end.

===========================================================================

How to use:

python3 is required. 

In ms_prefix_scan.py, set parameter datafileName, parafileName and datalist, then run 'python3 ms_prefix_scan.py'
