Datafly Datafly algorithm is an algorithm for providing anonymity. The
algorithm selects the attribute with the greatest number of distinct
values as the one to generalize first. Example: Iteration 1: Compute
freq count of Table w.r.t. QI set.

    MaritalStat Age     ZipCode FreqC
    Separated   29  32042   1
    Single  20  32021   1
    Widowed 24  32024   1
    Separated   28  32046   1
    Widowed 25  32045   1
    Single  23  32027   1

    Table does not satisfy /r-value: 6 tuples. Number of distinct values per QID-att: MaritalStat: 3, Age: 6, ZipCode: 6 Generalize table using Age attribute.

    Iteration 2:
    Compute freq count of Table w.r.t. QI set.
            
    MaritalStat Age ZipCode FreqC
    Separated   [25:30) 32042   1
    Single      [20:25) 32021   1
    Widowed     [20:25) 32024   1
    Separated   [25:30) 32046   1
    Widowed     [25:30) 32045   1
    Single      [20:25) 32027   1

    Table does not satisfy lvalue: 6 tuples. Number of distinct values per QID-att: MaritalStat: 3, Age: 3, ZipCode: 6 Generalize table using Zip Code attribute.

    Iteration 3:
    Compute freq count of Table w.r.t. QI set.
            
    MaritalStat Age ZipCode FreqC
    Separated   [25:30) 3204*   2
    Single      [20:25) 3202*   2
    Widowed     [20:25) 3202*   1
    Widowed     [25:30) 3204*   1

    Table does not satisfy lvalue: 2 tuples. Number of distinct values per QID-att: MaritalStat: 3, Age: 2, ZipCode: 2 Generalize table using MaritalStat attribute.

    Iteration 4:
    Compute freq count of Table w.r.t. QID set.
            
    MaritalStat Age ZipCode FreqC
    Not Married [25:30) 3204*   3
    Not Married [20:25) 3202*   3

    Table satisfies /r-value, return anonymized table. Anonymized version of Table.

    The result table:                   
    Tuple#  EQ  Marital Stat    Age ZIPCode Crime
    1       Not Married [25-30) 3204*   Murder
    4   1   Not Married [25-30) 3204*   Assault
    5       Not Married [25-30) 3204*   Piracy
    2       Not Married 120-25) 3202*   Theft
    3   2   Not Married [20-25) 3202*   Traffic
    6       Not Married [20-25) 3202*   Indecency

Process 1.Compute the frequency count (FreqC) of the table w.r.t the
attributes in the quasi-identifier(QI) set. 2.if K-anonymity is
satisfied (all FreqC \>= k), step 3. else if table is ready for
suppression, suppress tuples with FreqCs \<= suppression thresould, step
3. else a.generalize table using the attribute having the most number of
distinct values. b.step 1 c.step 2 3.Return anonymized table.

DataSet The dataset is txtfile.(Remove the column of attribute names)

Running modify the code: 1.store the file in the workplace file and
fresh project. 2.set row heading, QI and file location in the setup().
3.create new DGH(domain generalization hierarchies) trees according your
QIs. 3.1.the sequency of the trees must be same as that of QIs. 3.2.if
the some column' data is not numerical, you should build the tree in the
txtfile and store in the workpalce. running the code: set the suitable
K.

Set K of K-anonmity
