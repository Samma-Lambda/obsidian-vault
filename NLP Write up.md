## Data Extraction
Jane had provided the data in the form of a folder of PDFs. In order to work with this data, we need to be able to identify the text within these PDFs and store them in a useable format. 

The PDF formats are inconsistent. For example one page of the PDF might have the text nicely stored in the text layer of the pdf making it easy to extract from. But another page in the exact same PDF might have none of the text stored in the text layer, instead having a image to present the text to the reader. 
Examples of this for visualization are page 158 of the humana financial report where there is nothing in the text layer, but rendered as an image there is clearly an image containing the text "Humana A more human way to healthcare".
Examples of there being text in the text layer are super easy to come by. 
This is likely due to companies wanting to use custom fonts and logos

Thus to be able to extract the text properly we need to do a hybrid approach. We first attempt to extract the text from the text layer, and then if there is nothing present in the text layer we use OCR to extract the text. 

For the PDF text extraction we are using the PyMuPDF python package. For the OCR we use the pytesseract package, a python wrapper for utilizing the google Tesseract OCR engine. 

## Preparing the Data
Due to the complicated nature of language, it is common practice to stem the words in text before analyzing them. This causes words that only differ by inflection to be represented by the same lexeme. An example of this is the lexeme RUN which encompasses the words run, runs, running and ran. To achieve this effect we used the snowball stemmer algorithm. 

Additionally in the process of collecting the text, there are a large number of non-alphabetical characters that end up in the text, which are removed. 


## Building the Dictionary
Now that the data is in a useful format we can do statistical analysis on it

I can't find the paper that explains the original derivation of the statistic that we are using(which is important because I am pretty sure that our statistic is a heuristic and not a formal statistic), It would be nice to be able to . 

For each n-gram we calculate S where $S=\frac{\sqrt{N}(A\cdot D-C\cdot B)}{\sqrt{(A+B)(C+D)}}$. Values of $S>0$ correspond to the n-gram being more prevalent in the target corpus while $S<0$ correspond to the n-gram being more prevalent in the contrast document. 

For our target corpus we used the text extracted from the PDFs. For our contrast corpus we used the brown corpus, with the subcategories of 'news', 'editorial', 'reviews' due to their conceptual similarity allowing us to better find significant n-grams.

We created a list of the the top 500 highest ranked and 500 lowest ranked unigrams and bigrams. We chose not to do any higher than the 2-grams due to the inherent variety of the higher length grams, and due to their    


## Using the Dictionary
While the dictionary we have created has a large amount of use cases, we wanted to show two specific use cases.
### Man Whitney U Test
The Man Whitney U test is a form of hypothesis test which determines wether one population tends to produce higher results of a specific variable. The null hypothesis of the Man Whitney U test is the for a sample $x$ in population one, and sample $y$ in population two that $P(x>y)=0.5$ while the alternative hypothesis is $P(x>y)\neq 0.5$ 

In our specific use case, we want to determine wether the top ranked esg statements are using our highly ranked unigrams more than the bottom ranked esg statements. We conducted a one sided Man Whitney U test and rejected the null hypothesis at significance value($\alpha = 0.05$) with a $p$-value of $0.0018$ 

But this approach did not account for the differing document sizes between the populations. We then ran the same test but instead normalized by document size, which resulted in us failing to reject the null hypothesis. 

So to clarify this I went an did a hypothesis test on the length of the documents which came back inconculusive 




Often when working with text classification overfitting of machine learning models can be a problem. To combat this we have trained a Support Vector Machine with only vectors seeing the significant unigrams and bigrams. We then studied the effectiveness of this support vector machine at classifying the sentances as originating from text talking about sustainability or the contrast text. 