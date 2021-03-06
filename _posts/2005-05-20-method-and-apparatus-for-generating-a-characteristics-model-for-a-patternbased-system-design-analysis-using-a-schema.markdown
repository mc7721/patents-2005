---

title: Method and apparatus for generating a characteristics model for a pattern-based system design analysis using a schema
abstract: A method for analyzing a target system that includes generating a characteristics model using a schema defining a domain, obtaining a plurality of characteristics from the target system using a characteristics extractor, wherein the plurality of characteristics is associated with the characteristics model storing each of the plurality of characteristics in a characteristics store, and analyzing the target system by issuing at least one query to the characteristics store to obtain an analysis result.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07653898&OS=07653898&RS=07653898
owner: Sun Microsystems, Inc.
number: 07653898
owner_city: Santa Clara
owner_country: US
publication_date: 20050520
---
The present application contains subject matter that may be related to the subject matter in the following U.S. applications filed on May 20 2005 and assigned to the assignee of the present application Method and Apparatus for Tracking Changes in a System Ser. No. 11 133 831 Method and Apparatus for Transparent Invocation of a Characteristics Extractor for Pattern Based System Design Analysis Ser. No. 11 134 154 Method and Apparatus for Generating Components for Pattern Based System Design Analysis Using a Characteristics Model Ser. No. 11 133 717 Method and Apparatus for Pattern Based System Design Analysis Ser. No. 11 134 062 Method and Apparatus for Cross Domain Querying in Pattern Based System Design Analysis Ser. No. 11 133 507 Method and Apparatus for Pattern Based System Design Analysis Using a Meta Model Ser. No. 11 134 021 and Pattern Query Language Ser. No. 11 133 660.

As software technology has evolved new programming languages and increased programming language functionality has been provided. The resulting software developed using this evolving software technology has become more complex. The ability to manage the quality of software applications including design quality and architecture quality is becoming increasingly more difficult as a direct result of the increasingly complex software. In an effort to manage the quality of software applications several software development tools and approaches are now available to aid software developers in managing software application quality. The following is a summary of some of the types of quality management tools currently available.

One common type of quality management tool is used to analyze the source code of the software application to identify errors or potential errors in the source code. This type of quality management tool typically includes functionality to parse the source code written in a specific programming language e.g. Java C etc. to determine whether the source code satisfies one or more coding rules i.e. rules that define how source code in the particular language should be written . Some quality management tools of the aforementioned type have been augmented to also identify various coding constructs that may result in security or reliability issues. While the aforementioned type of quality management tools corrects coding errors it does not provide the software developer with any functionality to verify the quality of the architecture of software application.

Other quality management tools of the aforementioned type have been augmented to verify that software patterns have been properly implemented. Specifically some quality management tools of the aforementioned type have been augmented to allow the software developer to indicate in the source code the type of software pattern the developer is using. Then the quality management tool verifies during compile time that the software pattern was used implemented correctly.

In another implementation of the aforementioned type of quality management tools the source code of the software is parsed and the components e.g. classes interfaces etc. extracted from the parsing are subsequently combined in a relational graph i.e. a graph linking all or sub sets of the components . In a subsequent step the software developer generates an architectural design and then compares the architectural design to the relational graph to determine whether the software application conforms to the architectural pattern. While the aforementioned type of quality management tool enables the software developer to view the relationships present in the software application it does not provide the software developer with any functionality to conduct independent analysis on the extracted components.

Another common type of quality management tool includes functionality to extract facts i.e. relationships between components classes interfaces etc. in the software and subsequently displays the extracted facts to the software developer. While the aforementioned type of quality management tool enables the software developer to view the relationships present in the software application it does not provide the developer with any functionality to independently query the facts or any functionality to extract information other than facts from the software application.

Another common type of quality management tool includes functionality to extract and display various statistics e.g. number of lines of code new artifacts added software packages present etc. of the software application to the software developer. While the aforementioned type of quality management tool enables the software developer to view the current state of the software application it does not provide the developer with any functionality to verify the quality of the architecture of the software application.

