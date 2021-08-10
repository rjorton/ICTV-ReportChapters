# ICTV-ReportChapters

This GitHub repo stores instructions for how to load an ICTV Report Chapter from the submitted MS-Word document into the ICTV website's Telligent content management system. Also in the repo are a couple of files (EndNote style, chapter template) and a couple of scripts to help.

The vast majority of the style/rules were not like this initially and have been built up over the years. The below is a summary of the existing style/rules - these are not my style/rules (I don't like many of them), they are the Report style/rules which are implemented; most of them (heading names, ordering etc) are specified within the Word chapter template itself (uploaded here to GitHub as well for clarity).

You need to be logged into the [ICTV Report website](https://www.ictv.global/report/) to be able to edit pages, if logged in you should see the **Edit ‘pencil’ icon** in the top left corner of the screen.

## Create the chapter Wiki ##

To create a new chapter, you need to create a new Wiki. This should be done within the correct parent Wiki e.g. [dsDNA viruses](https://talk.ictvonline.org/ictv-reports/ictv_online_report/dsdna-viruses/), from there:
 
```
Edit -> Manage Group -> Applications -> Add Application -> Add Wiki
```

**Enter the virus family name** (or floating genus name) into the **Name field** and click **Save**.

After refreshing the parent page (e.g. [dsDNA viruses](https://talk.ictvonline.org/ictv-reports/ictv_online_report/dsdna-viruses/)) you should see the new Wiki you have created in the list, click on it to begin building the chapter.


After initially creating the chapter Wiki, I typically make it private until it is complete by:

```
Edit -> Manage Wiki -> Permissions -> Site Roles -> Everyone
```

And **uncheck** the **Read Wiki** checkbox

**NB:** you will need to remember to re-check this box when the chapter is ready for public viewing.

### Short URL ###

At this stage you can email Elliot to create the short chapter URL. He can create the link if the main Wiki page exists even if it has no content e.g.:

*Flaviviridae*  
[https://www.ictv.global/report/flaviviridae](https://www.ictv.global/report/flaviviridae)  
[https://talk.ictvonline.org/ictv-reports/ictv\_online\_report/positive-sense-rna-viruses/w/flaviviridae](https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/flaviviridae)

There are many different ways to build the chapter, below is just one example of the route that can be taken – this route is being used in this tutorial so I can cover most things without being too confusing rather than the de facto route.

## Create the pages of the chapter ##

I often simply open an existing chapter in a side-by-side window to check/copy many of the styles and layouts, such as the first chapter - [*Flaviviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/flaviviridae).

To create a new page within the Wiki: 

```
Edit -> Manage Wiki -> Pages -> Add Page
```

**Enter the name of the parent page** in the **Parent** field (as you type text, it will display matching pages, so you can select the parent from the dropdown list) – the parent will typically be the top level family Wiki page (unless you have subfamilies in which case you will want to place a genus within the correct subfamily).

**Enter the name of the page itself** in the **Title** field. Family chapters have the following pages in the following order:

- Genus: Flavivirus
- Genus: Myvirus
- Genus: Othervirus
- Unassigned species
- Authors: Flaviviridae
- Resources: Flaviviridae
- References: Flaviviridae
- Citation: Flaviviridae

You will need to check whether there are any floating species (not in a genus) within the family (and/or subfamilies), this is typically not indicated in the word doc (or the section is left in where there are in fact none). If there are none then there is no need for the Unassigned species page - see later section on this for more details.

**NB**: Subfamily pages should be created (the only exception so far has been the [*Roniviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/roniviridae)) whilst subgenera do not currently need their own page - see genera section later.

**NB**: 'Further reading' pages still exist on some older chapters but are no longer created for new chapters.

**NB**: It is not possible to italicise text entered in these name fields, the italics of page headings and within the Table of Contents is handled behind the scenes by Telligent (Elliot's team modified the template to display them in italics).

Enter **TBA** (To Be Added) into the **Body** field as the page cannot be created with empty text (as you progress you may want to add the page text here directly upon the first creation).

You may want to **uncheck** the **'Notify me when this page is edited'** checkbox.

**Click** the **Post** button

### Reordering pages ###

To reorder pages within the Wiki's Table of Contents (TOC: the navigation menu on the side), which by default is sorted alphabetically:

```
Edit -> Manage Wiki -> Table of Contents
```

You can then reorder the pages within the TOC by dragging and moving them, this includes creating/changing parent/child relationships.

**NB:** you should click the **Save** button to save your changes

**NB:** if you select a page, a 'Hide in table of contents' option becomes visible which can be used to hide pages.

**NB:** taxon pages (subfamilies and genera) should be sorted by rank then alphabetically i.e. subfamilies should come before any genera not in subfamilies, with taxa of the same rank sorted alphabetically. Unassigned species are typically placed underneath the named taxa.

The References, Authors, and Citation pages typically don't contain references so can be created next as they won't need hyperlinked references (again pages need not be created in this order, this is just an overall example of how to do).

## References page ##

By default the references in the word document should be in the standard ICTV  Report format (sorted by author, author names in bold, ending in [PMID Number]). For example, see: [References: *Flaviviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/flaviviridae/365/references-flaviviridae)

These refs should be copy and pasted into the References page Body text field, this typically results in empty lines inserted between references which need to be deleted.

To create links from [PMID Number] to PubMed, I use the source code function of the page:

```
Tools -> Source Code
```

Copy and paste the source code of the page into a basic text editor such as TextEdit or Notepad, and do a couple of global find/replace functions:

Replace (**NB:** there is a **space** after PMID below):

```
[PMID 
```

with:


```
[<a href="https://www.ncbi.nlm.nih.gov/pubmed/
```

then replace:

```
]
```

with:


```
" target="ictvref">PubMed</a>]
```

Finally, replace the following text (as non-PubMed articles still come out with [PMID) with nothing:


```
[PMID
```

I will re-write an old script I had to do this in python, but it frequently broke due to numerous issues such as the ] or " characters being in the title of articles, and changes in the endnote style affecting non-PubMed reference formats - so I preferred to do this manually in the end where I could see and fix the issues easily in TextEdit (typically takes a minute or two). 

Overall, the goal is to go from:

[PMID 24335300]

to a hyperlinked version (launching a new tab/window]:

[[PMID 24335300](https://pubmed.ncbi.nlm.nih.gov/24335300/)]

When finished simply replace (by copy and pasting) the edited source code back into the Source code window of the report page being edited.

**RJO ToDo:** create python version of script for running on windows (as well as mac/linux)

## Authors page ##

Copy and paste the author details for the chapter into the Authors page.

- Author names should be highlighted in bold
- The corresponding author should be marked with an asterisk (star) *
- The following should be added at the end of the author list: * to whom correspondence should be addressed
  - Not (as frequently comes in): * corresponding author
- The chair of the study group should have the following text directly underneath their name:
  - *Theviridae* Study Group Chair
  - Not (as frequently comes in): Chair, *Theviridae* Study Group
- Telephone numbers should not be used anymore, delete if there
- 'E-mail' is used rather than 'Email' 'email' 'e-mail' or 'mail' etc
- Hyperlinks/Mail-to-links are removed from email addresses
- If there are old authors (of previous versions) - insert a 'Authors of a previous version of this Report' subheading and list the appropriate authors e.g. see [Authors: *Flaviviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/flaviviridae/364/authors-flaviviridae)
- The authors of the 9th ICTV Report chapter (if there was one) should be acknowledged at the bottom of the page in the form:
  - The chapter in the Ninth ICTV Report, which served as the template for this chapter, was contributed by Smith, P., Jones, P. and Davis, J.

When initially pasting the content, it will annoyingly treat each line as a separate paragraph. There are numerous ways to fix these, one is to select all an author's details and use a Div block:

```
Format ->  Formats -> Blocks -> Div
```

An alternative is to modify the source code via (Tools -> Source code) and use  \<br\> breaks

## Citation page ##

A citation to the Journal of General Virology (JGV) profile should be added to the citation page in the form:

A summary of this ICTV Report chapter has been published as an ICTV Virus Taxonomy Profile article in the Journal of General Virology, and should be cited when referencing this online chapter as follows:

Simmonds, P., Becher, B., Bukh, J., Gould, E.A., Meyers, G., Monath, T., Muerhoff, S., Pletnev, A., Rico-Hesse, R., Smith, D.B., Stapleton, J.T., and ICTV Report Consortium. 2017, [ICTV Virus Taxonomy Profile: *Flaviviridae*](https://www.microbiologyresearch.org/content/journal/jgv/10.1099/jgv.0.000672), Journal of General Virology, 98:2–3.

**NB:** when creating the chapter the citation will not exist so should be created as 'In Press' with a year estimation, e.g.:

Simmonds, P., Becher, B., Bukh, J., Gould, E.A., Meyers, G., Monath, T., Muerhoff, S., Pletnev, A., Rico-Hesse, R., Smith, D.B., Stapleton, J.T., and ICTV Report Consortium. 2021, ICTV Virus Taxonomy Profile: *Flaviviridae*, Journal of General Virology, (In Press).

**NB:** this page will need to be edited at a later date when the profile is published, including a hyperlink to the publication on the JGV website

**NB:** when creating the hyperlink to the profile, this should launch a new/tab window as it is moving off the report website. To create a hyperlink, select the text to be hyperlinked:


```
Insert -> Link
```

Enter the URL and select **New window** from the **Target** dropdown.

## Edits within MS-Word ##

Firstly, the EndNote library should now be switched to the **ICTV_HyperlinksHover** style (in the OneDrive Admin folder, and also uploaded here) within the word document. This changes the references so that they have the information needed to create the hoverable hyperlinks (e.g. article and journal title). 

**NB:** you can of course not bother we hoverable/hyperlinked references, in which case leave EndNote on the existing style. All the steps listed below still need to be done. The only thing that can be skipped is the last step where the source code of the page is copied and run through a script to convert the references - see later section on References.

Secondly, a few checks/changes need to be done within the word document:

1. Accept all track changes, and stop tracking changes, remove comments (after addressing anything) (in the past comments etc have resulted in anomalies when pasting into the online textboxes such as spaces disappearing).
2. Convert figure usage from Figure 1, Figure 2, Figure 3, Figure 4 etc to the ICTV Report style. Figures on the main family page are labelled **Figure 1.***Myviridae*****, **Figure 2.***Myviridae*****, **Figure 3.***Myviridae*****, etc. Whilst figures on genera pages are labelled **Figure 1.***Myvirus*****, **Figure 2.***Myvirus*****, **Figure 1.***Othervirus*****, **Figure 2.***Othervirus*****, etc. Where *Myviridae*, *Myvirus*, and *Othervirus* are the corresponding taxa names. **NB:** There is no space after the number, they are not separate sentences. **NB:** The Figure number/name is highlighted in bold, whilst the rest of the legend is not (e.g. see [*Flaviviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/flaviviridae)) figures.
3. Ensure figure legends are in the correct place within the text (previously they were in their own section), and no 'Insert Figure X near here' texts remain 
4. As above in (2), but for tables as well e.g. **Table 1.***Myviridae*****, **Table 2.***Myviridae*****, **Table 1.***Myvirus*****, **Table 1.***Othervirus*****. This does not include the 'Member species' and 'Related, unclassified viruses' tables which are typically not numbered/labelled.
5. Ensure Table 1 (the summary table) is referenced somewhere in the text, typically at the end of the 1st sentence.
6. Ensure Table 1 (the summary table) has the column headings **Characteristic** and **Description** in bold
7. Ensure Table 1 (the summary table) does not have a colon after 'Typical member' or 'Example' as it is now called (1st data row) and has two columns (this often seems a direct copy and paste from the JGV profile).
8. Ensure all Figures and Tables are referenced somewhere in the text, often some of not.
9. Remove bold (and underlined if used) from all report headings and subheadings - Summary, Virion, Biology etc - although this can be done online, it is far easier to do it in Word
10. Ensure the report headings (Summary, Virion, etc) confirm to the **latest** style as specified in the chapter template e.g. only first letter capitalised, Antigenicity is now a sub-heading in Biology, it is no longer 'Phylogenetic relationships' but 'Relationships within the taxa', etc, etc.
11. Ensure report headings/sections are in the correct order (see chapter template) - particularly Antigenicity and genera pages where there have been recent changes in the location of Derivations of names and also demarcation criteria.
12. Delete anything that shouldn't be there - there are often things from the template left in like 'Member species table auto populated' or unassigned species sections when there aren't any etc.
12. Turn off Endnote hyperlinks if they are on (where you can click on the citation and it will jump to the bibliography at the end of the Word document): Word -> EndNote -> Configure bibliography -> uncheck 'Link intext citations ...'
13. Convert everything to single line spacing (often individual sections, or the whole thing is double spaced).
14. Other things to look out for - more recently a lot of hyperlinks seem to be 'hidden' within the text (looks like someone colours them black and gets rid of underline rather than removing the hyperlink), sometimes to Wikipedia pages, sometimes an individual word but sometimes a whole paragraph - as they are hidden they only become apparent after pasting into the online editor (where they become visible), in which case one must go back and fix within word and re-paste.

## Family page - online editor ##

To **Edit** a page online, simply scroll down to the bottom of the page and click the **Edit** button (you need to be logged in to see it).

Select all the family page text from the Word document and copy and paste it into the family page Body text field online.

Unfortunately, this does not (at least for me) preserve the Heading levels, so these need to be changed online:

- Main headings - Summary, Virion etc should be heading 2
- Subheadings such as Antigenicity within Biology should be heading 4 (subheadings were previously heading 3 combined with indentation, without indentation it is hard to distinguish headings 2 and 3, so this was dropped to heading 4)

```
Format -> Formats -> Headings -> Heading 2

Format -> Formats -> Headings -> Heading 4
```

### Empty Lines ###

Typically in Word, new (empty) lines are used to visually separate paragraphs from each other. Unfortunately, this translates to empty paragraphs online creating large white space gaps. Therefore, all empty lines should be deleted after pasting the text into the Body text field online. This could of course be done in Word prior to uploading (but does the make the word doc rather ugly to read).

### Table 1 ###
Turn on the border of Table 1 (the summary table), select the table and then:

```
Table -> Table properties -> enter 1 into Border
```

### Figures ###

The ICTV Report style specifies that images should be inserted into a table (1 column, 2 rows) with a border: 1st row for the figure itself, and 2nd row for the legend.

Tables can be inserted (into the appropriate location) via the GUI:

```
Table -> Table -> Select a 1x2 table from the grid
```

A border will need to be added, see the instructions for Table 1 above. Alternatively, tables with a border can be inserted directly via the source code:

```
Tools -> Source code
```

And paste the following into the correct location

```
<table border="1">
<tr>
<td></td>
</tr>
<tr>
<td></td>
</tr>
</table>
```

You will then need to copy/paste the appropriate figure legend into the 2nd row of its corresponding table. This all could also be done in Word beforehand.

Figures should be converted to **png** or **jpeg**. PDFs and TIFs will not be displayed (a download link to the file itself will be shown).

Figures should be cropped to remove excessive whitespace (often they come in as an entire A4 image with loads of whitespace). The width of the online report is very limited so excessive whitespace can result in images that appear very small.

Multiple figures may need to be combined into a single image, i.e. if panels have been submitted individually, and may need (A) and (B) or (i) and (ii) etc labels added.

To insert a Figure:

```
Insert -> Image/video/file
```

Click the **Upload** button (recently this just looks like text, but it is a button), and navigate to the file you want to upload on your computer, and click **OK**.

To resize a figure, double click it and resize it via the **Dimensions** fields.

The alignment of a figure can also be changed, typically 'center' is used:

```
Format -> Formats -> Alignment -> Center
```

### Anchors ###

Genera pages (as well as other pages) often refer back to the family page, particularly for Figures or if a genus page has an empty section. To enable the hyperlink from a genus page to jump to the correct location within the family page anchors should be used. To insert an anchor, select the text/figure to be anchored and:

```
Insert -> Anchor
```

Technically you only need to anchor those elements that are being linked to, but I typically anchor the main headings by default (Heading/Figure name -> Anchor name):

- Summary -> Summary
- Virion -> Virion
- Genome organization and replication -> Genome
- Biology -> Biology
- Relationships within the family -> Phylogeny
- Figure 1.Myviridae -> Fig1
- etc

How to utilise the anchor is covered in the genera page section later.

**NB:** sometimes similar links are required from one genus page to another, or from a genus to a subfamily page, anchors can be used again in such cases to ensure the link goes to the right section of the target page.

### Resources link ###

Add a hyperlink from phylogeny figure(s) (typically in the 'Relationships...' sections) to the Resources page in the form:

```
This phylogenetic tree and corresponding sequence alignment are available to download from the Resources page.
```

Where 'Resources page' is a hyperlink to the corresponding Resources page.

See the Resources page section below for the other side of this.

### Member taxa ###

A list of all the member taxa should be created at the end of the chapter. This is essentially a list of all the subfamilies and genera in the chapter, which are hyperlinked to the correct page.

- The heading title is 'Member taxa'
- The taxa are indented to reflect parent/child relationships, e.g. a genus within a subfamily
- The taxa are sorted alphabetically but with genera nested within their parent subfamily (if any)
- Subgenera are not currently included in this list (as they do not have their own page)
- 'Unassigned species' should be included if they exist at the end of the list
- Hyperlinks to the corresponding taxa page should be created for each entry
- Bullet points are used (there is a button on the GUI)

At this point if you compare the list created to the taxonomy browser on the left-hand side, if often becomes apparent if a taxon has been missed from the chapter word document by the SG (or if you have missed one during the transfer from Word to Web).

### Chapter information ###

At the very top of the chapter there should be a collection of information about the authors, the citation, the corresponding author's name & email, the editors, and the date updated.

Authors names are in bold, the ICTV Report Consortium is not included as an author here (but is on the Citation page).

The citation is in a 2 line form, with the 1st line ending with 'Author et al., (Year):' and the 2nd line starting with 'ICTV Virus Taxonomy Profile:', e.g. [*Flaviviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/flaviviridae):

The citation for this ICTV Report chapter is the summary published as Simmonds et al., (2017):  
ICTV Virus Taxonomy Profile: *Flaviviridae*, Journal of General Virology, 98:2–3.

As with the Citation page, this will need to be created as 'In Press' initially and edited at a later date when it is published along with a hyperlink to the JGV website. The hyperlink should be added to the publication title.

And then the following, bold title, non-bold info:

**Corresponding author:** Name (email address)  
**Edited by:** Editor names  
**Posted:** July 2021  
**PDF:** TBA 

The above elements are on new lines within one paragraph, as with the Authors page either use Div blocks or adjust the Source code to use \<br\> breaks.

Again, if in doubt, check another chapter out, you can always copy and paste the source code from there and edit it for the new chapters details.

### PDFs ###

PDFs will be discontinued for now as needs frequent updating, so they should not be added onto new/updated chapters for now.

**RJO ToDo:** get PDF pipeline in a sharable shape, but it will be a Mac/Linux only affair due to the libraries it uses.

### Updates ###

Major updates (i.e. taxonomic updates via the Study Group rather than a typo update) should be recorded in the **Posted:** field in the chapter info at the top of the chapter, in the form:

[*Flaviviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/flaviviridae)  
**Posted:** January 2017, updated February 2019

[*Rhabdoviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/negative-sense-rna-viruses/w/rhabdoviridae)  
**Posted:** April 2018, updated November 2019 & March 2021

## Resources page ##

The main function of the Resources page is to store the sequence alignments and phylogenetic trees of the chapter, but can also be used to highlight links to other Wiki's and resources.

Alignments and trees should be in a section entitled (heading 2):

**Sequence alignments and tree files:**

With an indented subheading (heading 4) of the actual Figure number:

**Figure 1.*Flaviviridae*:**


To upload alignments and trees:

```
Insert -> Image/video/file
```

Navigate to the file on your local computer via the Upload button. Upon uploading it will show the file as a large thumbnail. Click on the thumbnail to show some options and select **Convert to link** which will convert it to a hyperlink. This hyperlink then needs to be edited to give it a different display name such as 'Sequence alignment (FASTA format)'.

Typically, external resources are listed first under a heading Websites (heading 2).

For an example, see: 

[Resources: *Flaviviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/flaviviridae/371/resources-flaviviridae)

[Resources: *Papillomaviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/dsdna-viruses/w/papillomaviridae/893/resources-papillomaviridae)


For chapters with no resources, the default is

**Sequence alignments and tree files:** (heading 2)

None currently associated with this report. (indented)

For an example, see:

[Resources: *Ampullaviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/dsdna-viruses/w/ampullaviridae)

## Genera pages ##

The process for genera pages is much the same as the top level family one - after you copy and paste the contents from the Word file, sort the headings out (heading 2 and heading 4), remove blank lines, insert images, etc, etc. Extra things for a genus page are:

### Headings ###

If this is not a single genus family, then the following headings/sections are required in the following order:

- Distinguishing features 
- Virion
- Genome organization and replication 
- Biology
- Derivation of names
- Species demarcation criteria
- Member species

Followed by (if it exists):

- Related, unclassified viruses

The page starts with a Distinguishing features section/heading (unlike family pages which start with a Summary section/heading)

Often, a section (such as Virion) within a genus page may be empty. In such cases, the following text should be used (e.g. see [*Ascovirus*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/dsdna-viruses/w/ascoviridae/408/genus-ascovirus)):

```
See discussion under family description.
```

With the text 'family description' being a hyperlink to the corresponding section on the family page. This is where the anchors come in. To utilise an anchor to say the Virion section of the *Flaviviridae* chapter use the below hyperlink (note the #Virion at the end - the name of anchor assigned previously to the Virion heading):

[https://talk.ictvonline.org/ictv-reports/ictv\_online\_report/positive-sense-rna-viruses/w/flaviviridae#Virion](https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/flaviviridae#Virion)

The same process can be used to link to Figures or to other pages

### Single genus families ###
If there is only a single genus in the family/chapter then most (all) of the information will likely be on the family page. Therefore, the Distinguishing features section should say:

```
Since only one genus is currently recognized, the genus description corresponds to the family description.
```

Again with 'family description' being a hyperlink to the family page.

In addition, for single genus families, there is no need to list all the other headings/sections if they are empty, only sections that have additional content should be displayed ('Member species' should always be there however). For example, see [*Asfivirus*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/dsdna-viruses/w/asfarviridae/839/genus-asfivirus).

### Member species ###

This table should be inserted under the **Member species** heading:

```
Insert -> ICTV Virus Properties table
```

Then enter the genus name (or subgenus) into the 'The top-level taxa name' text field.

Underneath the table the following text should be placed (heading level 5 and indented):

```
Virus names, the choice of exemplar isolates, and virus abbreviations, are not official ICTV designations.
```

Alternatively, this can be pasted directly into the source code with:

```
<h5 style="padding-left: 30px;">Virus names, the choice of exemplar isolates, and virus abbreviations, are not official ICTV designations.</h5>

```

### Subgenera ###

To date, there has not been a chapter that really describes subgenera in any detail such as demarcation criteria. They are currently simply handled by splitting the Member species section on the genus pages into multiple sections - one for each subgenus with the heading **Member species - subgenus** ***Mysubvirus*** and its own member species table.

For an example, see [*Arteriviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/arteriviridae)

**NB:** typically the word document does not indicate that subgenera exist in the genus, so check the taxonomy browser.

### Related, unclassified viruses ###

There is a simple **Java** script **ICTV_TableLinks** to create GenBank links within the 'Related, unclassified viruses' table. Again, this utilises the **Source code** of a page. Copy and paste the source code of **ONLY** the **table** in question into a local file (including the table html tags). If the table is in the standard format (1 header row, 3 columns, 2nd column accession number) then the script can just be run on the file only:

```
java -jar ICTV_TableLinks.jar source_code.txt
```

Otherwise you will need to provide what column the accesion numbers are in and the total number of columns (both parameters simple integer numbers):

```
java -jar ICTV_TableLinks.jar source_code.txt accession_col total_cols
```

This will create an output file called **source_code_out.txt**, this should be copied and pasted to replace the source code of the original table **only** (i.e. it is the source code of the table only, not the whole page).

The table itself may need to be modified when uploaded to the web and before running the scripts. Multiple accession numbers (e.g. for segmented viruses) need to be in a structured format with a colon (:) used to separate a name (e.g. RNA1, RNA2 etc) from the accession number, and a semi-colon used to separate multiple sequences in the column. In addition, although the script handles an asterisk after the accession number (for footnotes), there are sometimes many different footnotes used, these will need to be deleted and re-created pre and post script.

Acceptable formats for the accession column are:

- Accession
- Accession, Accession, Accession
- Label: Accession
- Label: Accession; Label: Accesion; Label Accesion
- Blank

The script will link to ncbi nucleotide only - if alternative accesions are used - they may need to be fixed manually if they do noy auto-redirect on the NCBI end.

An example is uploaded to the repo from the [*Mammarenavirus*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/negative-sense-rna-viruses/w/arenaviridae/1117/genus-mammarenavirus) genus page, input file = **mamma_table.txt** and output file = **mamma_table_out.txt**, usage:

```
java -jar ICTV_TableLinks.jar mamma_table.txt
```

**NB:** you will need to supply the full path to the files if they are not in the current directory

**NB:** you will need to provide the path/location to the folder ICTV_TableLinks.jar is stored in if not in the current folder

**NB:** you will need [**Java**](https://www.oracle.com/uk/java/technologies/javase-jre8-downloads.html) installed on your machine to run it, and need to run it through the Terminal/MS-DOS Prompt

Underneath the Related, unclassified viruses table the following text should be placed (heading level 5 and indented):

```
Virus names and virus abbreviations, are not official ICTV designations.
```

Alternatively, this can be pasted directly into the source code with:

```
<h5 style="padding-left: 30px;">Virus names and virus abbreviations, are not official ICTV designations.</h5>

```

**NB:** note this is different to the Member species text

### Unassigned species ###

You will need to check whether there are any floating species (not in a genus) within the family, this is typically not indicated in the word doc (or the section is left in where there are in fact none). This can be either at the family or the subfamily level. 

At the family level, the title of the page (for the TOC) is **'Unassigned species'** whilst the top heading (h2) of the page is **'Unassigned species in family *Myviridae*'**. The member species table (ICTV Virus Properties table) should be pasted directly under this heading; after entering the appropriate taxon name, select 'Only unassigned species' from the 'What species should be displayed?' dropbox. For example, see [*Geminiviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/ssdna-viruses/w/geminiviridae/621/unassigned-species).

For subfamilies, the Unassigned species table has previously been added to the subfamily page itself rather than on a separate page under a heading **'Species unassigned to a genus'**. For example, see [*Herelleviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/dsdna-viruses/w/herelleviridae/1267/subfamily-bastillevirinae) subfamilies. 

Note both these example chapters actually need updating as the tables are currently empty due to taxonomic updates.


## Subfamily pages ##

Subfamily pages are currently a little mixed, at the minimum they have should have a Distinguishing features and Member taxa section (hyperlinked list of genus pages within the subfamily). Ideally, the page should have a Genus demarcation criteria sections as well.

For examples, see: 

[*Herelleviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/dsdna-viruses/w/herelleviridae)  
[*Papillomaviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/dsdna-viruses/w/papillomaviridae)



## Report Index ##

Previously, chapter Wiki's would be listed on the [main report page](https://talk.ictvonline.org/ictv-reports/ictv_online_report/) by default, however due to updates in the Telligent system this functionality stopped. Therefore, a new report chapter Wiki must be manually added to the [main report page](https://talk.ictvonline.org/ictv-reports/ictv_online_report/).

```
Edit -> Manage Group Theme -> Edit this page
```

Select the **'Configure'** option (the cog wheel) on the chapter index element to launch an editor for that component. This will enable you to insert a new chapter by using a new bullet point and hyperlink.

Not only do you need to click **Save**, but you also need to click the **Publish** button on the original **Edit** menu when done.

## References ##

The EndNote library **ICTV_HyperlinksHover** changes the references within Word so that they have the information needed to create the hoverable hyperlinks (e.g. article and journal title). 

This changes references in the word document from:

```
Ptchelkine et al., 2017
```

to:

```
[{Ptchelkine et al., 2017:29127347RJOHTXPtchelkine et al., 2017, Unique architecture of thermophilic archaeal virus APBV1 and its genome packaging, Nat Commun, 8, 1, 1436}]. 
```

After uploading to the web, there is a script that can be run on the source code that will convert it to a hyperlink to the correct PubMed page, whilst changing the text displayed to simply 'Ptchelkine et al., 2017' and making the hyperlink hoverable with the extra information.

The script requires three things:

- The source code for the whole page should be copied into a local file
- A local file of the bibliography (i.e. what is originally pasted into the References page) is also needed - this is so that Smith, 2008a and Smith 2008b references can be re-instated which are otherwise lost (although they still have distinct hover information and hyperlink to different PudMed pages) (I believe this is due to EndNote figuring out that it now longer needs A and B as the references are distinguishable as they have different titles etc).
- The URL of the chapter's References page. Non PubMed references link to this page as they can't link to PubMed.

The script then creates a new modified version of the source code which should be used to replace the original online version of the source code via copy and paste.

A Java jar program **ICTV_RefLinks** has been uploaded to the repo that should be used as:

```
java -jar ICTV_RefLinks.jar source_code.txt references.txt url
```

As an example, a short section of the source code from the [*Hepacivrus*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/flaviviridae/362/genus-hepacivirus) genus report page is uploaded (hepaci_source.txt), the references from the [*Flaviviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/flaviviridae) chapter (flavi_refs.txt), and the URL for the *Flaviviridae* chapter is [https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/flaviviridae/365/references-flaviviridae](https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/flaviviridae/365/references-flaviviridae). This should be run as:

```
java -jar hepaci_source.txt flavis_ref.txt https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/flaviviridae/365/references-flaviviridae
```

This will create a file called **hepaci_source_out.txt** which contains the modified source code which should be uploaded to the ICTV Report website to replace the old code.

**NB:** you will need to supply the full path to the files if they are not in the current directory

**NB:** you will need [**Java**](https://www.oracle.com/uk/java/technologies/javase-jre8-downloads.html) installed on your machine to run it, and need to run it through the Terminal/MS-DOS Prompt

Obviously, this step can be ignored if not doing hoverable hyper-linked references.

## Overview ##

As said before the simplest way is to open an existing chapter and copy the style there, they should all be pretty much the same.

Good example chapters:

- [*Flaviviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/flaviviridae): multiple genera, no subfamilies or subgenera, further reading
- [*Thaspiviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/dsdna-viruses/w/thaspiviridae): single genus family, no resources
- [*Arteriviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/arteriviridae): large family, subfamilies and subgenera
- [*Roniviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/positive-sense-rna-viruses/w/roniviridae): single genus, subgenera, subfamily (but no subfamily page)
- [*Deltavirus*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/negative-sense-rna-viruses/w/deltavirus): the only floating genus chapter currently (needs updating)
- [*Parvoviridae*](https://talk.ictvonline.org/ictv-reports/ictv_online_report/ssdna-viruses/w/parvoviridae) - a completely out of date chapter - the current taxonomy does not match the report
