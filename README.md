# Email Analysis (in progress)
## Problem Statement
Download your emails from 1.1.2020 to 1.9.2020. Each recipient and sender is a node. Create a directed, weighted edge from the sender to the recipient. The weight of the edge is the number of emails exchanged.
(a) Compute weighted in-degree and out-degree of each node. Plot the degree distribution and note your observations.
(b) Consider the network as an undirected and unweighted network. Plot the degree distribution and note your observations.
(c) Find the average path length and clustering coefficient of the network version II.

1.	Libraries and Functions used: 
-

|NAME|USE|
|----|---|
|networkx|	It is a python library for studying graphs and networks. It is free software released under the BSD-new license|
|pandas|	It is a library for using various python data frame  manipulation functions|
|matplotlib.pyplot|	This python library is primarily used for data visualization; it provides plots such as hist( ) for histogram, scatter( ) for scatter plot, bar( ) for bar plot, etc|
|email.utils|	This python library is used to parse various components of an email such as sender’s address, receiver’s address, cc, bcc, and date of delivery of email, using built-in functions such as parseaddr( ) and getaddresses ( ) |
|mailbox|	It is a python library used to read a .mbox file, which is a container for entire mail and mail-metadata|
|collections	This python library has containers to store the collection of data |
|networkx.MultiDiGraph( )|	It creates an instance of Multi-Directed graph type, i.e., a graph with directed edges and multiple edges allowed between a pair of nodes.|
|MultiDiGraph( ).add_weighted_edges_from( )|	This function takes as input a 3-tuple of the format (u, v, w) and primarily adds the ‘w’ part i.e. the weight attribute to the edges|
|networkx.draw( )|	It takes as input, the network graph instance and various other arguments about the node (size/ label/ font/color), edge(directed/ size/ color), etc and renders the graph accordingly|
|networkx_draw_networkx_edges( )|	It takes as input network graph instance various edge attributes such as color, and width and renders the graph accordingly|
|MultiDiGraph.in_degree( )|	It computes the weighted in-degree of all the nodes, by setting the weight parameter as Boolean True
|MultiDiGraph.out_degree( )|	It computes the weighted out-degree of all the nodes, by setting the weight parameter as Boolean True
|networkx.Graph( ).degree( )|	It computes the degree of all the nodes for an unweighted, un-directed graph
|networkx.average_clustering( )|	It computes the clustering coefficient of a graph by summing the clustering coefficient of all individual nodes in the graph and taking their average|
|networkx.average_shortest_path_length( )|	It computes the average path length of the graph by aggregating over all possible shortest path between all possible pair of nodes in the graph|

2.	DATA PRE-PROCESSING
-
2.1.	 Data Extraction
-
•	Gmail data for each group member was extracted using Google Takeout - a project by Google Data Liberation Front, which allows users to export their data (Gmail, YouTube, and Maps) to a downloadable archive file. 
•	The Gmail data was exported as a .mbox file.
•	The file contents (mail subject, sender’s details, recipient’s details, the delivery date of email, cc, and bcc) were parsed using a python library, namely mailbox.

2.2.	 Data Filtering and Preparation
-
•	The parsed emails were filtered based on the date of delivery of email, to allow emails in the period 01-Jan-2020 to 01-Sep-2020 only.
•	A pandas data frame was created from the filtered data.
•	The format of the data kept in the data frame was of the form < u, v, w> where ‘u’ is the sender’s address, ‘v’ is the recipient address, and ‘w’ is the number of emails sent from ‘u’ to ‘v.’
•	This format of data was used so that it can be smoothly passed to the networkx module to create the corresponding graph instance.
•	Each sender is a node. Each receiver is a node. The edge direction in a directed, weighted graph indicates the direction of email, and the edge weight denotes the number of emails sent.

2.3.	 Assumptions
-
The following assumptions were taken for simplification:

•	If a mail was sent through a google group, i.e., there are multiple senders for the same mail, then the google group is considered to be a single node in the network.
•	The above assumption is extended for receivers also, i.e., if a mail is sent to a google group, then also it is considered as a single node in the network drawn.
•	Those mails are dropped, where the sender’s email address is the same as the receiver’s email address, i.e., the sender has mailed to self. It would not significantly contribute to the Gmail network analysis since it is a self-loop only.
•	Few email addresses are not depicted, where an email address was less descriptive, for eg-drive@noshare, no-reply@..., classroom@123.., instead their corresponding user names are shown to convey more information to the reader.
•	Since the majority of email addresses are Gmail accounts, they are displayed without the domain ‘@gmail.com’. Those outside this domain are shown as is.
•	In the Network Version I (Directed, Weighted), the edge weights are depicted by their thickness (width), i.e., more is the edge weight, thicker it is shown.


