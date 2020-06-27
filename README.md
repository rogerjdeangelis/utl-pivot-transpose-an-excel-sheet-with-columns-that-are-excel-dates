# utl-pivot-transpose-an-excel-sheet-with-columns-that-are-excel-dates
Pivot-transpose-an-excel-sheet-with-columns-that-are-excel-dates 
    Pivot-transpose-an-excel-sheet-with-columns-that-are-excel-dates                                                                 
                                                                                                                                     
    No need for 'proc import'                                                                                                        
                                                                                                                                     
    I could not figure out how to use the ops input(sheet1) to get the output.                                                       
    So a solved a related problem. Maybe this will help                                                                              
                                                                                                                                     
    You could probably pivot this easily in excel?                                                                                   
                                                                                                                                     
        Method                                                                                                                       
          1. input is sheet1 in d:/xls/have.xls                                                                                      
                                                                                                                                     
          2. In order to get text column names like 'Jan-90' you need to spcify                                                      
             validvarname=any and scan_text=no                                                                                       
                                                                                                                                     
             options validvarname=any;                                                                                               
             libname xel "d:/xls/have.xlsx" scan_text=no;                                                                            
                                                                                                                                     
          3.  The libname engine is limited to 255 excel columns so merge.                                                           
              Sheet has 361 columns. Split the sheet columns.                                                                        
                                                                                                                                     
              merge xel.'sheet1$a1:gg25'n  xel.'sheet1$gh1:mw25'n;                                                                   
                                                                                                                                     
          4.  Transpose and output an excel sheet                                                                                    
                                                                                                                                     
                                                                                                                                     
    github                                                                                                                           
    https://tinyurl.com/ycmkug8k                                                                                                     
    https://github.com/rogerjdeangelis/utl-pivot-transpose-an-excel-sheet-with-columns-that-are-excel-dates                          
                                                                                                                                     
    have workbook                                                                                                                    
    https://tinyurl.com/ycc4whjx                                                                                                     
    https://github.com/rogerjdeangelis/utl-pivot-transpose-an-excel-sheet-with-columns-that-are-excel-dates/blob/master/have.xlsx    
                                                                                                                                     
    wnt workbbok                                                                                                                     
    https://tinyurl.com/ycrlyhyh                                                                                                     
    https://github.com/rogerjdeangelis/utl-pivot-transpose-an-excel-sheet-with-columns-that-are-excel-dates/blob/master/want.xlsx    
                                                                                                                                     
    SAS Forum                                                                                                                        
    https://tinyurl.com/ybvvkxjg                                                                                                     
    https://communities.sas.com/t5/SAS-Data-Management/Convert-an-excel-data-table-into-SAS-format/m-p/665492                        
                                                                                                                                     
                                                                                                                                     
    d:/xls/have.xlsx   (361 columns)                                                                                                 
                                                                                                                                     
    ---------------------------------------- .. -----------------------                                                              
    |Date  Jan-90 Feb- Mar-90 Apr-90 May-90|         Nov-11     Dec-11|                                                              
    |--------------------------------------- .. ----------------------|                                                              
    |F1   |      |     |     |      |      |    |         .|         .|                                                              
    |-----+------+-----+-----+------+------+    +----------+----------|                                                              
    |F2   |      |     |     |      |      |    |         .|         .|                                                              
    |-----+------+-----+-----+------+------+    +----------+----------|                                                              
    |F3   |      |     |     |      |      |    |         .|         .|                                                              
    |-----+------+-----+-----+------+------+    +----------+----------|                                                              
    |F4   |      |     |     |      |      |    |         .|         .|                                                              
    |-----+------+-----+-----+------+------+    +----------+----------|                                                              
    |F5   |      |     |     |      |      |    |         .|         .|                                                              
    |-----+------+-----+-----+------+------+    +----------+----------|                                                              
    |F6   |      |     |     |      |      |    |         .|         .|                                                              
    |-----+------+-----+-----+------+------+    +----------+----------|                                                              
    |F7   |      |     |     |      |      |    |      -0.3|      3.18|                                                              
    |-----+------+-----+-----+------+------+    +----------+----------|                                                              
    |F8   |      |     |     |      |      |    |      3.54|      3.84|                                                              
    |-----+------+-----+-----+------+------+    +----------+----------|                                                              
    |F9   | -8.42| 2.16| 1.2 | -5.54| 11.12| .. |      2.62|      6.58|                                                              
    |-----+------+-----+-----+------+------+    +----------+----------|                                                              
                                                                                                                                     
     [sheet1]                                                                                                                        
                                                                                                                                     
    /*           _               _                                                                                                   
      ___  _   _| |_ _ __  _   _| |_                                                                                                 
     / _ \| | | | __| `_ \| | | | __|                                                                                                
    | (_) | |_| | |_| |_) | |_| | |_                                                                                                 
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                                
                    |_|_                                                                                                             
      _____  _____ ___| |                                                                                                            
     / _ \ \/ / __/ _ \ |                                                                                                            
    |  __/>  < (_|  __/ |                                                                                                            
     \___/_/\_\___\___|_|                                                                                                            
                                                                                                                                     
    */                                                                                                                               
                                                                                                                                     
     d:/xls/want.xlsx  (sample output)                                                                                               
                                                                                                                                     
     -----------------------                                                                                                         
     |     month_          |                                                                                                         
     |Date year    value   |                                                                                                         
     |---------------------|                                                                                                         
     |F9 | Jan-90| -8.42   |                                                                                                         
     |---+-------+---------|                                                                                                         
     |F9 | Feb-90| 2.16    |                                                                                                         
     |---+-------+---------|                                                                                                         
     |F9 | Apr-90| -5.54   |                                                                                                         
     |---+-------+---------|                                                                                                         
     |F9 | May-90| 11.12   |                                                                                                         
     |---+-------+---------|                                                                                                         
     |F9 | Jun-90| -2.55   |                                                                                                         
     |---+-------+---------|                                                                                                         
     |F9 | Jul-90| -3.66   |                                                                                                         
     |---+-------+---------|                                                                                                         
     |F9 | Aug-90| -11.39  |                                                                                                         
     |---+-------+---------|                                                                                                         
     |F9 | Sep-90| -7.54   |                                                                                                         
     |---+-------+---------|                                                                                                         
     |F9 | Oct-90| -3.35   |                                                                                                         
     |---+-------+---------|                                                                                                         
     |F9 | Nov-90| 8.41    |                                                                                                         
     |---+-------+---------|                                                                                                         
     |F9 | Feb-91| 6.65    |                                                                                                         
     |---+-------+---------|                                                                                                         
     |F9 | Mar-91| 0.76    |                                                                                                         
     |---+-------+---------|                                                                                                         
     |F9 | Apr-91| -0.9    |                                                                                                         
     |---+-------+---------|                                                                                                         
     |F9 | Jun-91| -7.91   |                                                                                                         
     |---+-------+---------|                                                                                                         
     |F9 | Jul-91| 5.57    |                                                                                                         
     -----------------------                                                                                                         
                                                                                                                                     
    /*                                                                                                                               
     ___  __ _ ___                                                                                                                   
    / __|/ _` / __|                                                                                                                  
    \__ \ (_| \__ \                                                                                                                  
    |___/\__,_|___/                                                                                                                  
                                                                                                                                     
    */                                                                                                                               
                                                                                                                                     
     WORK.WANT_SAS total obs=221                                                                                                     
                                                                                                                                     
                   month_                                                                                                            
      Date     year       value                                                                                                      
                                                                                                                                     
       F9     01JAN90     -8.42                                                                                                      
       F9     01FEB90      2.16                                                                                                      
       F9     01MAR90      1.20                                                                                                      
       F9     01APR90     -5.54                                                                                                      
       F9     01MAY90     11.12                                                                                                      
       F9     01JUN90     -2.55                                                                                                      
       F9     01JUL90     -3.66                                                                                                      
       F9     01AUG90    -11.39                                                                                                      
       F9     01SEP90     -7.54                                                                                                      
       F9     01OCT90     -3.35                                                                                                      
       F9     01NOV90      8.41                                                                                                      
       F9     01DEC90      2.60                                                                                                      
                                                                                                                                     
                                                                                                                                     
     Variables in Creation Ord                                                                                                       
                                                                                                                                     
    #    Variable      Type    Len    Format                                                                                         
                                                                                                                                     
    1    Date          Char      3    $3.                                                                                            
    2    month_year    Num       8    DATE7.                                                                                         
    3    value         Num       8                                                                                                   
                                                                                                                                     
                                                                                                                                     
    /*                                                                                                                               
     _ __  _ __ ___   ___ ___  ___ ___                                                                                               
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|                                                                                              
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                                              
    | .__/|_|  \___/ \___\___||___/___/                                                                                              
    |_|                _               _               _                                                                             
      _____  _____ ___| |   ___  _   _| |_ _ __  _   _| |_                                                                           
     / _ \ \/ / __/ _ \ |  / _ \| | | | __| `_ \| | | | __|                                                                          
    |  __/>  < (_|  __/ | | (_) | |_| | |_| |_) | |_| | |_                                                                           
     \___/_/\_\___\___|_|  \___/ \__,_|\__| .__/ \__,_|\__|                                                                          
                                          |_|                                                                                        
    */                                                                                                                               
                                                                                                                                     
    * if output workbook exist then delete it;                                                                                       
    %utlfkil(d:/xls/want.xlsx);                                                                                                      
                                                                                                                                     
    * use date column names as then appear in excel;                                                                                 
    options validvarname=any;                                                                                                        
                                                                                                                                     
    libname xel "d:/xls/have.xlsx" scan_text=no;                                                                                     
                                                                                                                                     
    data havDte;                                                                                                                     
      * libname is limited to 255 columns so split and merge;                                                                        
      merge xel.'sheet1$a1:gg25'n  xel.'sheet1$gh1:mw25'n;                                                                           
    run;quit;                                                                                                                        
                                                                                                                                     
    libname xel clear;                                                                                                               
                                                                                                                                     
                                                                                                                                     
    libname xel "d:/xls/want.xlsx";                                                                                                  
                                                                                                                                     
    * simple transpose;                                                                                                              
    proc transpose data=havDte out=xel.want(where=(value not =: "F")                                                                 
                 rename=(col1=value _name_=Month_year) drop=_label_);                                                                
    by date notsorted;                                                                                                               
    var date -- 'Dec-19'n;                                                                                                           
    run;quit;                                                                                                                        
                                                                                                                                     
    libname xel clear;                                                                                                               
                                                                                                                                     
    /*               _        _     _                                                                                                
     ___  __ _ ___  | |_ __ _| |__ | | ___                                                                                           
    / __|/ _` / __| | __/ _` | `_ \| |/ _ \                                                                                          
    \__ \ (_| \__ \ | || (_| | |_) | |  __/                                                                                          
    |___/\__,_|___/  \__\__,_|_.__/|_|\___|                                                                                          
                                                                                                                                     
    */                                                                                                                               
                                                                                                                                     
    If you want a SAS dataset I suggest you do the following;                                                                        
                                                                                                                                     
                                                                                                                                     
    libname xel "d:/xls/want.xlsx";                                                                                                  
                                                                                                                                     
    proc sql dquote=ansi;                                                                                                            
      create                                                                                                                         
          table want_sas (where=(value ne .)) as                                                                                     
      select  /* convert to SAS date */                                                                                              
         date                                                                                                                        
        ,input(compress('01-'!!month_year,'-'),date7.) as month_year format=date7.                                                   
        ,input(value,best.)                            as value                                                                      
      from                                                                                                                           
         xel.want                                                                                                                    
    ;quit;                                                                                                                           
                                                                                                                                     
    libname xel clear;                                                                                                               
                                                                                                                                     
                                                                                                                                     
                                                                                                                                     
