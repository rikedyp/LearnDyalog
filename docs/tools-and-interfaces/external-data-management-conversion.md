# External Data Management and Format Conversion
Reading data into and getting data out of the workspace.

There are some in-built tools for importing data from files and the internet. If you are already familiar with [python](./external-language-interfaces-standard-libraries.md#python-pynapl), [R](./external-language-interfaces-standard-libraries.md#r-language-rsconnect) or [.NET](./external-language-interfaces-standard-libraries.md#net) then you can use one of the [external language bridges](./external-language-interfaces-standard-libraries.md) to bring data into APL from files via one of these languages. However, it can be simpler and faster in many cases to use one of the following tools.

## Text Files
[:material-web: Read Text File documentation](https://help.dyalog.com/latest/#Language/System%20Functions/nget.htm)  
[:material-web: Write Text File documentation](https://help.dyalog.com/latest/#Language/System%20Functions/nput.htm)

`⎕NGET` and `⎕NPUT` can be used to read and write text files.

>```APL
>(⊂words)⎕NPUT'data/words.txt'                      ⍝ Write words to a unicode text file
>(content encoding newline)←⎕NGET'data/words.txt'   ⍝ Read words from a unicode text file
>words←(⎕UCS newline)((~∊⍨)⊆⊢)content               ⍝ Split words on each new line 
>```

## ⎕CSV
[:material-web: Comma Separated Values documentation](https://help.dyalog.com/latest/#Language/System Functions/csv.htm)  
[:fontawesome-brands-youtube: Video: Parsing content from text files using ⎕CSV](https://www.youtube.com/watch?v=AHoiROI15BA)

The Comma Separator Values system function `⎕CSV` can read tabular data from `.csv` files as APL matrices. Here are some features of `⎕CSV`:

*[CSV]: Comma Separated Values

Read data from and write data to files directly  

>```APL
>data ← ⎕CSV '/path/to/file.csv'   ⍝ Read from file.csv
>data ⎕CSV '/path/to/file.csv'     ⍝ Write to file.csv
>```

Separate the header (first row) from the rest of the data:

>```APL
>(data header) ← ⎕CSV '/path/to/file.csv' ⍬ ⍬ 1
>```

Treat specific columns of input as numeric or text, depending on the options provided.  

>```APL
>numeric_if_possible ← ⎕CSV '/path/to/file.csv' ⍬ 4
>```
> The `4` in this example indicates to convert numeric values if possible, and otherwise keep the value as text:

Use a separator other than commas, using the "Separator" variant option, for example using tabs (`⎕UCS 9`) for Tab Separated Values (.tsv).  

>```APL
>tsv ← ⎕CSV⍠'Separator' (⎕UCS 9)⊢'/path/to/file.tsv'
>```

Read data chunks at a time so as to not fill the workspace, using the "Records" variant option.  

???Example "Example of using the Records variant option"
	```APL
		path ← '/path/to/file.csv'    ⍝ The file path as simple character vector
		ReadCSV10←⎕CSV⍠'Records' 10   ⍝ A function to read CSV 10 records at a time
		tn←path ⎕NTIE 0               ⍝ Tie the file - this locks it from use by other applications
		first10 ← ReadCSV10 tn        ⍝ Read the first 10 records (rows)
		second10 ← ReadCSV10 tn       ⍝ Read the next 10
		≢¨first10 second10
	10 10
		first10 second10
	┌──────────┬──────────┐
	│┌──┬─────┐│┌──┬─────┐│
	││1 │JQZUK│││11│DECJM││
	│├──┼─────┤│├──┼─────┤│
	││2 │ANPYW│││12│PXPGL││
	│├──┼─────┤│├──┼─────┤│
	││3 │WYVSR│││13│SYSCN││
	│├──┼─────┤│├──┼─────┤│
	││4 │ZOGOX│││14│EKDPS││
	│├──┼─────┤│├──┼─────┤│
	││5 │CXKRS│││15│XCOHA││
	│├──┼─────┤│├──┼─────┤│
	││6 │BFTYO│││16│RDAHR││
	│├──┼─────┤│├──┼─────┤│
	││7 │VFLAS│││17│KPUTW││
	│├──┼─────┤│├──┼─────┤│
	││8 │BAFYD│││18│TPDOD││
	│├──┼─────┤│├──┼─────┤│
	││9 │XPEBP│││19│BGIVA││
	│├──┼─────┤│├──┼─────┤│
	││10│UVBFG│││20│IITSO││
	│└──┴─────┘│└──┴─────┘│
	└──────────┴──────────┘
		⎕NUNTIE tn                    ⍝ Don't forget to untie the file after use!
	```

If you are reading large tabular data, you can use [`⎕MAP`](#map) to access the data without bringing it all into your workspace, potentially preventing a `WS FULL` error.

## `⎕JSON`
[:material-web: JSON Convert](https://help.dyalog.com/latest/#Language/System%20Functions/json.htm)

Convert between APL arrays and character vectors (text) in JavaScript Object Notation (JSON) format.

Lists can be represented as APL vectors.

>```APL
>      1⎕JSON (1 2 3)'ABCD'
>[[1,2,3],"ABCD"]
>```

Objects can be represented as APL namespaces.

>```APL
>      0⎕JSON '{"name":"David", "age": 42}'
>#.[JSON object]
>```

Both can be represented as a matrix of depth, name, value and type columns somewhat similar to that used by `⎕XML`.

>```APL
>      0 (⎕JSON ⎕OPT'Format' 'M')'[{"name":"David", "age": 42}, {"name": "Sandra", "age": 42}]'
>┌─┬────┬──────┬─┐
>│0│    │      │2│
>├─┼────┼──────┼─┤
>│1│    │      │1│
>├─┼────┼──────┼─┤
>│2│name│David │4│
>├─┼────┼──────┼─┤
>│2│age │42    │3│
>├─┼────┼──────┼─┤
>│1│    │      │1│
>├─┼────┼──────┼─┤
>│2│name│Sandra│4│
>├─┼────┼──────┼─┤
>│2│age │42    │3│
>└─┴────┴──────┴─┘
>```

## `⎕XML`
[:material-web: XML Convert documentation](https://help.dyalog.com/latest/#Language/System%20Functions/xml.htm)

*[XML]: Extensible Markup Language

`⎕XML` converts between XML character vectors and a nested matrices of node depth, tag name, value, attribute key/value pairs and markup description columns.

>```APL
>      ⎕XML'<name born="1920">Ken</name><name born="1925">Jean</name>'
>┌─┬────┬────┬───────────┬─┐
>│0│name│Ken │┌────┬────┐│5│
>│ │    │    ││born│1920││ │
>│ │    │    │└────┴────┘│ │
>├─┼────┼────┼───────────┼─┤
>│0│name│Jean│┌────┬────┐│5│
>│ │    │    ││born│1925││ │
>│ │    │    │└────┴────┘│ │
>└─┴────┴────┴───────────┴─┘
>```

## Regular Expressions
[:material-web: Search and Replace documentation](https://help.dyalog.com/latest/#Language/System%20Functions/r.htm)

Search and replace using regular expressions.

`⎕R` and `⎕S` are dyadic operators which allow searching text using Pearl Compatible Regular Expressions (PCRE).

Dyalog's search and replace accept multiple search and replace strings and/or functions in a single call.

**Example:** Convert what you say into what your dog Rex hears:

>```APL
>      Rex ← 'rex' 'food' '\w'⎕R'\0' '*'⍠1
>      Rex 'Rex, I told you not to do that! Now, Rex, go and wait outside'
>Rex, * **** *** *** ** ** ****! ***, Rex, ** *** **** *******
>```

## Microsoft Office (OLE Client)
[:fontawesome-solid-file-pdf: Chapter Q, Section 2 of Mastering Dyalog APL](https://www.dyalog.com/uploads/documents/MasteringDyalogAPL.pdf)  
[:fontawesome-solid-file-pdf: Chapter 9 of the Dyalog for Microsoft Windows Interface Guide](https://docs.dyalog.com/latest/Dyalog%20for%20Microsoft%20Windows%20Interface%20Guide.pdf#page=185)  
[:fontawesome-solid-file-pdf: Article: Charting the APL/Excel Waters](https://www.dyalog.com/uploads/conference/dyalog11/presentations/C05_using_excel_under_apl/officeauto11.pdf)  
[:fontawesome-brands-youtube: Dyalog Webinar: APL and Microsoft Excel](https://dyalog.tv/Webinar/?v=hs90SdUc9dE)  

OLE is a Microsoft technology which can be used to interface with Microsoft Office products, including Excel, PowerPoint and Word. The Dyalog OLE bridge is only on Microsoft Windows.

Here is a quick example to open a connection to Excel, create a workbook and add data to it.

```APL
      XL←⎕NEW'OLEClient'(⊂'ClassName' 'Excel.Application')
      XL.Visible←1
      XL.Workbooks.Add⍬
      XL.ActiveWorkbook.Sheets[1].Name
Sheet1
      XL.ActiveWorkbook.Sheets[1].Range[⊂'A1:A5'].Value2←⍪⍳5
      XL.ActiveWorkbook.Sheets[⊂'Sheet1'].Range[⊂'B1:B5'].Value2←⍪,¨'ABCDE'
```

## `⎕MAP`
[:material-web: `⎕MAP` documentation](http://help.dyalog.com/latest/#Language/System%20Functions/map.htm).

`⎕MAP` allows you to treat a file on disk as if it were a variable in the workspace. This is useful if you are working with data that cannot fit inside the available workspace memory. One approach might be to read the data in chunks and process one chunk at a time (for example, see the "Records" variant option for `⎕CSV`). Another approach is to use `⎕MAP`.

>```APL
>      text ← 80 ¯1 ⎕MAP '/path/to/file.txt'
>```

You must specify the type according to the [Data Representation `⎕DR`](http://help.dyalog.com/latest/#Language/System%20Functions/Data%20Representation%20Monadic.htm) of the data to be read.

## Binary files or arbitrary file types
[:fontawesome-solid-file-pdf: Native Files cheat sheet](https://docs.dyalog.com/latest/CheatSheet%20-%20Native%20Files.pdf)  
[:material-web: System Functions Categorised](https://help.dyalog.com/latest/#Language/System%20Functions/Summary%20Tables/System%20Functions%20Categorised.htm)

The term "Native Files" refers to any type of file on a hard disk. Some system functions beginning `⎕N` can be used to read and write files of arbitrary type and format.

>```APL
>      tn←'words.txt'⎕NTIE 0   ⍝ Tie the file, locking it from use by other processes
>      ⎕←10↑⎕NREAD tn 80 ¯1    ⍝ Read the data as Unicode text
>A
>A's
>AA's
>      ⎕NUNTIE tn              ⍝ Untie the file
>```

## APL Component files
[:fontawesome-brands-dyalog: Chapter N of Mastering Dyalog APL](https://www.dyalog.com/uploads/documents/MasteringDyalogAPL.pdf#page=557)  
[:material-web: Component Files Online Documentation](https://help.dyalog.com/latest/#Language/APL%20Component%20Files/Component%20Files.htm)  
[:fontawesome-solid-file-pdf: Chapter 5 of Dyalog Programming Reference Guide](https://docs.dyalog.com/latest/Dyalog%20Programming%20Reference%20Guide.pdf)

If it is only APL systems that need to store data, the most convenient and efficient way to store that data is in APL component files. Component files can store any type of APL array, including namespaces.

## Downloading data from the internet
See [HttpCommand](./communication-tools.md#httpcommand).

## SQL Interface
[:fontawesome-solid-file-pdf: SQL Interface Guide](https://docs.dyalog.com/latest/SQL%20Interface%20Guide.pdf)

SQAPL provides an interface to ODBC-compliant SQL databases including Oracle, Microsoft Access, MySQL, MariaDB and DB2. It contains functions to read, write and manage SQL databases. It is supported on all platforms, although some platforms could incur an additional licence fee for the server component of SQAPL.

For quick access to simply read data from or write data to a table, the functions `LoadSQL` and `SaveSQL` from the utility workspace `loaddata` may be all that you need.