In general in one aspect the invention relates to a method for analyzing a target system comprising generating a characteristics model using a schema defining a domain obtaining a plurality of characteristics from the target system using a characteristics extractor wherein the plurality of characteristics is associated with the characteristics model storing each of the plurality of characteristics in a characteristics store and analyzing the target system by issuing at least one query to the characteristics store to obtain an analysis result.

In general in one aspect the invention relates to a system comprising a characteristics model defining at least one artifact and a plurality of characteristics associated with the at least one artifact wherein the characteristics model is generated using a schema defining a domain a target system comprising at least one of the plurality of characteristics defined in the characteristics model at least one characteristics extractor configured to obtain at least one of the plurality of characteristics from the target system a characteristics store configured to store the at least one of the plurality of characteristics obtained from the target system and a query engine configured to analyze the target system by issuing at least one query to the characteristics store and configured to obtain an analysis result in response to the at least one query.

In general in one aspect the invention relates to a computer readable medium comprising software instructions for analyzing a target system comprising software instructions to generate a characteristics model using a schema defining a domain obtain a plurality of characteristics from the target system using a characteristics extractor wherein the plurality of characteristics is associated with the characteristics model store each of the plurality of characteristics in a characteristics store and analyze the target system by issuing at least one query to the characteristics store to obtain an analysis result.

Other aspects of the invention will be apparent from the following description and the appended claims.

Exemplary embodiments of the invention will be described with reference to the accompanying drawings. Like items in the drawings are shown with the same reference numbers.

In the exemplary embodiment of the invention numerous specific details are set forth in order to provide a more thorough understanding of the invention. However it will be apparent to one of ordinary skill in the art that the invention may be practiced without these specific details. In other instances well known features have not been described in detail to avoid obscuring the invention.

In general embodiments of the invention relate to a method and apparatus for pattern based system design analysis. More specifically embodiments of the invention provide a method and apparatus for using one or more characteristics models one or more characteristics extractors and a query engine configured to query the characteristics of a target system to analyze the system design. Embodiments of the invention provide the software developer with a fully configurable architectural quality management tool that enables the software developer to extract information about the characteristics of the various artifacts in the target system and then issue queries to determine specific details about the various artifacts including but not limited to information such as number of artifacts of the specific type present in the target system relationships between the various artifacts in the target system the interaction of the various artifacts within the target system the patterns that are used within the target system etc. Further one or more embodiments of the invention provide a method and apparatus for automatically generating the characteristics model from a schema e.g. an XML schema defining a domain discussed below .

In one embodiment of the system the characteristics model describes artifacts i.e. discrete components in a particular domain. In one embodiment of the invention the domain corresponds to any grouping of related artifacts i.e. there is a relationship between the artifacts . Examples of domains include but are not limited to a Java 2 Enterprise Edition J2EE domain which includes artifacts such as servlets filters welcome file error page etc. a networking domain which includes artifacts such as web server domain name server network interface cards etc and a DTrace domain described below . In one embodiment of the invention each characteristics model includes one or more artifacts one or more relationships describing the interaction between the various artifacts and one or more characteristics that describe various features of the artifact. An example of a characteristics model is shown in . Those skilled in the art will appreciate that the system may include more than one characteristics model .

In one embodiment of the invention the use of a characteristics model enables a user to analyze the target system with respect to a specific domain. Further the use of multiple characteristics models allows the user to analyze the target system across multiple domains. In addition the use of multiple characteristics models allows the user to analyze the interaction between various domains on the target system .

In one embodiment of the invention the characteristics model is generated from a schema defining the domain. Embodiments detailing the generation of the characteristics model from a schema defining the domain are described in below.

In one embodiment of the invention the characteristics extractors e.g. characteristics extractor A A characteristics extractor N N are used to obtain information about various artifacts i.e. characteristics defined in the characteristics model . In one embodiment of the invention the characteristics extractors characteristics extractor A A characteristics extractor B N are generated manually using the characteristics model .

