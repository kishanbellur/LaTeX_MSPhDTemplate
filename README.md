LaTeX: University of Cincinnati - MS/PhD Template
================

What is this?
-------------------

A LaTeX template for writing MS thesis or PhD dissertation (for 
double-sided printing)

Disclaimer
-------------------

These files are distributed in the hope that they will 
be useful, but without any warranty; without even the implied warranty of 
merchantability or fitness for a particular purpose.

Using this template is not a substitute for learning LaTeX and/or 
understanding its how it works. Also, using this template does not 
necessarily guarantee that the Graduate College will approve the 
thesis/dissertation. The Graduate College reserves every right to request 
changes in the future that are not covered by this template yet. 


Features
-------------------

Apart from modularizing the document preparation process, and producing title 
and signature pages, etc. in compliance with the Graduate College requirements, 
the template provides the following:

  1. Ability to accommodate up to two advisors

  2. Ability to accommodate up to four advisory committee members

  3. Embdedded fonts - the PDF looks the same when printed as it looks 
     when it’s viewed on computer

  4. If using Linux/UNIX or Mac, the process of generating the PDF could 
     be as simple as typing ```make```

  5. Ability to make a timestamp-based snapshot of the entire folder via
     the command ```make snapshot```

Neither this template nor its author, however, will typeset your report,
thesis or dissertation for you. You are responsible for it.