Fig.1: Snapshot of how data looks for yatin.mcs19.du@gmail.com before passing it to the netowrkx module and similarly for supriya.mcs19.du@gmail.com and ashwani.mcs19.du@gmail.com.

|Group Members’ Email-address|	Number of distinct emails	|Number of Nodes (n)	
Number of edges in Network Version I
(mI)	
Number of edges in Network Version II
(mII)

yatin.mcs19.du
@gmail.com
	
89	
77	
89	
76

supriya.mcs19.du
@gmail.com	
79	
72	
79	
71

ashwani.mcs19.du
@gmail.com 
	
138	
112	
138
	
111


Table 2: Summary of each group members’ Gmail Network Version I (weighted, directed graph) and Network Version II (unweighted, un-directed graph)






3.	OBSERVATION PLOTS AND TABLES
 

Fig 2.1: Directed, weighted Gmail Network (Version I) for yatin.mcs19.du@gmail.com
 
   
Fig 2.2: Directed-Weighted Gmail Network (Version I) for supriya.mcs19.du@gmail.com





 Fig 2.3: Directed-Weighted Gmail Network (Version I) for ashwani.mcs19.du@gmail.com
         
							     (a)



       
         (b)



       
           (c)

Fig 2.4: Weighted in-degree and weighted out-degree distribution of Network Version I for 
(a) yatin.mcs19.du@gmail.com, (b) supriya.mcs19.du@gmail.com and (c) ashwani.mcs19.du@gmail.com
 

Fig 2.5: Undirected un-weighted Gmail Network (Version II) for supriya.mcs19.du@gmail.com and similar network is observed for yatin.mcs19.du@gmail.com and ashwani.mcs19.du@gmail.com. 
¬ 

(a)

 

(b)

 

(c)

Fig 2.6: Degree distribution for Network version II (Un-weighted and Un-directed) for 
(a) yatin.mcs19.du@gmail.com, (b) supriya.mcs19.du@gmail.com and (c) ashwani.mcs19.du@gmail.com

Group members’ 
email-address	
Number of nodes in the network	
Clustering Coefficient for Network Version II	
Average path length for 
Network Version II (µL)

yatin.mcs19.du
@gmail.com
	
77	
0.0	
1.974

supriya.mcs19.du
@gmail.com
	
72	
0.0	
1.972

ashwani.mcs19.du
@gmail.com
	
112	
0.0	
1.982

Table 3: Observed clustering coefficient and average path length for Network version II for all group members




Group members’ 
email-address	
Number of nodes in the network
(n)
	
Maximum weighted in-degree of Network Version I
(ki max)	
Maximum weighted 
out-degree of Network Version I
(ko max)

yatin.mcs19.du
@gmail.com
	
77	
102	
196

supriya.mcs19.du
@gmail.com
	
72	
293	
45

ashwani.mcs19.du
@gmail.com
	
112	
517	
314

Table 4: Some additional observations from Network version I for all group members






Group members’
email-address	
Top-5 email exchanges
( Incoming )	
Top-5 email exchanges
( Outgoing )

yatin.mcs19.du
@gmail.com
	vaishali.mcs18.du@gmail.com (15)	devansh.mcs19.du@gmail.com (21)
	vb.ducs@gmail.com (14)	vb.ducs@gmail.com (19)
	ashwanivarshney25@gmail.com (14)	vaishali.mcs18.du@gmail.com (19)
	ashwani.mcs19.du@gmail.com (11)	ashwani.mcs19.du@gmail.com (18)
	jaspreet.mcs19.du@gmail.com (9)	himanshu.mcs19.du@gmail.com (15)


supriya.mcs19.du
@gmail.com
	Revanth Kumar (Classroom) (45)	farheen.mcs19.du@gmail.com (4)
	info@mailer.netflix.com (38)	vb.ducs@gmail.com (4)
	Coursera (24)	mcs19du@googlegroups.com (3)
	farheen.mcs19.du@gmail.com (18)	1916035@pg.du.ac.in (2)
	University of Delhi (18)	ashwani.mcs19.du@gmail.com (2)


