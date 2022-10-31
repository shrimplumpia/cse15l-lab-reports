# Researching Commands

## ***The less command***
<br/>

## Example 1: Basic Usage
<br/>
In the command line, type:

~~~
less [options] [filename]
~~~

<br/><br/>
Using the files provided from our lab in week 4 (docsearch), I used this command:

~~~
less technical/biomed/bcr458.txt
~~~

And received this output:
~~~
Introduction
Marin County, located north of San Francisco,
California, is distinguished among urban counties in the United States by its relatively small population (250,000 residents), by a median per-capita income of more than 200% that of the nation [ 1 ] , and by elevated rates of breast cancer that were first reported in the early 1990s [ 2 ] . The media has since pronounced Marin County 'the breast cancer capital of the world' [ 3 ] , and heightened community concern has inspired grassroots and scientific efforts to investigate reasons for the high incidence.
Initial studies have suggested that elevated rates in white women living in Marin County and the San Francisco Bay Area (SFBA) are generally explained by the higher prevalence of established breast cancer risk factors, including higher levels of education and income, later age at first birth, and nulliparity [ 4 5 ] . Our previous assessment of breast cancer incidence trends in Marin County isolated the rate elevation to women aged 45-64 years at diagnosis [ 6 ] . Community and scientific concern over increasing incidence rates has nevertheless remained high, so detailed surveillance o incidence and mortality rates has continued.
It has been estimated that only 45-55% of breast cancer cases in the United States are explained by established risk factors such as income, reproductive factors, and family history [ 7 ] . Distinctive breast cancer incidence and mortality patterns in well-defined populations may therefore inform etiologic understanding. For this reason, and as part of ongoing regional cancer surveillance efforts, we analyzed the most recent breast cancer incidence and mortality data available for Marin County and compared these rates and trends with those from other areas in California.
      
      
Materials and methods
        