What all does one need to get started?
-------------------

  1. Access to a complete installation of LaTeX:

     1. [TeXLive](http://www.tug.org/texlive/) for Linux and Mac, and
        [MiKTeX](http://miktex.org/) for Windows.
        This will likely come with [TeXMaker](http://www.xm1math.net/texmaker/) - a LaTeX-aware text 
        editor.
        
     3. As an alternative, use an online platform such as [Overleaf](https://www.overleaf.com) for simplicity.

  2. This template in its entirety

  3. Basic understanding of how LaTeX works


Which files should one edit?
-------------------

  1. Rename (not just copy over) ```6+2_DEGREE.tex``` by substituting ```6+2``` with your UC 6+2 user ID, and ```DEGREE``` with either ```MS``` or ```PhD```

  2. Open the renamed ```6+2_DEGREE.tex```

     1. Iff writing a MS thesis, then change ```\documentclass[Degree=PhD]{UC}``` to ```\documentclass[Degree=MS]{UC}```

     2. Comment the lines marked ```% Optional``` under ```Front Matter``` section if there is a need

     3. Remove some or add more chapters under ```Chapters``` section as needed

     4. Remove some or add more appendices under ```Appendices``` section as needed

  3. Update ```Personalize/Personalize.tex``` with relevant information

  4. Update ```FrontMatter/Abbreviations.tex```, ```FrontMatter/Abstract.tex```, ```FrontMatter/Acknowledgments.tex```, ```FrontMatter/Dedication.tex```, ```FrontMatter/Definitions.tex``` and ```FrontMatter/Preface.tex``` with relevant information

  5. Update ```Chapters/Chapter?.tex``` with relevant information

  6. Save all references in ```References/References.bib``` with relevant information

  7. Change ```\bibliographystyle{jpc}``` in ```References/References.tex``` to something else to produce the required format for references

  8. Update ```Appendices/Appendix?.tex``` with relevant information

  9. Place all figures in ```Figures``` folder

  10. Update ```UC.cls``` and/or ```Packages/*.sty``` iff there is a need, and iff there is an understanding of how the LaTeX class/style file works


How does one compile?
-------------------

**Using ```overleaf```:**

```
compile 6+2_DEGREE.tex
```

**Linux (or Mac) from a terminal using the command line, using ```Makefile```:**

```
cd LaTeX_MSPhDTemplate
make
```

**Linux (or Mac) from a terminal using the command line, without using ```Makefile```:**

```
cd LaTeX_MSPhDTemplate
latex --shell-escape 6+2_DEGREE
bibtex 6+2_DEGREE
latex --shell-escape 6+2_DEGREE
latex --shell-escape 6+2_DEGREE
dvips -R0 -Ppdf -t letter -o 6+2_DEGREE.ps 6+2_DEGREE.dvi
ps2pdf -dPDFSETTINGS=/prepress -dSubsetFonts=true -dEmbedAllFonts=true -dMaxSubsetPct=100 6+2_DEGREE.ps 6+2_DEGREE.pdf
```

**Mac using ```TeXMaker``` application:**

Navigate to ```TeXMaker » Preferences » Quick Build » Quick Build Command » User``` and enter the following

```
"/usr/texbin/latex" -interaction=nonstopmode %.tex | 
"/usr/texbin/bibtex" %.aux | 
"/usr/texbin/latex" -interaction=nonstopmode %.tex | 
"/usr/texbin/latex" -interaction=nonstopmode %.tex | 
"/usr/texbin/dvips" -Ppdf -o %.ps %.dvi | 
"/usr/local/bin/ps2pdf" -dPDFSETTINGS=/prepress -dEmbedAllFonts=true -dSubsetFonts=true -dMaxSubsetPct=100 %.ps
```

**Windows using ```TeXMaker``` application:**

Navigate to ```TeXMaker » Options » Configure TeXMaker » Quick Build » Quick Build Command » User``` (a recent and stable version of GhostScript, GhostPCL, GhostXPS and MuPDF can be downloaded from http://ghostscript.com/; check the path to ```gswin32c.exe```; thanks to Henriette Groenvik for bringing a typographical error to author's attention) and enter the following

```
latex -interaction=nonstopmode %.tex | 
bibtex % | 
latex -interaction=nonstopmode %.tex | 
latex -interaction=nonstopmode %.tex | 
dvips -Ppdf -o %.ps %.dvi | 
"C:/Program Files (x86)/gs/gs9.00/bin/gswin32c.exe" -dBATCH -dNOPAUSE -sDEVICE=pdfwrite -r600 -dCompatibilityLevel=1.4 
-dPDFSETTINGS=/printer -dEmbedAllFonts=true -dSubsetFonts=true -dMaxSubsetPct=100 -sOutputFile="%.pdf" "%.ps"
```

What if one needs colored text?
-------------------

The template provides the following 140 named colors (given with their hexadecimal notation; color scheme adopted from http://www.w3schools.com/html/html_colorvalues.asp). Example usage: 

```\textcolor{Color}{colored text}```


| Hex code | Color             | Hex code | Color                |
|:---------|:------------------|:---------|:---------------------|
| #000000  | Black             | #BA55D3  | MediumOrchid         |
| #000080  | Navy              | #BC8F8F  | RosyBrown            |
| #00008B  | DarkBlue          | #BDB76B  | DarkKhaki            |
| #0000CD  | MediumBlue        | #C0C0C0  | Silver               |
| #0000FF  | Blue              | #C71585  | MediumVioletRed      |
| #006400  | DarkGreen         | #CD5C5C  | IndianRed            |
| #008000  | Green             | #CD853F  | Peru                 |
| #008080  | Teal              | #D2691E  | Chocolate            |
| #008B8B  | DarkCyan          | #D2B48C  | Tan                  |
| #00BFFF  | DeepSkyBlue       | #D3D3D3  | LightGray            |
| #00CED1  | DarkTurquoise     | #D8BFD8  | Thistle              |
| #00FA9A  | MediumSpringGreen | #DA70D6  | Orchid               |
| #00FF00  | Lime              | #DAA520  | GoldenRod            |
| #00FF7F  | SpringGreen       | #DB7093  | PaleVioletRed        |
| #00FFFF  | Aqua              | #DC143C  | Crimson              |
| #00FFFF  | Cyan              | #DCDCDC  | Gainsboro            |
| #191970  | MidnightBlue      | #DDA0DD  | Plum                 |
| #1E90FF  | DodgerBlue        | #DEB887  | BurlyWood            |
| #20B2AA  | LightSeaGreen     | #E0FFFF  | LightCyan            |
| #228B22  | ForestGreen       | #E6E6FA  | Lavender             |
| #2E8B57  | SeaGreen          | #E9967A  | DarkSalmon           |
| #2F4F4F  | DarkSlateGray     | #EE82EE  | Violet               |
| #32CD32  | LimeGreen         | #EEE8AA  | PaleGoldenRod        |
| #3CB371  | MediumSeaGreen    | #F08080  | LightCoral           |
| #40E0D0  | Turquoise         | #F0E68C  | Khaki                |
| #4169E1  | RoyalBlue         | #F0F8FF  | AliceBlue            |
| #4682B4  | SteelBlue         | #F0FFF0  | HoneyDew             |
| #483D8B  | DarkSlateBlue     | #F0FFFF  | Azure                |
| #48D1CC  | MediumTurquoise   | #F4A460  | SandyBrown           |
| #4B0082  | Indigo            | #F5DEB3  | Wheat                |
| #556B2F  | DarkOliveGreen    | #F5F5DC  | Beige                |
| #5F9EA0  | CadetBlue         | #F5F5F5  | WhiteSmoke           |
| #6495ED  | CornflowerBlue    | #F5FFFA  | MintCream            |
| #66CDAA  | MediumAquaMarine  | #F8F8FF  | GhostWhite           |
| #696969  | DimGray           | #FA8072  | Salmon               |
| #6A5ACD  | SlateBlue         | #FAEBD7  | AntiqueWhite         |
| #6B8E23  | OliveDrab         | #FAF0E6  | Linen                |
| #708090  | SlateGray         | #FAFAD2  | LightGoldenRodYellow |
| #778899  | LightSlateGray    | #FDF5E6  | OldLace              |
| #7B68EE  | MediumSlateBlue   | #FF0000  | Red                  |
| #7CFC00  | LawnGreen         | #FF00FF  | Fuchsia              |
| #7FFF00  | Chartreuse        | #FF00FF  | Magenta              |
| #7FFFD4  | Aquamarine        | #FF1493  | DeepPink             |
| #800000  | Maroon            | #FF4500  | OrangeRed            |
| #800080  | Purple            | #FF6347  | Tomato               |
| #808000  | Olive             | #FF69B4  | HotPink              |
| #808080  | Gray              | #FF7F50  | Coral                |
| #87CEEB  | SkyBlue           | #FF8C00  | DarkOrange           |
| #87CEFA  | LightSkyBlue      | #FFA07A  | LightSalmon          |
| #8A2BE2  | BlueViolet        | #FFA500  | Orange               |
| #8B0000  | DarkRed           | #FFB6C1  | LightPink            |
| #8B008B  | DarkMagenta       | #FFC0CB  | Pink                 |
| #8B4513  | SaddleBrown       | #FFD700  | Gold                 |
| #8FBC8F  | DarkSeaGreen      | #FFDAB9  | PeachPuff            |
| #90EE90  | LightGreen        | #FFDEAD  | NavajoWhite          |
| #9370DB  | MediumPurple      | #FFE4B5  | Moccasin             |
| #9400D3  | DarkViolet        | #FFE4C4  | Bisque               |
| #98FB98  | PaleGreen         | #FFE4E1  | MistyRose            |
| #9932CC  | DarkOrchid        | #FFEBCD  | BlanchedAlmond       |
| #9ACD32  | YellowGreen       | #FFEFD5  | PapayaWhip           |
| #A0522D  | Sienna            | #FFF0F5  | LavenderBlush        |
| #A52A2A  | Brown             | #FFF5EE  | SeaShell             |
| #A9A9A9  | DarkGray          | #FFF8DC  | Cornsilk             |
| #ADD8E6  | LightBlue         | #FFFACD  | LemonChiffon         |
| #ADFF2F  | GreenYellow       | #FFFAF0  | FloralWhite          |
| #AFEEEE  | PaleTurquoise     | #FFFAFA  | Snow                 |
| #B0C4DE  | LightSteelBlue    | #FFFF00  | Yellow               |
| #B0E0E6  | PowderBlue        | #FFFFE0  | LightYellow          |
| #B22222  | FireBrick         | #FFFFF0  | Ivory                |
| #B8860B  | DarkGoldenRod     | #FFFFFF  | White                |


Got questions? Need help?
-------------------

Refer to the [formatting guidelines by the graduate college at University of Cincinnati](https://grad.uc.edu/student-life/etd/formatting.html).

DO NOT send your comments, concerns, issues and/or questions about this
template to UC's Graduate College or Information Technology.
[Google](http://google.com/) search often provides a quick and reliable answer.
If all else fails, then contact the author. Understand that this is a pro-bono
project. Author may very well be busy with work and life responsibilities and
as such, do not expect a quick answer/solution.


Don't like this template OR have an idea to improve?
-------------------

Feel free to clone/fork this repository and make changes to fit your needs. 
You have my explicit permission to do so. This template and/or the changes 
you make may very well work for you (or your institution). Please note that
if you decide to do so, you are doing so entirely at your very own discretion 
and that neither the author nor the institution is 
responsible for any/all damage - intellectual and/or otherwise.

Credit
-------------------
The author is grateful to [Dr. Gowtham ](https://sgowtham.com/) who initially created this for students at Michigan Tech students. The original template was forked and since been modified/adapted for use at University of Cincinnati.

Author
-------------------
Kishan Bellur, PhD         
Assistant Professor  
Mechanical and Materials Engineering  
University of Cincinnati  
Email: bellurkn@ucmail.uc.edu               
URL: https://kishanbellur.github.io
