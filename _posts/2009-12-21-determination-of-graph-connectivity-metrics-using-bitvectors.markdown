---

title: Determination of graph connectivity metrics using bit-vectors
abstract: Determination of a connectivity-metrics for graphs representative of networks of interest. A graph that represents a network of interest is accessed. The graph includes nodes representing points in the network of interest, and edges corresponding to the nodes. Bit-vectors are generated corresponding to the nodes and/or edges, wherein individual bits in the bit-vectors respectively provide a logical indication of connectedness. The connectivity-metric is then determined by applying a logical bit operation to the plurality of bit-vectors. Examples of connectivity metrics include a connected components, shortest paths, betweenness, clustering, and tree-based determinations.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08145588&OS=08145588&RS=08145588
owner: Unisys Corporation
number: 08145588
owner_city: Blue Bell
owner_country: US
publication_date: 20091221
---
This application is a divisional of U.S. Ser. No. 11 498 024 filed on Aug. 2 2006 now U.S. Pat. No. 7 672 919.

This invention relates generally to graph analysis and more particularly to bit vector algorithms for graph processing.

Graph analysis plays a critical role in data mining that involves transactional activity social networks and communications. Much of this analysis uses connectivity metrics such as betweenness and closeness to characterize highly connected nodes intermediaries or hubs of activity. Calculating these metrics requires finding such graph properties as connected components or shortest paths. The processing required to find all connected components or shortest paths for a large graph is very expensive making real time interactive analysis infeasible.

One connectivity metric is referred to as connected components which may be determined using recursive functions in conventional systems. An unrestricted recursive process commences by setting all of the nodes in a graph to UNVISITED and selecting any UNVISITED node as a starting point. The selected node is then marked as VISITED and a depth first search of all connected nodes that are also UNVISITED is performed marking each node encountered in the search as VISITED. This searching is continued until no more UNVISITED nodes can be found in this component. The next component s starting point is found by searching the graph for remaining UNVISITED node s . The process is then repeated until all nodes in the graph are marked VISITED. The depth first search is implemented as a recursive function. This implementation runs very quickly but may cause a stack overflow if the graph is too large.

An alternative implementation of the unrestricted recursive algorithm is one that restricts the recursive depth to avoid stack overflow errors. This implementation is considerably slower than the unrestricted version but will produce the same results as long as the recursive depth allowed is greater than or equal to the graph s diameter. A graph s diameter is defined as the number of edges in the longest shortest path of the graph. This definition guarantees a finite diameter even in graphs with unconnected components. If the restricted recursive depth is shorter than the diameter the algorithm will fail not being able to connect these components.

Accordingly existing algorithms for determining connected components are variously inefficient particularly with regard to graphs of relatively large diameter. Other connectivity metrics include shortest paths betweenness clustering and Steiner Tree. Techniques are also known for determining these connectivity metrics but they too are variously deficient for larger graphs.

Accordingly what is needed are techniques for determining connectivity metrics that are less computationally expensive than existing techniques and that are more readily extensible to graphs of relatively large diameter.

The present invention provides fast bit vector solutions for finding graph properties with significant reduction of the computational time required as compared to conventional techniques.

According to one aspect embodiments of the present invention determine a connectivity metric for a graph representative of a network of interest. A graph that represents a network of interest is accessed. The graph includes nodes representing points in the network of interest and edges corresponding to the nodes. Bit vectors are generated corresponding to the nodes and or edges wherein individual bits in the bit vectors respectively provide a logical indication of connectedness. The connectivity metric is then determined by applying a logical bit operation to the plurality of bit vectors.

One example of a connectivity metric is a connected components determination. Determining the connectivity metric for that example involves iteratively applying a bit wise OR operation to bit vectors that indicate connectedness between respective nodes. The number of iterations required until there is no additional change in the updated bit vectors determines a measurement of connectivity i.e. the diameter of the graph . The number and size of connected components are also evident from the updated bit vectors.

Another example of a connectivity metric is a shortest path determination. There determining the connectivity metric includes iteratively applying a bit wise logical operation to the bit vectors that indicate connectedness between respective nodes until the updated bit vectors have no additional change. The distances between respective nodes are then determined by searching the updated bit vectors and the shortest path between nodes is determined based upon those distances.

