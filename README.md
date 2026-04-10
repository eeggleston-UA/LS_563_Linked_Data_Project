## LS 563 Linked Data Project -- SF Dataset

### (A)	About the science fiction (SF) project dataset
The project dataset contains approximately sixty SF book titles. All authors are Hugo Award recipients. The titles were drawn from the Seattle Library Collection Inventory, freely available in CSV format on Kaggle.com. Forming the final dataset required substantial cleaning and normalization, although most original bibliographic data was retained. The project intention was to work with a realistic, catalog-based, public library dataset, to be eventually converted into linked data. The resulting dataset contains fewer subject terms and total fields than the original, but maintains the character of the Seattle Library bibliographic data. 

### (B)	Ontology(ies) and controlled vocabularies used
To convert this SF bibliographic dataset into linked data, the Library of Congress (LC) BIBFRAME environment was selected. This means the central ontology is BIBFRAME, and BIBFRAME provided the vocabularies for most elements. An important exception was the use of VIAF. This name authority (controlled vocabulary) file group from OCLC was used for author URIs—but still in the BIBFRAME context. Subject URIs were drawn from LC Subject Headings (LCSH) as another controlled vocabulary. I also used the BIBFRAME LC Extension Ontology for the publisher literal. With the exception of the external name authority source, the project is LC and BIBFRAME-based.

### (C)	Linking strategy
As the project is largely BIBFRAME-based, this is reflected in the linking strategy. Conceptually, the BIBFRAME Work is the hub of the linked data model, with the Instance as a strong secondary center. In my model, there are also Items linked to each Instance. These three levels—Work, Instance, Item—outline the basic BIBFRAME structure, as data is linked in descending levels of abstraction. My strategy follows this outline.

Following the BIBFRAME pattern, my titles (literal), subjects (URI) (LCSH), authors (URI) (VIAF), and Instances (URI) radiate from each Work. The Instance reflects the next level down, as with a “particular published form,” and so literals like ISBN, publisher, media type, and publication year are linked at this level. Also linked to each Instance, as representing actual books or audiobooks, are the Item nodes. The literals attached to these Item nodes, for item location and collection, conceptually represent physical items and places. In this pattern, then, my linking strategy reflects the BIBFRAME levels of Work, Instance, and Item. The bibliographic data from my dataset is assigned a place according to this hierarchy, or level of abstraction (as noted above).	

The choices listed for URIs and literals also reflect an adaptation of my dataset to a BIBFRAME linking structure. Each BIBFRAME Work is identified by a dataset literal. Subject URIs are drawn from LC, to align with this linking environment. VIAF provided a broad selection of author URIs that could be reconciled through OpenRefine. Literals were chosen for the remaining data points, as this appropriately matches their BIBFRAME structural level, as described above: as fitting a level of abstraction, and arranged by a BIBFRAME class and property form.

### (D) Sample Triples

1.
_Readable:_
```
BIBFRAME Instance		-->     has property / is identified by   -->    BIBFRAME ISBN
```
_Turtle (without prefixes):_
```
bf:Instance	    bf:identifiedBy		  bf:Isbn  
```
_N-Triples:_

\<https://id.loc.gov/ontologies/bibframe/Instance> \
\<https://id.loc.gov/ontologies/bibframe/identifiedBy>  \
\<https://id.loc.gov/ontologies/bibframe/Isbn>  .

2.
_Readable:_
```
BIBFRAME ISBN		-->     has property / actual value    -->     	"9780425190449"  /  literal ISBN
```
_Turtle:_
```
bf:Isbn	      rdf:value	     "9780425190449"^^xsd:integer
```
_N-Triples:_

\<https://id.loc.gov/ontologies/bibframe/Isbn>  \
\<http://www.w3.org/1999/02/22-rdf-syntax-ns#/type/value>  \
\"9780425190449"  .


