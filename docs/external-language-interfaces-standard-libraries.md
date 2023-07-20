# External Language Interfaces and Standard Libraries

## .NET
[:fontawesome-solid-file-pdf: .NET Core Interface Guide](https://docs.dyalog.com/latest/dotNET%20Core%20Interface%20Guide.pdf)  
[:fontawesome-solid-file-pdf: Dyalog for Microsoft Windows .NET Framework Interface Guide](https://docs.dyalog.com/latest/Dyalog%20for%20Microsoft%20Windows%20.NET%20Framework%20Interface%20Guide.pdf)  
[:fontawesome-solid-file-pdf: Comparison of .NET Core/Framework Interfaces](https://docs.dyalog.com/latest/dotNET%20Differences.pdf)  

Whether you are using the .NET Framework for Microsoft Windows or the newer open-source cross-platform .NET Core, Dyalog APL can both call useful .NET libraries to perform activities like encryption and compression - and be integrated as a component within .NET frameworks like ASP.NET Core.

Dyalog’s .NET bridge automatically converts APL arrays to and from .NET types and makes it possible to hook APL functions up to .NET events. APL classes can be exported as .NET assemblies that can be consumed by frameworks and programs written in other .NET languages like C# and F#.

To use .NET functions and namespaces, set `⎕USING` and create an instance of a .NET class with `⎕NEW`.

```APL
      ⎕USING←'System'
      mydt ← ⎕NEW DateTime (2008 4 30)
      TimeZone.CurrentTimeZone.StandardName
GMT Standard Time
```

## Python (Py'n'APL)
[:fontawesome-brands-github: Dyalog/pynapl](https://github.com/Dyalog/pynapl)  
[:fontawesome-brands-youtube: Dyalog Webinar: Summer Intern Show](https://dyalog.tv/Webinar/?v=yk36ONBMK20)  
[:fontawesome-brands-youtube: Video: Python + APL = Py'n'APL at the Dyalog '22 User Meeting](https://dyalog.tv/Dyalog21/?v=gOUFXBUMv_A)

Call APL functions from Python, and call Python functions. Leverage the vast ecosystem of packages to solve well known tasks.

Py'n'APL can automatically convert between Python and APL data types, and converts Python iterable objects to APL vectors.

## R language (RSConnect)
[:fontawesome-brands-github: kimmolinna/rsconnect](https://github.com/kimmolinna/rsconnect)

Call R functions from APL using Rserve.

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

## LAPACK
[:fontawesome-brands-github: Dyalog/Math](https://github.com/Dyalog/Math)

The `Eigen` function in the `Math` library uses the C library LAPACK (Linear Algebra Package).

## FFTW
[:fontawesome-brands-github: Dyalog/Math](https://github.com/Dyalog/Math)

The `Fourier` function in the `Math` library uses the C library FFTW (Fastest Fourier Transform in the West).

## Compiled libraries interface (`⎕NA`)
The **Name Association** function ⎕NA provides access from APL to compiled functions within a library. 

[:material-web: Online documentation for Name Association ⎕NA](http://help.dyalog.com/latest/#Language/System%20Functions/na.htm)

A library is implemented according to the operating system as follows:

- a Dynamic Link Library (DLL) under Windows
- a Shared Library (.so or .dylib) under Linux and macOS
- a static library (.a) under AIX

A compiled library is a collection of functions typically written in C (or C++) each of which may take arguments and return a result.

Input and output data types must be explicitly declared.

## APL as a Shared Library
[:fontawesome-solid-file-pdf: APL as a Shared Library](http://docs.dyalog.com/latest/APL%20as%20a%20Shared%20Library.pdf)  
[:fontawesome-solid-file-pdf: The JSON_APL Shared Object](http://docs.dyalog.com/latest/The%20JSON_APL%20Shared%20Object.pdf)

An SDK which can be used to package APL code along with the Dyalog interpreter as a shared or static library (**.dll**, **.so**, **.dylib**). This library can then be called by any language which is able to access native shared libraries.

*[SDK]: Software Development Kit

The JSON_APL Shared Object offers a plug-and-play shared object with which users can call APL functions by passing character strings. It also functions as an example of using the shared library SDK.
