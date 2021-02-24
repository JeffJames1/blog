# Performance Tip: All vs. Relevant Values in Tableau filters

This is an on-going balancing act and the impact of the choice isn't always obvious.

Choosing "Relevant Values" seems great. The displayed options are those still in data set after the other filters have been applied, and the list is smaller. Smaller lists are always better, right?

Unfortunately, the real impact is more complex. Every filter that is set to "Relevant Values" requires a query of the database to return a distinct list of the remaining values. If you have many filters (not a focused design, but that's a different topic), each one has latency associated with compiling the query, connecting to the database, etc. Even if the query itself is quick, there is overhead. Additionally, Tableau has a limit to the number of queries that it can run in parallel. If you exceed it, the others are queued until a slot becomes available.

Many dashboards that we or our clients create have 5-8 worksheets, and 5-10 filters. With all of that complexity, a single change to a filter or an action can run 30+ queries against the database. There's nothing inherently wrong with that, but it make it much harder to achieve performance goals.

Bottomline: rather than always using "Relevant Values", give some strong consideration to using "All values in database" which only requires a single query when the dashboard is opened. Alternatively, use custom list or wildcard filters which do not require queries with every change to the other filters.

**Alternative:** If you need to use "Relevant Values" due to end user requirements, AND you're up for a little more work, there is an alternative. You can create a data set that contains all unique combinations of dimension values, build the quick filters from that, then filter the primary data source through cross-data source filtering. That is probably a topic for another post, so I'll hold off on the details for now.  