In one embodiment of the invention the characteristics extractor e.g. characteristics extractor A A characteristics extractor B N corresponds to an agent loaded on the target system that is configured to monitor and obtain information about the artifacts in the target system . Alternatively the characteristics extractor e.g. characteristics extractor A A characteristics extractor B N may correspond to an interface that allows a user to manually input information about one or more artifacts in the target system . In another embodiment of the invention the characteristics extractor e.g. characteristics extractor A A characteristics extractor B N may correspond to a process or system configured to obtain information about one or more artifacts in the target system by monitoring network traffic received by and sent from the target system . In another embodiment of the invention the characteristics extractor e.g. characteristics extractor A A characteristics extractor B N may correspond to a process or system configured to obtain information about one or more artifacts in the target system by sending requests e.g. pinging etc. for specific pieces of information about artifacts in the target system to the target system or alternatively sending requests to the target system and then extracting information about the artifacts from the responses received from target system . Those skilled in the art will appreciate that different types of characteristics extractors may be used to obtain information about artifacts in the target system .

Those skilled in the art will appreciate that each characteristics extractor or set of characteristics extractors is associated with a particular characteristics model . Thus each characteristics extractor typically only retrieves information about artifacts described in the characteristics model with which the characteristics extractor is associated. Furthermore if there are multiple characteristics models in the system then each characteristics model may be associated with one or more characteristics extractors.

The information about the various artifacts in the target system obtained by the aforementioned characteristics extractors e.g. characteristics extractor A A characteristics extractor N N is stored in the characteristics store via the characteristic store API . In one embodiment of the invention characteristics store API provides an interface between the various characteristics extractors characteristics extractor A A characteristics extractor N N and the characteristics store . Further the characteristics store API includes information about where in the characteristics store each characteristic obtained from the target system should be stored.

In one embodiment of the invention the characteristics store corresponds to any storage that includes functionality to store characteristics in a manner that allows the characteristics to be queried. In one embodiment of the invention the characteristics store may correspond to a persistent storage device e.g. hard disk etc . In one embodiment of the invention the characteristics store corresponds to a relational database that may be queried using a query language such as Structure Query Language SQL . Those skilled in the art will appreciate that any query language may be used. In one embodiment of the invention if the characteristics store is a relational database then the characteristics store includes a schema associated with the characteristics model that is used to store the characteristics associated with the particular characteristics model . Those skilled in the art will appreciate that if there are multiple characteristics models then each characteristics model may be associated with a separate schema.

In one embodiment of the invention if the characteristics store is a relational database that includes a schema associated with the characteristics model then the characteristics store API includes the necessary information to place characteristics obtained from target system in the appropriate location in the characteristics store using the schema.

In one embodiment of the invention the query engine is configured to issue queries to the characteristics store . In one embodiment of the invention the queries issued by the query engine enable a user e.g. a system developer etc. to analyze the target system . In particular in one embodiment of the invention the query engine is configured to enable the user to analyze the presence of specific patterns in the target system as well as the interaction between various patterns in the target system.

In one embodiment of the invention a pattern corresponds to a framework that defines how specific components in the target system should be configured e.g. what types of information each component should manage what interfaces should each component expose and how the specific components should communicate with each other e.g. what data should be communicated to other components etc. . Patterns are typically used to address a specific problem in a specific context i.e. the software system environment in which the problem arises . Said another way patterns may correspond to a software architectural solution that incorporates best practices to solve a specific problem in a specific context.

Continuing with the discussion of the query engine may also be configured to issue queries about interaction of specific patterns with components that do not belong to a specific pattern. Further the query engine may be configured to issue queries about the interaction of components that do not belong to any patterns.

In one embodiment of the invention the query engine may include pre specified queries and or enable to the user to specify custom queries. In one embodiment of the invention both the pre specified queries and the custom queries are used to identify the presence of one or more patterns and or the presence of components that do not belong to a pattern in the target system .

In one embodiment of the invention the pre specified queries and the custom queries are specified using a Pattern Query Language PQL . In one embodiment of the invention PQL enables the user to query the artifacts and characteristics of the artifacts stored in the characteristics store to determine the presence of a specific pattern specific components of a specific pattern and or other components that are not part of a pattern within the target system .