In still another example the bit vectors are edge bit vectors and the connectivity metric is a betweenness determination. This metric is determined by iteratively applying a bit wise logical operation to the bit vectors that are coincident with the nodes of each edge to produce updated bit vectors until there is no additional change.

In still another example the connectivity metric is a clustering determination and determining the connectivity metric uses the bit vectors to determine a clustering coefficient of a clustering algorithm.

Various networks of interest may also be analyzed including but not limited to social networks transactional activity networks and communications networks.

The present invention can be embodied in various forms including business processes computer implemented methods computer program products computer systems and networks user interfaces application programming interfaces and the like.

In the following description for purposes of explanation numerous details are set forth such as flowcharts and system configurations in order to provide an understanding of one or more embodiments of the present invention. However it is and will be apparent to one skilled in the art that these specific details are not required in order to practice the present invention.

Bit vectors are a distributed representation of an adjacency matrix commonly used to represent graphs. The bits in a bit vector represent graph nodes but the bit vectors can represent either nodes or edges e.g. edge econnects nodes nand n . A node bit vector is simply a row from the graph s adjacency matrix. An edge bit vector represents the nodes that are within some number of edges from a particular edge. Node bit vectors v n are a distributed form of an adjacency matrix. The adjacency matrix is an n n matrix. The first n represents a row and the n within the brackets represent the column. A given vector is represented in a row with the column values respectively representing the values in the vector. The variable i designates the number of iterations applied to the bit vector. Each node bit vector represents a particular graph node and its connectivity to all other graph nodes. Each bit position represents a node in the graph. A node s bit vector has logical indications indicating connections to other nodes. Thus there are 1 values for all nodes directly connected to this node and 0 values in the absence of connections as shown in .

Depending on the application nodes can be considered reflexive connected to themselves or not. The examples described herein consider nodes to be reflexive but the same principles of the present invention may be applied to non reflexive nodes.

Edge bit vectors e n represent an edge and the nodes that are connected by that edge. is a graphical diagram illustrating an example of a graph and corresponding edge bit vector . As with node bit vectors n designates a particular node index in the bit vector and i designates the number of iterations applied to the bit vector. Edge bit vectors are edge centric not node centric like node bit vectors but both provide unambiguous descriptions of a graph.

Before proceeding with further description of bit vector algorithms for determining connectivity metrics according to various aspects of the present invention it is noted that it has been determined that the processing time required for the bit vector algorithms is closely tied to a graph s diameter. Since it is expensive to find the diameter of a graph for certain smaller groups traditional algorithms such as recursive algorithms will be more efficient. However for the vast majority of potential networks of interest it is believed that the bit vector algorithms of the present invention will consume fewer computing resources both in terms of calculation and memory.

The present invention is applicable to a variety of potential networks of interest including but not limited to social networks transactional networks and communications networks. The modeling of networks may also be variously provided. For example social networks may be modeled using graphs that fit the small world model described in Newman M. E. J. Models of the Small World A Review 2000 . Small world models like co authorship networks are graphs where typically the average node degree is greater than 3 and the graph diameter is less than 20. Additional examples of networks of interest include Internet domain level movie actors co authorship and a power grid. See Albert R. and A. L. Barabasi Statistical Mechanics of Computer Networks June 2001 for information including the average degree of such networks. 

The graph analysis application runs on a conventional operating system in memory and carries out the described functionality by execution of computer instructions. The application may make use of various execution platforms including but not limited to those implementing Java applets. The artisan will readily recognize the various alternative programming languages and execution platforms that are and will become available and the present invention is not limited to any specific execution environment.

Although the graph analysis application is preferably provided as software it may alternatively be hardware firmware or any combination of software hardware and firmware. Although one modular breakdown is described such is provided by way of example only as the functionality of the graph analysis application may be provided in any number of alternative designs having greater fewer or differently named component modules.

