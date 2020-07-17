
## The Summarizer

   There are huge chuck of documents with a bundle of data. These documents can be shortened to a set of data or we could say creating a subset of the documents or summarize them to get the important and relavent data from the documents.Summarization can be done for text,images and videos.Text summarization can be done in two process extraction-based summarizations and abstraction-based summarizations.Here in this project I have followed the extraction-based summarizations.Which means extracting key sentences to do the summarizations for the documents.
   In this project,we can extract the summaries by selecting random documents by giving the percentage of how many documents of the total documents are to be considered.
# Author
 Saisri M Potluru.You can contact me at saisri.m.potluru-1@ou.edu .
# Description 
  The files used in this project are in json file which are with a nested dictionary format.
  The format of the data files is :
  
   ## JSON schema of full text documents

~~~
{
    "paper_id": <str>,                      # 40-character sha1 of the PDF
    "metadata": {
        "title": <str>,
        "authors": [                        # list of author dicts, in order
            {
                "first": <str>,
                "middle": <list of str>,
                "last": <str>,
                "suffix": <str>,
                "affiliation": <dict>,
                "email": <str>
            },
            ...
        ],
        "abstract": [                       # list of paragraphs in the abstract
            {
                "text": <str>,
                "cite_spans": [             # list of character indices of inline citations
                                            # e.g. citation "[7]" occurs at positions 151-154 in "text"
                                            #      linked to bibliography entry BIBREF3
                    {
                        "start": 151,
                        "end": 154,
                        "text": "[7]",
                        "ref_id": "BIBREF3"
                    },
                    ...
                ],
                "ref_spans": <list of dicts similar to cite_spans>,     # e.g. inline reference to "Table 1"
                "section": "Abstract"
            },
            ...
        ],
        "body_text": [                      # list of paragraphs in full body
                                            # paragraph dicts look the same as above
            {
                "text": <str>,
                "cite_spans": [],
                "ref_spans": [],
                "eq_spans": [],
                "section": "Introduction"
            },
            ...
            {
                ...,
                "section": "Conclusion"
            }
        ],
        "bib_entries": {
            "BIBREF0": {
                "ref_id": <str>,
                "title": <str>,
                "authors": <list of dict>       # same structure as earlier,
                                                # but without `affiliation` or `email`
                "year": <int>,
                "venue": <str>,
                "volume": <str>,
                "issn": <str>,
                "pages": <str>,
                "other_ids": {
                    "DOI": [
                        <str>
                    ]
                }
            },
            "BIBREF1": {},
            ...
            "BIBREF25": {}
        },
        "ref_entries":
            "FIGREF0": {
                "text": <str>,                  # figure caption text
                "type": "figure"
            },
            ...
            "TABREF13": {
                "text": <str>,                  # table caption text
                "type": "table"
            }
        },
        "back_matter": <list of dict>           # same structure as body_text
    }
}
~~~                          
# Description of the functions: 
 
## readfiles()
   This function will retrive the list of file names according to the given percentage.
  
## read_content()
   This function will read all the content text of the body_text of the list of files and tokenize by removing the stop words and punctuations in them and append all the text data of the documents in a form of list.
  
## vectorizer()
   This function will vectorize the data with the TfidfVectorizer and produce a dataframe with respective words for each of the files.
   
## kmeansclustering()
   kmeans is a unsupervised learning algorithm by which we will be able to form a clusters based on the documents.By this function we could know which document is assigned to which cluster.
   
## dataframe_con()
  I have used this function to extract all the documents accroding to the clusters which they belong to and return a list of string with the appended data of the documents for all the clusters.

## summarizations()
  This function will use the gensim package to summarize the data based on the number of clusters considered.
  
## output_file()
   This function is used to write all the summarizations obtained from the clusters and store it in a single "SUMMARY.md" file with a header.
   
# Assumptions  
 -I have used pandas dataframe to have the ease to combine the data.
 
# External Resources:
  https://towardsdatascience.com/k-means-clustering-8e1e64c1561c
  http://queirozf.com/entries/pandas-dataframe-groupby-examples
  https://www.geeksforgeeks.org/python-pandas-dataframe/
  Text Analytics with python - textbook 




   
  
  
   
   
   
   
   
