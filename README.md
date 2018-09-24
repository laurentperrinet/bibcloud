bibcloud
========

a tool to gather and share bibliographic collections


https://tex.stackexchange.com/questions/166675/how-could-i-manage-a-bibliography-in-a-world-full-of-clouds-citeulike-mendele

I always used a single ``babel.bib`` BibTex file to keep a record of all my readings. Great. Then I managed it using a VCS (first SVN, then git). Super great. But at the same time, resources like [CiteUlike][1] or Mendeley (but also other services like orcid) allow for cloud-like services of having this data everywhere, anytime. Super super great!

But this fails if you have no connection to internet (remote conference, ...) or more importantly if these services change their policy (mendeley to citeulike sync disappeared at a sudden). The work you provide is not yours. These are mostly commercial services while all the open-source tools are there. Most importantly, the multiplicity of tools makes it difficult to share bibliographic data easily, while if we would have a tool to translate between them this would make it possible (without changing your habits).

As a consequence, I wish to build such a "BibCloud" service with the following features:

* ``bibcloud init`` : use with biblatex (but a format using [bibjson][2] is possible)
* CLI coded in python (widespread in the scientific community), all databases + configuration files being stored in plain text files.
* ``bibcloud commit -am' adding Sawyer14nature'; bibcloud push `` : CVS integration (git / hg / ...) - and storage in remote repositories (github, bitbucket)
* ``bibcloud pull citeulike``, ``bibcloud push citeulike`` : easy conversion + pull and push to existing accounts (Citeulike, Mendeley) - including synchronization of PDFs
* ``bibcloud detect_dups records`` implementation of tools to detect and merge duplicate records, and duplicate fields (like ``bibcloud detect_dups authors``:  an author with different versions, like eg ``Tom Sawyer``, ``T Sawyer``, ``T J Sawyer`` or for journal names with ``bibcloud detect_dups journals``)
* ``bibcloud pull 2323422.pdf`` scan a pdf to extract its metadata (like the DOI) - allow to include the citation in the paper ``bibcloud push 2323422.pdf`` to simply send a file to colleagues.
* ``bibcloud citekey Sawyer14`` : generate a citekey according to a given rule
* ``bibcloud edit Sawyer14`` : edits one particular entry
* ``bibcloud file Sawyer14`` : files the PDF corresponding to the entry according to some rule
* ``bibcloud push html`` easy conversion to some web format (github pages?) to read papers online.

Before attempting to put that together, I wish to know of the existing pieces the community may know.

Notes:

* it is different from this [question "Workflow for managing references?"][3] as existing solutions like zotero or  do not work for me. I wish to get the pieces of the puzzle together to build a command-line tool for managing bibliographies.
* it is different to this [question][4] or to [this other][5] as they ask more for a GUI solution.


  [1]: http://www.citeulike.org/
  [2]: http://www.bibjson.org/
  [3]: https://tex.stackexchange.com/questions/18848/workflow-for-managing-references
  [4]: https://tex.stackexchange.com/questions/33619/latex-and-bibliography-management-tools
  [5]: https://tex.stackexchange.com/questions/162703/mac-bibliography-management-with-biblatex-support-export

ideas
-----

 * use http://opds-spec.org/specs/ to store th PDF files
 * anything similar in https://github.com/epfl-dcsl/bibcloud or https://github.com/braingineer/bibcloud ?
