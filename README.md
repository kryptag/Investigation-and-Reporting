# Investigation-and-Reporting


* A list of all Google queries you made to solve it, and timestamps (just copy it from the browser history)
* A list all pages you visited to solve it (just copy it from the browser history)
* A list of the 3 most biggest stumbling blocks you came across and your reflection on why they were problematic (did you misunderstand   something, was some of the info you found wrong, did you miss a detail, …)
* A brief “every 30 min” diary as explained in the slides (this is more frequent than one would normally do, and is just meant as part     of   the exercise)



1. http://www.tutorialsteacher.com/linq/sample-linq-queries 22:00
2. https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/ 22:02
3. https://www.linqpad.net/Resources.aspx 22:05
4. https://stackoverflow.com/questions/3916093/linq-wherex-x-containsstring-that-start-with-foo/3916105#3916105 22:15


Link 1,2 and 3 was what i mostly used for the general basics and undestanding how LINQ works and what the concept is. 4th was mostly to find out what the method for looking and the start of a string was. The solution was "StartsWith" as can be seen below. i Used all links multiple times jumping back and forth between LINQPad and those everytime i needed some help or information.


```
var nameStartWithJ = from c in Customers 
                     where c.ContactFirstName.StartsWith("J")
                     select new { CustomerName = c.ContactFirstName};

nameStartWithJ.ToList().ForEach(c => Console.WriteLine(c.CustomerName));
``` 



## Stumbling blocks

### 1.
The first problem i ran into was i couldn't find the driver to connect to the MySQL database, read through the guides on how to set up and connect for the first time, which is included in LINQPad. But i couldn't solve the problem with that guide. So a quick google search and i found this [link](https://stackoverflow.com/questions/6629786/how-can-i-connect-to-mysql-via-linqpad) which simply told me to open the connection window and press "more drivers" and find the IQ driver pack which gave me MySQL driver and some others.

### 2.
The second problem i ran into was the part which is described like this "In particular it is said the technology prevents client side joins." After a quite a lot of searching and reading on different webpages the only thing i found was from the telerik website where this was written.

**"Some of the LINQ queries executed via the OpenAccessContext API are not completely executed on the database server, i.e. they are not completely translated to SQL, but part of them is executed on the client-side using Linq to Objects. These queries do return the correct results to the user, but usually there is a certain performance penalty during their execution."**

And this is where more confusion arose because this tool is made to solve issues as they say **"Telerik Data Access is a tool that supports development of data-oriented software applications. Telerik Data Access tool is targeted at solving the object-relational impedance mismatch."** So using their expertise and knowledge it is indeed possible to create client side joins, though it is very inefficient and bad practice if you are looking to uptimize your application or data extraction.

22:32 http://tsherlock.tech/2018/03/20/joining-in-memory-list-to-entity-framework-query/

22:31 https://docs.coveo.com/en/530/coveo-for-sitecore-v4/joining-results-using-linq

22:31 https://stackoverflow.com/questions/21937933/generate-queries-on-the-client-side

22:31 https://docs.telerik.com/data-access/developers-guide/profiling-and-tuning/profiler-and-tuning-advisor/data-access-profiler-client-side-linq-queries

22:31 https://social.msdn.microsoft.com/Forums/en-US/3dc6b6c0-416c-4453-a9b3-0232256d765a/linq-statements-server-side-or-client-side?forum=adodotnetentityframework

22:31 LINQ client side joins - Google-søgning

these where the resources i found and used, other than the first 3 i mentioned earlier for this specific issue.

## Diary

Half of the problem that i had is already described in the "Stumbling blocks" part 2. But that was joined by a couple of "re-reads" of the assigment. Because the material i found told me that client side joins were possible, while the assignment told me to look into why it wasn't possible or why its prevented.