In one embodiment of the invention the query engine may include information or have access to information about the characteristics model that includes the artifact and or characteristics being queried. Said another way if the query engine is issuing a query about a specific artifact then the query engine includes information or has access to information about the characteristics model to which the artifact belongs. Those skilled in the art will appreciate that the query engine only requires information about the particular characteristics model to the extent the information is required to issue the query to the characteristics store .

Those skilled in the art will appreciate that the query engine may include functionality to translate PQL queries i.e. queries written in PQL into queries written in a query language understood by the characteristics store e.g. SQL . Thus a query written in PQL may be translated into an SQL query prior to being issued to the characteristics store . In this manner the user only needs to understand the artifacts and or characteristics that the user wishes to search for and how to express the particular search using PQL. The user does not need to be concerned with how the PQL query is handled by the characteristics store .

Further in one or more embodiments of the invention PQL queries may be embedded in a programming language such as Java Groovy or any other programming language capable of embedding PQL queries. Thus a user may embed one or more PQL queries into a program written in one of the aforementioned programming languages. Upon execution the program issues one or more PQL queries embedded within the program and subsequently receives and processes the results prior to displaying them to the user. Those skilled in the art will appreciate that the processing of the results is performed using functionality of the programming language in which the PQL queries are embedded.

In one embodiment of the invention the results of the individual PQL queries may be displayed using the visualization engine . In one embodiment of the invention the visualization engine is configured to output the results of the queries on a display device i.e. monitor printer projector etc. .

As discussed above each characteristics model defines one or more artifacts one or more relationships between the artifacts and one or more characteristics for each artifact. The following is an example of a Web Service Definition Language WSDL characteristics model. In the example the WSDL characteristics model includes the following attributes Definition ExternalImport Type Message Part Binding Operation PortType Fault Parameter Body and Service.

In the above WSDL Characteristics Model the Definition artifact is defined in lines 1 11 the ExternalImport artifact defined in lines 13 16 the Type artifact is defined in line 18 the Message artifact is defined in lines 20 24 the Binding artifact is defined in lines 26 33 the Operation artifact is defined in lines 35 45 the Fault artifact is defined in 47 51 the Parameter artifact is defined in lines 53 58 the Body artifact is defined in lines 60 66 the PortType artifact is defined in lines 68 72 the Service artifact is defined in lines 75 79 and the Part artifact is defined in lines 82 87.

A graphical representation of the aforementioned WSDL Characteristics Model is shown in . Specifically the graphical representation of the WSDL characteristics model shows each of the aforementioned artifacts characteristics associated with each of the aforementioned artifacts and the relationships including cardinality among the artifacts. In particular box corresponds to the Definition artifact box corresponds to the ExternalImport artifact box corresponds to the Type artifact box corresponds to the Message artifact box corresponds to the Part artifact box corresponds to the Binding artifact box corresponds to the Operation artifact box corresponds to the Fault artifact box corresponds to the Parameter artifact box corresponds to the Body artifact box corresponds to the PortType artifact and box corresponds to the Service artifact.

Those skilled in the art will appreciate that ST ST may be repeated for each characteristics model. In addition those skilled in the art will appreciate that once a characteristics store API is created the characteristics store API may only need to be modified to support additional schemas in the characteristics data store and additional characteristics extractors. Alternatively each characteristics model may be associated with a different characteristics store API.

As discussed above embodiments of the invention provide a method and apparatus for generating a characteristics model from a schema defining a domain. shows a flowchart describing a method for generating a characteristics model using a schema defining a domain in accordance with one embodiment of the invention. Initially the schema defining the domain is obtain ST . In one embodiment of the invention the schema is defined using a schema standard such as eXtensible Mark Language Schema Definition XSD .

SD is a standard created by the World Wide Web Consortium W3C that specifies how to formally describe the elements in an XML document. Thus one could define a domain such as a WSDL domain in an XML document using XSD. The following is an example of an XML document defining the WSDL domain using XSD.

