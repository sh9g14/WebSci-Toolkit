# LaTeX tutorial for University of Southampton PhD students
All the information you will need to get LaTeX up and running on your machine. 
~~~
Written using macOS but all software is cross-platform.
~~~
## Required TeX Distributions ##
**Windows:** Use MiKTeX, tutorial found at http://miktex.org/howto/install-miktex

**Mac:** Use MacTeX, tutorial found at http://www.tug.org/mactex/mactex-download.html

**ECS users** do not need this as all ECS-built computers come with a TeX distribution pre-installed.

## Required Software (all free!)
**TexMaker**
http://www.xm1math.net/texmaker/

### Recommended Software
**Github**
http://education.github.com/pack
Registering with a student account provides free private repositories, otherwise £5.02/mo (as of 19th March 2018)

**GitKraken**
http://www.gitkraken.com/
Used as a pretty GUI to manage Github changes.

**Mendeley**
http://www.mendeley.com/
A PDF management tool useful for exporting citation data into LaTeX via the BibTeX format.

**Nvivo**
http://www.qsrinternational.com/nvivo/nvivo-products
Another PDF management tool but with the ability to highlight text and assign it to nodes, such as assigning "Social media is the greatest thing since sliced bread" to Introduction. A free copy can be obtained via http://software.soton.ac.uk

## Step 1: Installation ##
Install Texmaker from http://www.xm1math.net/texmaker/

## Step 2: Templates ##
Go to http://library.soton.ac.uk/thesis/templates and click on LaTeX templates. Currently this houses a FPSE template only but this can be edited to suit your needs. Save this in a sensible location. Extract the contents.

## Step 3: Creating the main document ##
Open TexMaker and navigate to `ecsdocs->templates->latex->ecsdocs->Thesis.tex`. If you try to render the file now it will error as the template file is not in the same directory. Navigate to `ecsdocs->tex->latex->ecsdocs->ecsthesis.cls` and copy this into the same directory as your `Thesis.tex` file. For 9 month reviews use ecsprogress.cls. For 18 month reviews use ecsminithesis.cls. 

**Recommended:** Create a new folder (in your Github repository if that's set up) and copy the `Thesis.tex` and ecsthesis.cls files into it.

Inside the `Thesis.tex` file you will see a lot of marked-up text. This tells TexMaker and LaTeX to render this information in the appropriate places, so change this to fit your details. Below the dashed line you will see several `\include{ChapterName}` commands. These tell TexMaker to import other `.tex` files into your main `Thesis.tex` file as if they were chapters within the one file. It is recommended to split the chapters like this as if you are using one large `.tex` file then it gets messy very quickly. Also splitting the chapters is advantageous for tracking changes and version control. 

The names within the `\include{ChapterName}` need to match the names of the other `.tex` files in your directory, e.g. `\include{LiteratureReview}` would match the `LiteratureReview.tex` file. 

At the bottom you'll see `\bibliographystyle{ecs}`, and while there is an `ecs.bst` file in `ecsdocs->bibtex->bst->ecsdocs->ecs.bst`, changing `\bibliographystyle{ecs}` to `\bibliographystyle{apalike}` matches the Harvard referencing style and negates the need for a `.bst` file due to the `\usepackage{natbib}` command in the preamble. Though bear in mind referencing styles change depending on your department.

The final part of this step is to create a folder inside your directory for images. You can call it what you like, but the thesis template refers to `Figures` so call it that for now unless you wish to change it.

## Step 4: Splitting Chapters ##
Unlike the main document, you do not need to replicate the preamble for new chapters. You start with `\chapter{ChapterName}` as you would in the main document, then appropriate `\section{Section1}` `\subsection{Subsection1}` commands as appropriate. 

E.g.:

```latex
%% ----------------------------------------------------------------
%% Introduction.tex
%% ---------------------------------------------------------------- 
\chapter{Introduction} \label{Chapter:Introduction}
This is a chapter.

	\section{LaTeX}
		\subsection{Is}
			\subsubsection{The Best}
```      

## Step 5: General LaTeX Use ##
### Inserting Tables ###
Tables are finicky at the best of times in most word processors, none more so than in LaTeX. This is where the coder's mettle is tested. Thankfully, you only need to get it working once then copy the code over and over. 

To insert a table, the code is as follows:
```latex
\begin{table}[!htb] #htb is a combination of letters to tell LaTeX to place the table at the top (t) or bottom (b) of the page. Usually both work
  \begin{tabular}{ c | c | c } #Data is centred in the table, use l or r for left/right
  data1 & data2 & data3
  \end{tabular}
  \caption{This is a table}
  \label{Table1} #Refer to this in the text using \ref{Table1}
\end{table}  
```
Tables can often be placed in unexpected locations. Experience shows that carrying on as normal often forces the table to go where you want it to as sometimes the layout doesn't display properly until there is sufficient text before and after it. 

### Inserting Images ###
Thankfully this is a lot easier than tables as there is less customisation.

```latex
\begin{figure}
  \includegraphics[scale=1]{image1.png} 
  \caption{#image1.png refers to an image in your /Figures/ folder in your Thesis directory}
  \label{Image1} #Refer to this in text using \ref{Image1}
\end{figure}
```
The `[scale=1]` option allows you to modify the size of the image. If you are inserting a large image into a small section (e.g. ACM double column templates or the bottom of a page in your thesis) you can change the value to suit. `[scale=0.5` makes it half the size, `[scale=2]` makes it twice the size.

## Step 5: Rendering ##
In TexMaker, once you click the arrow icon at the top of the screen next to the Paste icon, TexMaker will render the LaTeX script into a PDF on the right hand side, as well as saving this PDF in the same directory as where your `Thesis.tex` file resides. Depending on the setup, you may need to change the rendering settings within TexMaker to make this possible. Go to Preferences (on the Mac, presumably Settings in Windows), then click on Commands (default view) then Embed in the bottom right corner as this allows for viewing the PDF alongside the code. Then click on Quick Build and select PdfLaTeX + View PDF if it is not already selected. 

## Step 6: Changing the .cls file ##
**REQUIRED** This is required by everyone as the ECS template is 7 years old and uses FPSE's old name of Faculty of Engineering, Science and Mathematics. Open up the ecsthesis.cls in TexMaker and search for `faculty`. You need to change the entries about halfway through the document (lines 162 and 165) to your respective Faculties. 

# External Links #
As with any process, LaTeX and TexMaker has a learning curve. It might seem all too complicate at first, but it gets considerably easier with practise. There are many different tutorials available on the web and if you come across an issue then Google is your friend.

For a list of LaTeX table types, [click here](https://www.sharelatex.com/learn/Tables). 
For more information about images, [click here](https://www.sharelatex.com/learn/Inserting_Images)