In one embodiment a computer system includes the graph analysis application resident in memory on a conventional computer system with the graph analysis application including instructions that are executed by a processor. Alternative embodiments include an article of manufacture wherein the instructions are stored on a computer readable storage medium. The medium may be of any type including but not limited to magnetic storage media e.g. floppy disks hard disks optical storage media e.g. CD DVD and others. Still other embodiments include computer implemented processes described in connection with the graph analysis application as well as the corresponding flow diagram and other figures.

The graph analysis application includes a database module a graph management module a bit vector generation module and a connectivity metric determination module .

The database module stores and maintains information corresponding to a network of interest. Examples include but are not limited to a company e mail database a journal bibliography for authors that co author papers social networks etc. Although the database module is shown to reside within the graph analysis application it should be understood that a large database may be separately stored for access by the graph analysis application and as such the illustration is merely to indicate that the data is accessible by the graph access application . Also the database may be variously accessible such as through a network.

The graph management module accesses and maintains graph data for a currently analyzed network of interest. In that regard the graph management module accesses information in the database module and organizes and maintains the nodes and connections between nodes for a graph corresponding to the network of interest. The graph data corresponds to any network of interest for which graph information is available or extractable. Conventional techniques may be used to extract a graph from a given network depending upon how the information is stored. For example a graph is extracted from a database of e mails by identifying the addresses for the various senders and recipients and building the graph accordingly.

The bit vector generation module is in communication with the graph management module and thus accesses the graph information. The bit vector generation module generates a plurality of bit vectors for the graph. These bit vectors may include node bit vectors and or edge bit vectors as previously described. The bit vectors may be generated according to the technique described above wherein logical one represents a connection and logical zero represents that absence of a connection for the respective elements of the node or edge bit vectors.

The connectivity metric determination module determines connectivity metrics for the graph representative of the network of interest. Preferably this is accommodated by applying logical operations and other processing to the bit vectors. This processing is described in further detail below with regard to the various examples of connectivity metrics. The connectivity metrics include connected components shortest path betweenness clustering and tree based determinations.

In addition to the described modules the graph analysis application includes conventional facilities for interfacing with the user including but not limited to display as well as keyboard and cursor based input.

The graph that represents the network of interest is then accessed such as through access to the data in the above described database. The graph may be represented in the form of data that defines the nodes and connections between the nodes.

Bit vectors respectively corresponding to the nodes and or edges in the graph are then generated . The determination of the type of bit vector to generate may be contingent upon the desired type of connectivity metric as will be understood from the descriptions below.

The selected connectivity metric for the graph is determined by processing the bit vectors. This processing may include various operations preferably including at least one logical operation. The processing may be an iterative such that updated bit vectors corresponding to the graph are generated based upon previous iterations or combinations of previously generated bit vectors. The various processing of the bit vectors for the different types of connectivity metrics is described further below.

Once the calculations have been completed the results are displayed for the user again using common techniques for interfacing with the user.

The various examples of bit vector generation and corresponding connectivity metric determination performed by the graph analysis application are further described as follows.

A connected component of a graph is a sub graph of nodes that are connected to each other by at least one edge. Because no connectivity exists across connected components these sub graphs can be isolated for subsequent analysis. In social network analysis for example the number and size of connected components can be used to characterize the relationships represented by a graph.

For relatively large graphs the bit vector algorithm of the present invention is more robust and more efficient than conventional recursive algorithms for determining connected components.

This OR process continues until the bit vectors stop changing which in this simple example happens in v . The two different vector values in represent the two components and show which nodes belong to each component. Because the process stops in the diameter of this graph is also now known to be two.

The unrestricted recursive algorithm is much faster than either the restricted recursive or bit vector algorithms but it is limited to small graphs. The performance times of the restricted recursive and bit vector algorithms are compared in and . Random graphs were generated to review expected performance. Random graphs were used because they can be quickly generated and because they model some though obviously not all networks of interest. Random graphs are also useful for illustrating effectiveness because they can be characterized by their average degree average number of edges incident on graph nodes and their diameter length of the longest shortest path in the graph . is a graph illustrating how increasing the number of nodes with the number of edges fixed affects execution time. is a graph illustrating how changing only the number of edges affects execution time.

 Shortest paths is another common connectivity metric. One conventional algorithm for finding the shortest path from all nodes in a graph to all other nodes is known as Floyd Warshall s F W algorithm.