Cancer incidence and mortality data 
We obtained cancer incidence and mortality data for Marin County and other California counties from the California Cancer Registry and the California Office of Vital Statistics, respectively. Analyses were based on new cases of invasive breast cancer ( International Classification of Diseases - Oncology , 2nd edition, site codes 50.0-50.9 excluding histology codes 9590-9989; invasive
:
~~~

>This is only a portion of the output. Essentially, when the less command is used like this, it prints out the contents of a file one page at a time. In this case, the output was extremely long, and the ":" at the end signifies that the output goes on for longer to fit on one single page. You can continue to scroll down the page by using the scroll bar or down arrows, and go to the next page using the f key or space bar.

<br/>
This command is particularly helpful when trying to read through large files. When these files are read and printed to the command line, they are printed out in 'pages' that we can navigate between using different keyboard shortcuts, making the process of reading large files much more manageable.

<br/><br/>
<br/><br/>

---
## Example 2: Line Count
<br/>
In the command line, type:

~~~
less -N [filename]
~~~

<br/><br/>
Using the files provided from our lab in week 4 (docsearch), I used this command:

~~~
less -N technical/biomed/bcr458.txt
~~~

And received this output:
![](less-n.png)
*I put it in as an image instead of a code block since copy-pasting the output messed up the formatting.*

>Using -N with the 'less' command prints out a very similar output as just using 'less' by itself, except this time it includes the line number of each line in the file. 

<br/>
An example in which this would be useful is when we use the command line to read through a file, and need to record which paragraphs are most useful to us. If we needed paragraph 2 from the above output, for example, we could note that we need lines 6-27.

<br/><br/>
<br/><br/>

---
## Example 3: Multiple Files
<br/>
In the command line, type:

~~~
less [filename1] [filename2] [filename3]
~~~
Essentially, you can look through the contents of multiple files by passing them in as multiple command line arguments.

<br/> 
This would be useful when we need info from multiple files at once, and so we don't need to keep running the less command for each individual file.

<br/><br/>
Using the files provided from our lab in week 4 (docsearch), I used this command:

~~~
less technical/biomed/bcr458.txt technical/biomed/bcr607.txt
~~~

And received this output:
![](less-multiple-files.png)
> This image only displays the last page of the first file passed into the less command, just to show that the last line doesn't just say (END). Instead, it shows that we can look at the next file passed into the command line, and we can access this file by pressing "n".

<br/><br/>
<br/><br/>

## ***The find command***
<br/>

---
## Example 1: Finding Every File in the Current Directory

<br/><br/>
Using the files provided from our lab in week 4 (docsearch), I used this command:

~~~
find .
~~~

And received this output:
![](find-dot.png)
*This is a screenshot of only a portion of the output, since there are so many ./technical files within Docsearch.*
> The "." in the command tells 'find' to search and print every file in the current directory. When I ran this command using the code from our week 4 lab, I was in the docsearch directory, so the output printed out every file within that directory (so files within the technical folder, which contains the 911 reports, biomed, government, and plos folders).

This command can be useful when we need to know exactly what files are contained within a certain directory.

<br/><br/>
<br/><br/>

---
## Example 2: Exact file names in the directory
<br/>
In the command line, type:

~~~
less . -name [String to look for]
~~~

The -name command tells 'find' to search for files or directories that contain the String following -name and print them. The "." before the -name command tells 'find' to search for files that are named exactly like the String following -name. This command is case-sensitive, meaning that lowercase and uppercase laters from the String have to exactly match the file or directory we are searching for. 

<br/>
This can be useful in a case where there is a very specific file we are looking for. We wouldn't need to look through every single file name within a directory, saving a lot of time.

<br/><br/>
Using the files provided from our lab in week 4 (docsearch), I used this command:

~~~
find . -name 'government'
~~~

And received this output:
~~~
./technical/government
~~~

>There is only one match for finding a file or directory named exactly 'government'. In this case, it's the government directory within the technical directory under docsearch.

<br/><br/>
<br/><br/>

---
## Example 3: Finding recently modified files
<br/>
Using the files provided from our lab in week 4 (docsearch), I used this command:

~~~
find . -amin -5
~~~

And received this output:
![](find-amin.png)
>This command searches for files in the current directory that were modified less than five minutes ago. For the sake of this example, I modified a line in one of the files in the docsearch repository and used -amin -5 immediately after to see what it would output. I believe that the "./.git/objects" lines may be referring to the exact edits I made in the file, while the "./technical" line refers to the exact file that I modified.

<br/>
A situation in which I think this would be useful is when we might accidentally modify a file we didn't mean to. If we have an extremely expansive directory like technical, the -amin -5 command would allow us to instantly find the file we mistakenly modified.

<br/><br/>
<br/><br/>

---
## ***The grep command***
<br/>

## Example 1: Basic usage
<br/>
In the command line, type:

~~~
grep [pattern] [filename]
~~~
grep looks for a pattern (e.g. a String expression) in the filename specified in the command line and prints out all the lines in that file that match that pattern.

<br/>
This is useful when we want to find very specific information within lines, and so we can use the pattern as a keyword to instantly find the information we are looking for.


<br/><br/>
Using the files provided from our lab in week 4 (docsearch), I used this command:

~~~
grep "small" technical/biomed/1468-6708-3-1.txt
~~~

And received this output:

~~~
in certain small subsets. A review of 13 studies of older throughout adult life. It may be that a small amount of number of studies of older persons is fairly small, and to normal yielded small, non-significant effect sizes, with due to a smaller sample size.
~~~
>The lines in this output don't really make sense when put together, but that's because these are all the lines that match the pattern I searched ("small").

<br/><br/>
<br/><br/>

---
## Example 2: Color-coding the pattern we are looking for
<br/>
In the command line, type:

~~~
grep --color [pattern] [filename]
~~~
This command works similarly to using grep normally, but this time we included the 'option' of color coding the pattern we are looking for using --color. This means that when our lines within the specified file include the pattern we're searching for, those lines are printed with the pattern we are looking for highlighted in the color red.

<br/>
If we are using the pattern as a keyword within a file, it can be helpful to color-code that keyword when many lines match the pattern we are looking for to distinguish the exact information that we need.

<br/><br/>
Using the files provided from our lab in week 4 (docsearch), I used this command:

~~~
grep --color "small" technical/biomed/1468-6708-3-1.txt
~~~

And received this output:
![](grep-color.png)
>The pattern I was searching for was "small", so this time all lines within the file 1468-6708-3-1.txt within the biomed directory in technical were printed with "small" being highlighted in red.

<br/><br/>
<br/><br/>

---
## Example 3: Line numbers of successful matches
<br/>
In the command line, type:

~~~
grep -n [pattern] [filename]
~~~
This command works similarly to using grep normally, but this time we included the 'option' of printing out the line numbers of each line we looked for. When our lines within the specified file include the pattern we are looking for, they printed along side the corresponding line numbers they have in their file.

<br/>
If we are looking for information using patterns as a keyword within a file, knowing the line numbers of that information can be useful if we need additional context. If we are able to locate those lines within the file (using a command like [less -N [filename]] listed in a previous example), we may be able to get additional context by looking at the lines directly next to the ones we searched for.

<br/><br/>
Using the files provided from our lab in week 4 (docsearch), I used this command:

~~~
grep --color -n  "small" technical/biomed/1468-6708-3-1.txt
~~~

And received this output:
![](grep-n-color.png)
>I actually combined two different 'options' here, --color and -n. In this picture, the line number of each matching line within their file is printed alongside those lines. Since I used --color as well, the pattern I searched for in these lines, "small", is highlighted in red as well.