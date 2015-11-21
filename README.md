# inverted\_index
A Hadoop map-reduce program to generate an inverted index for querying

## Structure

**out/** - Contains output from both WordCount and InvertedIndex map-reduce
functions. The post-processing hadoopOutputToJSON.py script converts the
InvertedIndex output to JSON, which the queryII.py script can read and query
from. The plot.py script allows you to generate a histogram of word count to 
visually inspect the words. This is how we chose our stop word threshold.

**run**\* - Bash script to run the entire suite, starting with pre-processing,
then the Hadoop jobs, and ending with post-processing. There are many variables 
for environment-specific parameters that *must be changed* in order to run 
this.

**script/** - Contains the pre-processing script line\_number.py, which adds a
document ID and line number to all lines in all .txt files in txt/. It outputs
docs\_id.json, which contains the document ID -> filename mapping for
queryII.py.

**src/** - Contains the two Hadoop Java classes, WordCount and InvertedIndex.
WordCount is a slightly modified version of the word count example provided in
Hadoop. InvertedIndex.jar contains both classes and is used by Hadoop for
processing the text.

**txt/** - Contains the source text files from Gutenberg. All .txt files have
their Gutenberg header removed, but are otherwise unaltered. The corresponding
.num files contain document ID and line numbers as added by line\_number.py.