The F W algorithm is a simple algorithm that operates on two Narrays of integers. One is the Distance matrix D N N and the other is the Intermediate matrix I N N . At the completion of the algorithm the Distance matrix will contain the distance from any node x to any other node y D x y and the Intermediate matrix will contain the path to take from node x to node y through the intermediate node k k I x y .

A problem with the F W algorithm is that it requires two Narrays of integers. These arrays are too large for typical application memory constraints such as Java application memory when Nis very large. The bit vector shortest path determination according to this aspect of the present invention mitigates the memory problem. The bit vector algorithm begins with the same expansion steps that were used to find connected components as described above. As with connected components expansion is continued until the bit vectors stop changing.

The distance from node x to node y can be found by searching x from n 1 incrementing n until bit y in x is ON. The distance from x to y is then n. Of course if x is the same as y the distance is zero. Unlike the F W algorithm where the distance can be immediately found in D x y the bit vector algorithm requires a search but can handle much larger graphs.

Finding the shortest path from node x to node y is a bit more complex. This is accomplished by initially finding the distance dbetween these nodes as explained above. The following steps find the shortest path from x to y 

Clustering algorithms are used to find groups of nodes that are highly interconnected. The concept of betweenness has been introduced as a more global measure of a node s involvement in a network of interactions. Clustering algorithms generally use information from the local neighborhood of a node to identify clusters. Betweenness on the other hand determines the centrality of paths within a network and ranks nodes based on the paths that pass through them.

The best connected scientist BCS algorithm was described in a work by Newman M. E. J. Who is the Best Connected Scientist A study of scientific co authorship networks June 2001 . The BCS algorithm can be described with the following analogy. Envision the co authorship graph as a roadmap where each author is a town node and the papers they co authored are the roads edges connecting the towns. The distance between any two towns on a particular road is the number of authors for the paper represented by that road. This means that papers with only a few authors are represented as shorter roads representing the closer ties that are likely to exist among smaller groups. Papers with only one author are ignored because they do not represent connections within the community.

Using this roadmap analogy if each town begins with a population equal to the number of towns and each person in each town travels to a unique destination town always using the shortest path then the best connected town will be the town with the most travelers entering it although it is arbitrary whether the traveler is tallied when entering or leaving the town.

It is important to understand the difference between connectedness and betweenness. Although the BCS algorithm s name includes the word connected it is really measuring betweenness. Authors ranked highly by the BCS algorithm are sometimes not directly connected to many people. Instead they often act as a bridge or conduit between groups that are internally highly connected but go through the conduit to get to other groups.

The bit vector implementation of the BCS algorithm according to this aspect of the present invention uses an edge bit vector representation as described above. As an example consider the graph in containing nodes and edges a f and its corresponding edge bit vectors in column e of the bit vector table illustrated in .

The algorithm proceeds from e to e by applying a logical OR operation to all of the edge bit vectors coincident with the end nodes of each edge. For example edge a has end nodes and . Edges e and f are also coincident with node and edge b is also coincident with node . Therefore for edge a e OR e OR e OR e . This process continues until all of the bit vectors stop changing that is e e . In the illustrated example this condition would be represented where e would be equal to e .

As illustrated in the bit vector table there are columns for four bit vectors corresponding to the nodes . As can be seen all of the edge bit vectors are coincident with the end nodes of each edge at e .

Because information about the graph s connectivity spreads with each step in this process the shortest paths and BCS tallies are done in the same pass. This factor and the fast OR operations provide for efficient determinations. The bit vector BCS algorithm has been determined to be significantly better than traditional implementations in analysis of experimental results.

Clustering algorithms are used in graph analysis to measure the level of connectivity within a graph. These algorithms can be used to measure the global or average connectivity across an entire graph or the local connectivity to find regions of a graph that are more or less densely connected than the rest of the graph.

The example of a clustering algorithm to be calculated using the bit vectors implements the clustering coefficient C defined by Equation 1. The clustering coefficient is three times the number of fully connected groups of three nodes triangles divided by all possible triples nodes that are directly connected to two distinct other nodes .

