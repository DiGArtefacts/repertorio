# Repertorio

Code for converting the _Repertorio Terminologico per la Schedatura delle Sculture dell’Arte Gandharica_ into a SKOS vocabulary.

Read more in [this blog post](https://digartefacts.hypotheses.org/14).

Example pages © 2007 IsIAO

## Updating SKOSMOS

Currently, VocBench and SKOSMOS us a slightly different SKOS format. So in order to publish the changes made in VocBench, we need these steps:

1. Download the data in turtle format from VocBench.
2. Convert them to SKOSMOS format using `Prepare_SKOSMOS.ipynb`.
3. Go to the Fuseki admin interface of SKOSMOS.
4. Delete the existing data (as importing the new file would only add new triples, but not delete obsolete ones). This can be done with this SPARQL query:

    ```sparql
    WITH <https://w3id.org/diga/terms/>
    DELETE { ?subject ?predicate ?object . }
    WHERE {
      ?subject ?predicate ?object .
    }
    ```
5. Upload the processed turtle file into Fuseki.
