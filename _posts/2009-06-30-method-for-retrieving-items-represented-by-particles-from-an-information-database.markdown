---

title: Method for retrieving items represented by particles from an information database
abstract: A set of words is converted to a corresponding set of particles, wherein the words and the particles are unique within each set. For each word, all possible partitionings of the word into particles are determined, and a cost is determined for each possible partitioning. The particles of the possible partitioning associated with a minimal cost are added to the set of particles.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08055693&OS=08055693&RS=08055693
owner: Mitsubishi Electric Research Laboratories, Inc.
number: 08055693
owner_city: Cambridge
owner_country: US
publication_date: 20090630
---
This application is a continuation in part of U.S. patent application Ser. No. 12 036 681 Method for Indexing for Retrieving Documents Using Particles filed by Ramakrishnan et al. on Feb. 25 2008.

This invention relates generally to information retrieval and in particular to retrieving of items represented by particles.

Information retrieval IR systems typically include a large list of items such as geographic points of interest POI or music album titles. The list is accessed by an index. Input to the index is a query supplied by a user. In response to the query the IR system retrieves a result list that best matched the query. The result list can be rank ordered according various factors. The input list of items index query and result list are typically represented by words. The input list of items query and result list originates from text or speech.

Spoken queries are used in environments where a user cannot use a keyboard e.g. while driving or the user interface includes a microphone. Spoken document retrieval is used when the items to be retrieved are audio items such as radio or TV shows. In those environments an automatic speech recognizer ASR is used to convert speech to words.

The ASR uses two basic data structures a pronunciation dictionary of words and a language model of the words. Usually the IR system represents the words phonetically as phonemes e.g. RESTAURANT is represented as R EH S T R AA N T. Phonemes refer to the basic units of sound in a particular language. The phonemes can include stress marks syllable boundaries and other notation indicative of how the words are pronounced.

The language model describes the probabilities of word orderings and is used by the ASR to constrain the search for the correct word hypotheses. The language model can be an n gram. If the n grams are bigrams then the bigram lists the probabilities such as P BELL TACO which is the probability that the word BELL follows the word TACO. The language model can also be a finite state grammar where the states in the grammar represent the words that can appear at each state and the transitions between states represent the probability of going from one state to another state.

First important words for the IR are typically infrequent identifier words. For example in an item POI MJ S RESTAURANT the important identifier word is MJ S. Frequently these identifier words are proper nouns from other languages. For example the word AASHIANI in the item AASHIANI RESTAURANT is from the Hindi language. Another way these identifier words emerge is through combination as with GREENHOUSE. Modifying the roots of words also increases the size of the vocabulary. In general the number of infrequent but important identifier words is very large.

In addition important identifier words are often mispronounced or poorly represented by the language model. Accurate statistics for the n grams also are generally unavailable. Hence the probability of recognizing important infrequent words is low and the word sequences are often incorrect. This leads to poor recall performance by the IR system.

Second the computational load for word based IR systems increases with the size of the list and index and the performance of system becomes unacceptable for real time retrieval.

The embodiments of the invention provide a method for retrieving items in an information retrieval IR database represented by particles. The number of unique particles is much smaller than the number of unique words e.g. smaller by an order of magnitude. This improves the performance of an automatic speech recognition ASR system leading to a decrease in recognition time by as much as 50 . Surprisingly even though the number of particles is decreased dramatically when compared with the number of words and the throughput increases likewise the performance of IR system measured by the recall rate is improved by as much as 2 .

As shown in embodiments of our invention provide a method for retrieving items from a database in an information retrieval IR system . The steps of the method operate in a processor as known in the art. The processor includes memory and I O interfaces.

The IR system includes a list of items represented by words. From the word based list we generate a list of items represented by particles. The correspondence between the items in the word based list and the items in the particle based list can be one to one or one to many when alternative pronunciations of the words are possible. As shown in the input list of items can originate from text speech or both text and speech.

Particles are well known in the field of speech recognition. As defined herein a particle represents a concatenated phoneme sequence. A string of particles represents the phoneme sequence for a word see Whittaker et al. Particle based language modelling International Conference on Speech and Language Processing ICSLP 2000.

Up to now particles have only been used to recognize words in an automatic speech recognizer ASR system. In contrast the invention uses particles to perform information retrieval IR .

We apply an indexer to the list to produce a particle based index . To retrieve items a particle based query is acquired from a user . The query can be derived from words in text or speech using the ASR.

The query is used to look up the index constructed from the particle based list . The output in response to the query is a result list of items from the word based list that correspond to the best matching items in the particle based list .

To generate the particle based list in a preprocessing step we maintain a set of unique words in the list . We convert the word based set to a set of unique particles . After we obtain the particle based set we can translate the words for the items in the list to the corresponding particle based items to generate the particle based list .

