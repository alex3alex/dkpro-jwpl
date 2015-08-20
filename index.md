---
#
# Use the widgets beneath and the content will be
# inserted automagically in the webpage. To make
# this work, you have to use › layout: frontpage
#
layout: frontpage
title: "DKPro JWPL and the Wikipedia Revision Toolkit"
---

JWPL (Java Wikipedia Library) is a free, Java-based application programming interface that allows to access all information in Wikipedia.

Core features:
 * Fast and efficient access to Wikipedia
 * Parser for the !MediaWiki syntax
 * Language independent

In addition to the core functionality, JWPL allows access to Wikipedia's edit history with the Wikipedia Revision Toolkit.

Features of the Wikipedia Revision Toolkit:
 * Tools for reconstructing past states of Wikipedia (TimeMachine)
 * Efficient access to all article revisions (RevisionMachine)
 * Dedicated revision storage format

More detailed information can be found in the [JWPLDocumentation documentation] .

Learn about the [HowToGetJWPL different possibilities to get and use JWPL]

Any questions should be posted to the [http://groups.google.com/group/jwpl JWPL Mailing List].


### How to cite?

If you use the Wikipedia Revision Toolkit (RevisionMachine, TimeMachine) in scientific work, please cite the ACL 2011 demo paper:
> Oliver Ferschke and Torsten Zsch and Iryna Gurevych (2011). Wikipedia Revision Toolkit: Efficiently Accessing Wikipedia’s Edit History. In: Proceedings of the ACL-HLT 2011 System Demonstrations. [(pdf)][ACL_2011] [(bib)][ACL_2011_BIB]
  
If you only use JWPL Core (API, !DataMachine), please cite the LREC 2008 paper: 
> Torsten Zesch and Christof Müller and Iryna Gurevych (2008). Extracting Lexical Semantic Knowledge from Wikipedia and Wiktionary. In: Proceedings of the 6th International Conference on Language Resources and Evaluation. [(pdf)][LREC_2008] [(bib)][LREC_2008_BIB]

### Code example

{{{
// configure the database connection parameters
DatabaseConfiguration dbConfig = new DatabaseConfiguration();
dbConfig.setHost("SERVER_URL");
dbConfig.setDatabase("DATABASE");
dbConfig.setUser("USER");
dbConfig.setPassword("PASSWORD");
dbConfig.setLanguage(Language.german);

// Create the Wikipedia object
Wikipedia wiki = new Wikipedia(dbConfig);
        
String title = "Hello world";
Page page = wiki.getPage(title);
        
// the title of the page
System.out.println("Queried string       : " + title);
System.out.println("Title                : " + page.getTitle());

// whether the page is a disambiguation page
System.out.println("IsDisambiguationPage : " + page.isDisambiguation());
        
// whether the page is a redirect
// If a page is a redirect, we can use it like a normal page.
// The other infos in this example are transparently served by the page that the redirect points to. 
System.out.println("redirect page query  : " + page.isRedirect());
        
// the number of links pointing to this page
System.out.println("# of ingoing links   : " + page.getNumberOfInlinks());
        
// the number of links in this page pointing to other pages
System.out.println("# of outgoing links  : " + page.getNumberOfOutlinks());

// the number of categories that are assigned to this page
System.out.println("# of categories      : " + page.getNumberOfCategories());
}}}

### About

This project was initiated under the auspices of Prof. Dr. Iryna Gurevych, [Ubiquitous Knowledge Processing Lab (UKP)](http://www.ukp.tu-darmstadt.de/), Technische Universität Darmstadt.

It is now maintained by 
 * [http://www.langtech.inf.uni-due.de/team/personal-profile-torsten-zesch/ Torsten Zesch], Language Technology Lab, University of Duisburg-Essen
 * [http://www.ferschke.com Oliver Ferschke], Language Technologies Institute, Carnegie Mellon University
 * [http://www.ukp.tu-darmstadt.de/people/richard-eckart-de-castilho Richard Eckart de Castilho], UKP Lab, Technische Universität Darmstadt
 * [http://www.ukp.tu-darmstadt.de/people/johannes-daxenberger Johannes Daxenberger], UKP Lab, Technische Universität Darmstadt

### License

GNU Lesser GPL.

[ACL_2011]: http://aclweb.org/anthology/P/P11/P11-4017.pdf
[ACL_2011_BIB]: http://www.aclweb.org/anthology/P/P11/P11-4017.bib
[LREC_2008]: http://www.ukp.tu-darmstadt.de/fileadmin/user_upload/Group_UKP/publikationen/2008/lrec08_camera_ready.pdf
[LREC_2008_BIB]: http://www.ukp.tu-darmstadt.de/publications/details/?no_cache=1&tx_bibtex_pi1%5Bpub_id%5D=TUD-CS-2008-4