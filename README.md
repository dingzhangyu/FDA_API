# FDA_API
U.S. Food and Drug Administration provides almost 10 kinds of APIs that enable users to extract information about drugs, medical devices, food, etc. The website for developer is https://open.fda.gov, which is also very useful and user-friendly for journalists to find information, including product recalls and adverse events, out of public interest.   

In my case, I chose its Food Recall Enforcement Reports API, which returns data from the FDA Recall Enterprise System.

## Query 1
For the first query, I want to see how many recalls have been initiated in 2019 regarding milk-related food. Here is the query:

```https://api.fda.gov/food/enforcement.json?search=reason_for_recall:"milk"+AND+classification:"Class+I"+AND+report_date:[20190101+TO+20191231]&count=recalling_firm.exact&limit=5```

For the first query, I’ve set five parameters:

* `Reason_for_recall = milk` means the recall has something to do with milk. You can change `milk` to any other types of food like `chips` or `ice+cream`.

* There are three classifications, where `Class+I` is the most serious one, which FDA defines as “dangerous or defective products that predictably could cause serious health problems or death.” The other two possible values are `Class+II` and `Class+III`.

* Report date is easy to understand, which means we perfectly collect all the recall reports in 2019. The correct format is `[yyyymmdd+TO+yyyymmdd]`, where `y`, `m` and `d` are all digits.

* `Count` means how we group the data. Here we want to have the number of recalls initiated by each company related, so we use set `count` equal to `recalling_firm.exact`.

* `Limit` means how many entries of result we want the query to return. Here we pick the top five companies in terms of number of recalls.