ashwani.mcs19.du
@gmail.com
	vb.ducs@gmail.com (88)	mcs19.du@googlegroups.com (94)
	technews@techgig.com (64)	ml-announcements@googlegroups.com(43)
	promotion@techgig.com (34)	vb.ducs@gmail.com (28)
	jobs@techgig.com (29)	sapna.varsh@gmail.com (25)
	yatin.mcs19.du@gmai.com (28)	supriyakatyal16@gmail.com

Table 5: Top-5 email-exchanges from Network version I for all group members

4.	INFERENCE & ANALYSIS

•	Analogous to many real-world graphs, the Gmail network for all group members is a large and sparse graph. The notion of large has to do with the order of the graph, i.e., the number of nodes is vast, while by sparse, it follows that graph size or number of edges, m = O(n). It is evident from Table 2. Although the number of nodes might not seem very large, it is worth mentioning that this Gmail network represents the data for a few months only; otherwise, the number of nodes in the network would run into thousands.

•	From Table 3, it is visible that the global clustering coefficient for Network Version II (undirected, unweighted) for all group members is precisely 0. This metric measures the strength of connectivity among the neighbors of the nodes, and the cliquishness in the network. While the value of 0 might seem contrary to many real-world networks, this arises because the Gmail network so formed in this context gives attention to the individual email address of the group member. If the Gmail data for all the group members are combined, it results in some positive (> 0) value for the global clustering coefficient of the network.  It implies that if a user links two different users, it is highly likely that these two linked users might know each other, or the chances of acquaintanceship among the 2 linked users would be much higher than that of 2 randomly selected strangers being acquaintances.

•	From Table 3, it is observed that the average path length for the Gmail network of all group members was recorded as ~2. It means that every node in the network is reachable via every other node in at most 2 hops. Since network version II is indeed a star graph, the radius of the graph, r(G) equals 1, and the diameter of the graph D(G), equals 2. Hence, it can be concluded that the Gmail network of each group member has a 2-degree separation.

•	Regarding Fig 2.4, it can be observed that the vast majority of nodes have minimal degrees, while very few hub nodes have a very high degree. It leads to the conclusion that the Gmail network follows Power-law distribution, which is usually seen in real-world networks. An extension to the power-law distribution is scale-free property, which is also observed.

•	From Fig 2.5 and Table 4, it follows that ashwani.mcs19.du@gmail.com and supriya.mcs19.du@gmail.com had a higher weighted in-degree while yatin.mcs19.du@gmail.com had a higher weighted-out degree than the former email addresses. For a social/communication network, it may follow that the user for this email address is more likely to spread information/ express his ideas to gain wider attention. Also, supriya.mcs19.du@gmail.com and ashwani.mcs19.du@gmail.com can be analogous to authority nodes (nodes with many incoming edges from many hub nodes), and yatin.mcs19.du@gmail.com it can be analogous to a hub node that is a node with many outgoing edges to important nodes (authority nodes). Hence, this email address is highly likely to be an initiator of events, the target of which shall be the authority nodes.

•	From Table 5, it has been observed that vb.ducs@gmail.com is a mutual sender for yatin.mcs19.du@gmail.com and ashwani.mcs19.du@gmail.com while it happens to be a mutual recipient of mails from all the 3 group members.

•	Degree distribution in Fig 2.6 recapitulates the fact that the given distribution represents a star graph, wherein out of ‘n’ nodes, the one central node has degree equals (n-1), and the remaining (n-1) nodes have degree precisely 1.

•	In addition to the above inference, we can also conclude that the real-world network exhibits small-world behavior, i.e., μL log n. From Table 3, it follows:
-	At n = 72, μL = log (72) = 1.857
-	At n = 77, μL = log (77) = 1.886
-	At n= 112, μL = log (111) = 2.049
Hence, small world behavior is thus satisfied.
 
•	All the above inferences are the properties of the real-world network, and it hence points towards a unified conclusion that Gmail networks belong to the class of real-world networks.


One final word of the conclusion is that while working with real-world data can be a fascinating process, it needs appropriate data pre-processing before performing subsequent analysis. However, within the limits of real-world characteristics, it is equally learning as well as challenging to work with real-world data.






5.	REFERENCES

1.	http://people.du.ac.in/~vbhatnagar/#teaching
2.	http://networksciencebook.com/
3.	https://dataminingbook.info/book_html/chap4/book-watermark.html
4.	https://networkx.github.io/documentation/networkx-1.9/
5.	https://networkx.github.io/documentation/stable/reference/classes/generated/networkx.Graph.degree.html
6.	https://networkx.github.io/documentation/latest/_downloads/networkx_reference.pdf