If an item in the word based list has multiple pronunciations then a Cartesian product of all possible partitioning into particles for all the words is formed and enumerated in the particle based list. For example if AASHIANI can be partitioned into particles as AA SH IY AA N IY or as AA SH Y AE N IH and RESTAURANT into particles as R E S T R AA N T or as R E S T ER R AA N T then all possible partitionings are enumerated in the particle based index 

Our language model includes particles e.g. an n gram language model that includes statistics on particle n grams.

The method of generating the particle based list from the word based list according the following ideas 

We achieve about a ten fold reduction in size which improves IR retrieval throughput by about 50 while at the same time increasing the recall performance by 2 .

The table is initialized with a row for each initial particle . In this example the table includes three initial particles AW R G L AE S AW R and G L AE S. The method attempts to partition each original particle into smaller particles.

The table contains data structures to keep track of original particles and particles added to the table. In addition the table contains data structures that indicate how the original particles were partitioned into smaller particles.

The Original Word column indicating whether the word was in the list or not. The Particle column indicating whether the word was partitioned into particles or not. The Partition Location column indicates where the partition was made. The Frequency column indicates the frequency of occurrence c of the particle. The length column indicating the length l of the particle in terms of phonemes.

Initially the frequencies c are obtained from the frequencies of the corresponding words in the list . If an original particle is partitioned the frequency count of the original particle is propagated to the new particles in the following manner. If the new particle does not exist in the table then its frequency is set to the frequency of the parent particle. If the new particle already exists in the table then its frequency is incremented by the frequency of the parent.

The current set of particles is evaluated using a minimal description length MDL cost which is the sum of a likelihood cost and an inventory cost . The inventory cost represents the size of the particle set. The goal of the method is to select a partitioning the words into particles that reduces the overall MDL cost. The method terminates for example after the set contains a desired number of particles.

The likelihood cost decreases if the frequency of the particle occurrence increases. As a result the method favors partitionings important infrequently occurring words into more frequently occurring particles.

The cost is the sum of the lengths of all the particles in the set in terms of phonemes weighted by a log probability of each phoneme. In one embodiment we assume that all phonemes are equally likely 

The inventory cost decreases when the number of unique particles and their length decreases. As a result our cost favors partitionings infrequent words into smaller and fewer particles. The inventory cost is a compressive cost to achieve the task of partitioning the words into particles such that the number of unique particles in the set is much much smaller than the number of unique words in the set .

Our size reduction is about an order of magnitude which leads to a 50 increase in throughput and a 2 increase in the accuracy of the recall rate.

Partitioning Evaluation The likelihood cost effectively evaluates possible partitionings of a word into particles. A word is converted to particles that have higher probabilities. In general a number of different evaluations are possible. For example we can evaluate a particular partitioning in terms of 

Inventory Evaluation The inventory cost evaluates the particles in the list biasing the construction a list with fewer particles and fewer phonemes. A number of alternative index evaluation procedures can be used for example a desired distribution of particles in terms of their frequencies lengths similarity or inverse document frequency IDF in the word index.

MDL Evaluation The MDL Cost evaluates the sum of the likelihood cost and the inventory cost. A number of alternative combinations of Likelihood and inventory cost can be used for example 

Using a greedy search procedure or a depth first search DFS to evaluate partitions of a word that minimizes the MDL cost. Alternatives include 

The input is the set . For each unique word in the list the original word particle frequency and length in terms of phonemes are supplied for determining costs.

For each unique word all possible partitionings into particles prefix and suffix are determined. A sum of the inventory cost and the likelihood cost is determined for each possible partitioning . The particles of the possible partitionings having a minimal sum are added to the set . If a partitioning of an original word particle is not performed it is still considered an intact particle.

After all the words have been processed a termination can be tested e.g. the set has the desired number of particles and the method terminates if true. Otherwise if false proceed by re processing all the original word in the table in a new random order iteratively until termination.

Although the example application is described for an information retrieval system the embodiments of the invention can be used for any application were the database includes words and it makes sense to translate the words to particles. For example automatic speech recognition ASR systems are a good candidate application.

Particularly ASR systems are constrained in what they can recognize by the items contained in the pronunciation dictionary. If a spoken word is not in the dictionary the ASR system is unable to recognize the word. This out of vocabulary OOV word can now be recognized by particles in the pronunciation dictionary because particles offer more flexibility as to how the ASR system matches the speech to the items in then pronunciation dictionary.

The invention can also be used with any word based search engine where the input is either text or speech and the items to be retrieved are text or speech.

Although the invention has been described by way of examples of preferred embodiments it is to be understood that various other adaptations and modifications can be made within the spirit and scope of the invention. Therefore it is the object of the appended claims to cover all such variations and modifications as come within the true spirit and scope of the invention.

