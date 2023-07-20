# User Commands
<span class="fa-file-pdf">:fontawesome-solid-file-pdf:</span> [User Commands User Guide](http://docs.dyalog.com/latest/User%20Commands%20User%20Guide.pdf)  
<span class="logo-youtube">:fontawesome-brands-youtube:</span> Video: [New User Commands in Dyalog v18.2](https://dyalog.tv/Webinar/?v=A6cNLh52BkI)  
<span class="logo-youtube">:fontawesome-brands-youtube:</span> Video: [Creating and managing your own User Commands](https://dyalog.tv/Webinar/?v=LWJzRGrOC3k)

User commands are tools that are available at any time, in any workspace, as extensions to the Dyalog development environment.

New user commands are added periodically; see the end of this page for instructions on installing updates. For additional information on user commands, see the [<span class='fa-file-pdf'>:fontawesome-solid-file-pdf:</span> _User Commands User Guide_](http://docs.dyalog.com/latest/User Commands User Guide.pdf).

User commands are invoked in an APL Session by starting an input line with a ] character. For example, the ]Boxing user command enables "boxed" output (and can be used to change other details of the way output is formatted):

```
      ]Boxing on
Was OFF
      'Hello' (1 2 3)
┌→────┬─────┐
│Hello│1 2 3│
└────→┴~───→┘
```

For a summary of the user command syntax, enter ]Help (Dyalog version 16.0 and earlier) or ] (version 17.0 and later).

For a list of the user commands available in your Session, enter ]?.

For example, with Dyalog version 16.0 (in July 2017):

```
      ]?
83 commands:                                                                                                                                                                                                               
 ARRAY         Compare  Edit                                                                                  
 CALC          Factors  FromHex  PivotTable  ToHex                                                            
 EXPERIMENTAL  DBuild  DTest                                                                                  
 FILE          CD  Collect  Compare  Edit  Find  Replace  Split  ToLarge  ToQuadTS  Touch                     
 FN            Align  Calls  Compare  Defs  DInput  Latest  ReorderLocals                                     
 MSWIN         Assemblies  Caption  CopyReg  FileAssociations  GUIProps  KeyPress  Open  ToHTML               
 NS            ScriptUpdate  Summary  Xref                                                                    
 OUTPUT        Box  Boxing  Disp  Display  Find  Format  Layout  Rows                                         
 PERFORMANCE   Profile  RunTime  SpaceNeeded                                                                  
 SALT          Clean  Compare  List  Load  Refresh  RemoveVersions  Save  Settings  Snap                      
 SPICE         UUpdate                                                                                        
 TOOLS         ADoc  Calendar  Chart  Demo  Version                                                           
 TRANSFER      In  Out                                                                                        
 UCMD          UDebug  ULoad  UMonitor  UNew  UReset  USetup                                                  
 WS            Check  Compare  Document  FindRefs  FnsLike  Locate  Map  NamesLike  Nms
               ObsLike  Peek  SizeOf  VarsLike
```

## Updates to Dyalog-supplied User Commands and to SALT

User commands and SALT are continually improved. So that users can benefit from fixes, zip files are uploaded from time to time containing the latest complete set of SALT and Dyalog-supplied user command files. To update SALT and the Dyalog-supplied user commands in your installation, follow the instructions below.:

1. Identify the **[DYALOG]** installation directory by entering the following in a Dyalog Session:
    
          ⎕←2 ⎕NQ'.' 'GetEnvironment' 'DYALOG'
    
2. Download the appropriate **.zip** file from the table below.
3. On Microsoft Windows:
    - Extract the contents of the **.zip** file to a temporary directory.
    - Copy the newly-extracted SALT directory (with its files and subdirectores) to the **[DYALOG]** installation directory. If prompted you need to overwrite/replace existing files and directories.  
        This might need administrator privileges.
4. On all other operating systems:
    - In a terminal window, with root permissions:
        - Change directory to the **[DYALOG]** installation directory.
        - Unzip the downloaded **.zip** file.
5. In a Dyalog session, run ]UReset user command to ensure that that all cached user command-related information has been updated.

|APL Version|Date of Latest Update|Download Links|
|---|---|---|
|14.0, 14.1 and 15.0|2017-08-22|[![](https://www.dyalog.com/uploads/images/General/zip_24.png)](https://www.dyalog.com/uploads/files/salt/salt_140-150.zip)|
|16.0|2018-04-23|[![](https://www.dyalog.com/uploads/images/General/zip_24.png)](https://www.dyalog.com/uploads/files/salt/salt_160.zip)|
|17.0|2021-06-21|[![](https://www.dyalog.com/uploads/images/General/zip_24.png)](https://www.dyalog.com/uploads/files/salt/salt_170.zip)|
|17.1 and 18.0|2021-11-03|[![](https://www.dyalog.com/uploads/images/General/zip_24.png)](https://www.dyalog.com/uploads/files/salt/salt_171-180.zip)|
|18.2|2022-03-10|[![](https://www.dyalog.com/uploads/images/General/zip_24.png)](https://www.dyalog.com/uploads/files/salt/salt_182.zip)|

For earlier versions of Dyalog, please contact [support@dyalog.com](mailto:support@dyalog.com).