Consider the graph shown in which illustrates nodes and related edges. By inspection this graph has two triangles and . The number of triples can be found by summing

The bit vector representation is used to calculate the clustering coefficient as follows. From the graph in the node bit vectors v are generated as shown in the bit vector table of which identifies the nodes and corresponding bit vectors .

This code uses the cardinality clone and methods that can be performed on Java BitSet objects to find connected pairs of nodes that share other common nodes forming triangles. The clustering coefficient can then be found by dividing the number of triangle nodes by the number of triples as shown in Equation 3.

Steiner Tree is the lowest cost tree that connects all of a set of pre selected terminal nodes. Finding Steiner Trees is a classic graph analysis problem because it requires global optimization and like the Traveling Salesman Problem has many practical applications.

Finding a Steiner Tree for a given set of pre selected nodes in a given graph can be solved in polynomial time in cases where two three or all nodes are terminal nodes.

Unlike finding a shortest path between nodes a Steiner Tree minimizes the link cost required to connect the terminal nodes and is not in general the same as the shortest paths.

If nodes and in the graph are terminal nodes then the Steiner Tree contains edges a b and c with a total cost of 5 not link d which is the shortest path between nodes and .

To find a Steiner Tree using bit vectors the link weights are discretized and replaced with a series of un weighted links as shown in the graph in are shown in the bit vector table shown in which denotes the nodes column and corresponding bit vectors columns . For graphs with un weighted links or links that are already discrete bit vectors can find an exact Steiner Tree solution. For graphs with continuously weighted links the solution will be an approximation.

The bit vector algorithm starts with a node bit vector representation of the discretized un weighted graph. The bit vectors for the graph in are shown in . Each node s bit vector is then logical OR d with the bit vectors of other nodes that are connected to that node. This process is repeated expanding the neighborhood of each node until one node has all of the terminal nodes as 1 s in its vector. This node represents the center of mass for the terminal nodes. The steps of this process are reflected in the bit vector table . Nodes and both reach the end condition with 1 s for nodes and in column . Either node can be selected for the next step.

The nodes with 1 s in band their interconnecting edges are referred to as the Super Steiner Tree because these nodes and edges are a super set of the desired Steiner Tree. These additional nodes and edges are pruned in the next step.

The Super Steiner Tree is pruned by finding the shortest path from each terminal node to its nearest neighbor terminal node according to the shortest path technique described above and keeping track of which nodes and edges are traversed in the process. Any nodes and edges not traversed by the end of this process are then pruned leaving the Steiner Tree. In the example from no pruning is required. The resulting Steiner Tree includes Nodes and with Nodes and as Steiner nodes.

The Steiner Tree will include all the original terminal nodes additional nodes needed to interconnect the original terminal nodes these additional nodes are called Steiner nodes and the minimum edges required. All tie solutions will be included using this process. Ties can be found by searching the resulting Steiner Tree for cycles.

Only connected graphs can contain a Steiner Tree. For this reason a test should be included that stops the algorithm when the graph s diameter is discovered before all terminal nodes are encountered.

The complexity of finding the Super Steiner Tree is similar to that of the connected component algorithm where the maximum distance between any two terminal nodes is considered the diameter. The complexity of the pruning step is O n where n is the number of terminal nodes.

For those embodiments using Java applets the bit vector implementation may use the BitSet object supported by the Java JDK. Bit vectors offer significant speed improvements over standard algorithm implementations because many iterative node by node operations are replaced by faster logical bit operations.

The various bit vector implementations also scale up well to large graphs especially small world social network type graphs that are highly clustered with small diameters.

Bit vectors can be easily adapted to applications with un directed and un weighted graphs. Directed graphs can also be represented by only putting 1 s in source node bit vectors. Finally weighted graphs can be represented as shown in the discussion on Steiner Trees.

Thus embodiments of the present invention accommodate the determination of connectivity metrics using bit vectors. Although the present invention has been described in considerable detail with reference to certain embodiments thereof the invention may be variously embodied without departing from the spirit or scope of the invention. Therefore the following claims should not be limited to the description of the embodiments contained herein in any way.

