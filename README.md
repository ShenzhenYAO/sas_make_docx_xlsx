# Creating/modifing WORD docx files by SAS

Specifically, the egp file in the folder "sas_code/" is expected to do the following:
1. import data from word/document.xml from the template docx file (indeed a docx file is a zip file), and save into a data set, e.g., import data from textcontent of the tag <w:t>, and save into a SAS dataset called 'title', in the column 'title_text'.
2. make changes of the data (e.g., change 'title_text' from the original 'Project Title' to 'Project one, the greatest research project').
3. output data to an xml file.
4. copy the template docx file to the output folder, as the output docx.
5. save the output data from step 3 to the output docx, replacing the original word/document.xml.

In the .egp file, there are two embedded programs. The first contains basics to read data from an xml file. The second contains a complete process from importing data from the word/document.xml in the template docx file, to exporting data to the output xml and add into the output docx, replacing the original word/document..

Although it is doable, the SAS way of creating/modifying a word docx is quite clumsy. 

First, the input data has to be put into tables. For example, to add a paragraph as a research step like:
>Step 1:
>Create a cohort from the following source:
>- PHRS
>- DP_claims

A data table must be created with multiple records, each for a line of the above text. This is against the normal practice of SAS coding, as users prefer to write these steps in comments of SAS code, and let a program to 
read and convert to steps in a word docx automatically.

Second, it remains unknown how to output to the same xml from multiple tables. 
- Should user create multiple xmlmap files? 
- If so, when exporting data to the same xml file, would it be overwritten each time using a different ?
- ...

Third, the SAS method of adding an xml file into a docx has problems. It just cannot make it right (perhaps adding unidentifiable strange characters when reading data into a zip). 

In summary, this project shows that editing a docx file by SAS is possible but not recommended. 
A better way is to use the js tool in the project __sas_egp_v8tov7__. That project is initially for converting epg files from v8 to v7. However, it as well provides tools to read comments (for description of research steps) from a SAS code file, and save as research steps into a docx file.