In the above WSDL Schema the Definition artifact is defined in lines 107 128 the ExternalImport artifact defined in lines 121 128 the Type artifact is defined in lines 130 134 the Message artifact is defined in lines 136 146 the Binding artifact is defined in lines 227 238 the Operation artifact is defined in lines 170 207 the Parameter artifact is defined in lines 209 216 the Fault artifact is defined in lines 218 225 the PortType artifact is defined in lines 158 168 and the Service artifact is defined in lines 272 282.

Continuing with the discussion of the schema defining the domain may be parsed to obtain parsed information ST . In one embodiment of the invention the parsed information corresponds to complexTypes complexType attributes and nest complexTypes if the schema is an XML document written in accordance with XSD. Those skilled in the art will appreciate that other heuristics may be used to map the parsed information to artifacts and characteristics within the characteristics model. Continuing with the discussion of the parsed information is subsequently mapped to either an artifact or a characteristics ST . In this manner the characteristics model is generated. In some cases the parsed information may include sufficient information to define relationships between the various artifacts as well as the cardinality of the relationships. Those skilled in the art will appreciate that the characteristics model generated using the method described in may not be a complete characteristics model. For example the characteristics model generated using the method described in may not define all the relationships between the artifacts and the cardinality of each of the relationships. In such cases the relationships and cardinality of each of the relationships may be input manually by the user.

Continuing with the discussion of the Java Reflection API is subsequently used to introspect the Java to obtain information about the artifacts and characteristics within the domain ST . More specifically the Java Reflection API includes functionality to obtain information about the class of each object variables and constants used in the object etc. In some cases the Java Reflection API may also be used to obtain information about the relationships and cardinality of the relationships between the various artifacts. The ability the obtain information about the relationships and the cardinality of the relationships is typically dependent on the detail of the schema that defines the domain.

The information obtained from introspecting the Java objects created in ST is subsequently used to create the characteristics model corresponds to the domain defined by the schema ST . Those skilled in the art will appreciate that the information obtained from introspecting the Java object is equivalent to the information obtained from parsing the schema defined above in .

Those skilled in the art will appreciate that the characteristics model generated using the methods described in may be modified to include additional artifacts and characteristics prior to using the characteristics models to analyze the target system.

At this stage the system is ready to analyze a target system. shows a flowchart in accordance with one embodiment of the invention. Initially characteristics are obtained from the target system using one or more characteristics extractors ST . In one embodiment of the invention the characteristics extractors associated with a given characteristics model only obtain information about characteristics associated with the artifacts defined in the characteristics model.

Continuing with the discussion of the characteristics obtained from the target system using the characteristics extractors are stored in the characteristics store using the characteristics store API ST . Once the characteristics are stored in the characteristics store the target system may be analyzed using the characteristics model or models a query engine and the characteristics stored in the characteristics store ST . In one embodiment of the invention the user uses the query engine to issue queries to characteristics store. As discussed above the query engine may include information or have access to information about the characteristics models currently being used to analyze the target system. The results of the analysis are subsequently displayed using a visualization engine ST .

Those skilled in the art will appreciate that ST ST may be performed concurrently with ST ST. In addition steps in may be performed concurrently with the steps in .

An embodiment of the invention may be implemented on virtually any type of computer regardless of the platform being used. For example as shown in a networked computer system includes a processor associated memory a storage device and numerous other elements and functionalities typical of today s computers not shown . The networked computer may also include input means such as a keyboard and a mouse and output means such as a monitor . The networked computer system is connected to a local area network LAN or a wide area network via a network interface connection not shown . Those skilled in the art will appreciate that these input and output means may take other forms. Further those skilled in the art will appreciate that one or more elements of the aforementioned computer may be located at a remote location and connected to the other elements over a network. Further software instructions to perform embodiments of the invention may be stored on a computer readable medium such as a compact disc CD a diskette a tape a file or any other computer readable storage device.

While the invention has been described with respect to a limited number of embodiments those skilled in the art having benefit of this disclosure will appreciate that other embodiments can be devised which do not depart from the scope of the invention as disclosed herein. Accordingly the scope of the invention should be limited only by the attached claims.

