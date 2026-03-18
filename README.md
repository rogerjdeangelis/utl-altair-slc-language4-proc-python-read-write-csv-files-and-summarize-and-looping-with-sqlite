    %let pgm=utl-altair-slc-language4-proc-python-read-write-text-files-and-summarize-and-looping-with-sqlite;

    %stop_submission;

    Altair slc language4 proc python read write text files and summarize and looping with sqlite

    Too long to post on a list, see gethub
    https://github.com/rogerjdeangelis/utl-altair-slc-language4-proc-python-read-write-csv-files-and-summarize-and-looping-with-sqlite

    Note: Note sqlite has csv read and write commands, however I want to present general txt processing in sql.
          Keep in mind that I am demonstrating that the exact sqlite queries 9 languages below.
          In addition you use the exact same queries in any language or operating system that is odbc compliant.

    Too long to post on a list, see github


    related repos (see for information of installing odbc and sqlite)

    https://github.com/rogerjdeangelis/utl-altair-slc-sqlite-cheat-sheet
    https://github.com/rogerjdeangelis/utl-altair-slc-language1-drop-down-to-open-source-spss-and-execute-postgresql-query
    https://github.com/rogerjdeangelis/utl-altair-slc-language2-drop-down-to-open-source-matlab-and-execute-sqlite-with-extensions
    https://github.com/rogerjdeangelis/utl-altair-slc-language3-proc-r-read-write-csv-files-and-summarize-and-looping-with-sqlite
    https://github.com/rogerjdeangelis/utl-altair-slc-language4-proc-python-read-write-csv-files-and-summarize-and-looping-with-sqlite

    PROBLEM

      PROCESS

      1  slc create sqlite table 'have' with 5 lines (sentences) and column name line

         d:/sqlite/mysqlite.db table have
         
         line                        name        sex    age    height

        This is the 1st line        Alfred       M      14     69.0
        This is the 2nd line        Alice        F      13     56.5
        This is the 3rd line        Barbara      F      13     65.3
        This is the 4th line        Carol        F      14     62.8
        This is the 5th line        Henry        M      14     63.5

      2  python summarize sqlite table

         select sex avg(age) avg(height) from have group by sex


      3  python convert sqlite table 'have' to text file using sqlite 'writefile' command

         d:/txt/have.txt

         This is the 1st line
         This is the 2nd line
         This is the 3rd line

      4  python convert text file 'd:/txt/have.txt' to python dataframe using sqlite readfile

          text

          This is the 1st line
          This is the 2nd line
          This is the 3rd line

      5  python iterate(loop) over numbers 1-10 and output median (5.5)


    OBJECTIVE

      I am trying to make sql programmers expert programmers in
      9 languages using exactly the same sql queries.
      Use packages and procedures for analysis and sql for data wrangling and interfacing.

      Add very powerfull sql processing to the open source spss
      Posgresql has windows extensions.

      I hope to add repos with  drop downs to sql with windows extensions in many languages

     *language 1   open source spss
     *language 2   open source matlab
     *language 3   r
     *language 4   python
      language 5   altair odbc sqlite
      language 6   excel
      language 7   perl
      language 8   slc proc sql (the only solution that does not support windows extensions)
      language 9   powershell

    /*                   _
    (_)_ __  _ __  _   _| |_
    | | `_ \| `_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    */

    * best first;
    %utlfkil(d:/sqlite/mysqlite.db);

    libname workx sas7bdat "d:/wpswrkx"; /*---  put in autoexec ---*/

    proc datasets lib=workx kill;
    run;

    libname sqlite odbc noprompt="driver=sqlite3 odbc driver; database=d:/sqlite/mysqlite.db;LoadExt=d:/dll/sqlean.dll;";

    proc datasets lib=sqlite;
     delete have;
    run;

    options validvarname=v7;
    data sqlite.have;
      informat
        line    $24.
        name    $8.
        sex     $1.
        age     8.
        height  8.
        ;
     input name sex age height line &;
    cards4;
    Alfred M 14 69 This is the 1st line
    Alice F 13 56.5 This is the 2nd line
    Barbara F 13 65.3 This is the 3rd line
    Carol F 14 62.8 This is the 4th line
    Henry M 14 63.5 This is the 5th line
    ;;;;
    run;quit;

    proc contents data=sqlite.have;
    run;

    proc print data=sqlite.have;
    run;

    proc sql;
     SELECT sql FROM sqlite.sqlite_master WHERE name='have'
    ;quit;

    libname sqlite clear;

    /**************************************************************************************************************************/
    /* sqlite table have in database d:/sqlite/mysqlite.db                                                                    */
    /*                                                                                                                        */
    /* sqlite.have                                                                                                            */
    /*                                                                                                                        */
    /* line                        name        sex    age    height                                                           */
    /*                                                                                                                        */
    /* This is the 1st line        Alfred       M      14     69.0                                                            */
    /* This is the 2nd line        Alice        F      13     56.5                                                            */
    /* This is the 3rd line        Barbara      F      13     65.3                                                            */
    /* This is the 4th line        Carol        F      14     62.8                                                            */
    /* This is the 5th line        Henry        M      14     63.5                                                            */
    /*                                                                                                                        */
    /* sqlite table have contents                                                                                             */
    /*                                                                                                                        */
    /* CREATE TABLE have( line VARCHAR(24), name VARCHAR(8), sex VARCHAR(1), age DOUBLE PRECISION, height DOUBLE PRECISION )  */
    /*                                                                                                                        */
    /* Altair SLC                                                                                                             */
    /*                                                                                                                        */
    /* The CONTENTS Procedure                                                                                                 */
    /*                                                                                                                        */
    /* Data Set Name           HAVE                                                                                           */
    /* Member Type             VIEW                                                                                           */
    /* Engine                                                                                                                 */
    /* Observations            .                                                                                              */
    /* Variables               5                                                                                              */
    /* Indexes                 0                                                                                              */
    /* Observation Length      49                                                                                             */
    /* Deleted Observations    0                                                                                              */
    /* Data Set Type                                                                                                          */
    /* Label                                                                                                                  */
    /* Compressed              NO                                                                                             */
    /* Sorted                  NO                                                                                             */
    /* Data Representation                                                                                                    */
    /* Encoding                wlatin1 Windows-1252 Western                                                                   */
    /*                                                                                                                        */
    /*       Alphabetic List of Variables and Attributes                                                                      */
    /*                                                                                                                        */
    /* Number    Variable    Type  Len   Pos    Format Informat                                                               */
    /* ________________________________________________________                                                               */
    /*      4    age         Num     8    33                                                                                  */
    /*      5    height      Num     8    41                                                                                  */
    /*      1    line        Char   24     0    $24.   $24.                                                                   */
    /*      2    name        Char    8    24    $8.    $8.                                                                    */
    /*      3    sex         Char    1    32    $1.    $1.                                                                    */
    /**************************************************************************************************************************/

    /*                   _     _
    (_)_ __  _ __  _   _| |_  | | ___   __ _
    | | `_ \| `_ \| | | | __| | |/ _ \ / _` |
    | | | | | |_) | |_| | |_  | | (_) | (_| |
    |_|_| |_| .__/ \__,_|\__| |_|\___/ \__, |
            |_|                        |___/
    */

    1                                          Altair SLC         13:59 Tuesday, March 17, 2026

    NOTE: Copyright 2002-2025 World Programming, an Altair Company
    NOTE: Altair SLC 2026 (05.26.01.00.000758)
          Licensed to Roger DeAngelis
    NOTE: This session is executing on the X64_WIN11PRO platform and is running in 64 bit mode

    NOTE: AUTOEXEC processing beginning; file is C:\wpsoto\autoexec.sas
    NOTE: AUTOEXEC source line
    1       +  ï»¿ods _all_ close;
               ^
    ERROR: Expected a statement keyword : found "?"
    NOTE: AUTOEXEC processing completed

    Altair SLC

    The DATASETS Procedure

             Directory

    Libref           WORKX
    Engine           SAS7BDAT
    Physical Name    d:\wpswrkx

                                     Members

                                Member
      Number    Member Name     Type         File Size      Date Last Modified

    --------------------------------------------------------------------------

           1    AVGS            DATA              5120      17MAR2026:13:49:18
           2    LINES           DATA              5120      17MAR2026:13:49:18
           3    MEDIAN_VALUE    DATA              5120      17MAR2026:13:49:18
    1         proc datasets lib=workx kill;
    2         run;quit;

    NOTE: Deleting WORKX.avgs (type=DATA)
    NOTE: Deleting WORKX.lines (type=DATA)
    NOTE: Deleting WORKX.median_value (type=DATA)
    NOTE: Procedure datasets step took :

          real time : 0.045
          cpu time  : 0.031


    3
    4         %utlfkil(d:/txt/class_export.txt);
    5
    6         options set=PYTHONHOME "D:\py314";
    7
    8         proc python;
    9         submit;
    10        import sqlite3
    11        import pandas as pd
    12        from pandasql import sqldf
    13
    14        # Connect directly to your SQLite database file
    15        conn = sqlite3.connect('d:/sqlite/mysqlite.db')
    16        conn.enable_load_extension(True)
    17        conn.load_extension('d:/dll/sqlean.dll')
    18
    19        # Read data from SQLite into pandas DataFrame
    20        avgs = pd.read_sql_query("""
    21            select
    22               sex,
    23               count(*) as count,
    24               round(avg(age),1)    as avg_age,
    25               round(avg(height),1) as avg_height
    26            from
    27               have
    28            group
    29               by sex
    30            """,conn)
    31        print(avgs)
    32
    33        conn.execute("""
    34            SELECT writefile(
    35                'd:/txt/class_export.txt',
    36                (
    37                    SELECT group_concat(line, char(10))
    38                    FROM have
    39                )
    40            )
    41        """)
    42
    43        lines = pd.read_sql_query("""
    44            SELECT value AS lines
    45            FROM json_each('["' || replace(readfile('d:/txt/class_export.txt'), char(10), '","') || '"]')
    46        """, conn)
    47        print(lines)
    48
    49        median_value = pd.read_sql_query("""
    50          WITH RECURSIVE nums(x) AS (
    51            SELECT 1
    52            UNION ALL
    53            SELECT x + 1 FROM nums WHERE x < 10
    54          ),
    55          med AS (
    56            SELECT
    57              x,
    58              ROW_NUMBER() OVER (ORDER BY x) AS r,
    59              COUNT(*) OVER () AS c
    60            FROM nums
    61          )
    62          SELECT AVG(x) AS median
    63          FROM med
    64          WHERE r IN ((c+1)/2, (c+2)/2)
    65        """,conn)
    66
    67        print(median_value);
    68        endsubmit;

    NOTE: Submitting statements to Python:


    69        import python=avgs data=workx.avgs;
    NOTE: Creating data set 'WORKX.avgs' from Python data frame 'avgs'
    NOTE: Data set "WORKX.avgs" has 2 observation(s) and 4 variable(s)

    70        import python=lines data=workx.lines;
    NOTE: Creating data set 'WORKX.lines' from Python data frame 'lines'
    NOTE: Data set "WORKX.lines" has 5 observation(s) and 1 variable(s)

    71        import python=median_value data=workx.median_value;
    NOTE: Creating data set 'WORKX.median_value' from Python data frame 'median_value'
    NOTE: Data set "WORKX.median_value" has 1 observation(s) and 1 variable(s)

    72        run;
    NOTE: Procedure python step took :
          real time : 1.242
          cpu time  : 0.078


    73
    74
    75
    ERROR: Error printed on page 1

    NOTE: Submitted statements took :
          real time : 1.385
          cpu time  : 0.171

    /*
     _ __  _ __ ___   ___ ___  ___ ___
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|
    | |_) | | | (_) | (_|  __/\__ \__ \
    | .__/|_|  \___/ \___\___||___/___/
    |_|
    */

    proc datasets lib=workx kill;
    run;quit;

    %utlfkil(d:/txt/class_export.txt);

    options set=PYTHONHOME "D:\py314";

    proc python;
    submit;
    import sqlite3
    import pandas as pd
    from pandasql import sqldf

    # Connect directly to your SQLite database file
    conn = sqlite3.connect('d:/sqlite/mysqlite.db')
    conn.enable_load_extension(True)
    conn.load_extension('d:/dll/sqlean.dll')

    # Read data from SQLite into pandas DataFrame
    avgs = pd.read_sql_query("""
        select
           sex,
           count(*) as count,
           round(avg(age),1)    as avg_age,
           round(avg(height),1) as avg_height
        from
           have
        group
           by sex
        """,conn)
    print(avgs)

    conn.execute("""
        SELECT writefile(
            'd:/txt/class_export.txt',
            (
                SELECT group_concat(line, char(10))
                FROM have
            )
        )
    """)

    lines = pd.read_sql_query("""
        SELECT value AS lines
        FROM json_each('["' || replace(readfile('d:/txt/class_export.txt'), char(10), '","') || '"]')
    """, conn)
    print(lines)

    median_value = pd.read_sql_query("""
      WITH RECURSIVE nums(x) AS (
        SELECT 1
        UNION ALL
        SELECT x + 1 FROM nums WHERE x < 10
      ),
      med AS (
        SELECT
          x,
          ROW_NUMBER() OVER (ORDER BY x) AS r,
          COUNT(*) OVER () AS c
        FROM nums
      )
      SELECT AVG(x) AS median
      FROM med
      WHERE r IN ((c+1)/2, (c+2)/2)
    """,conn)

    print(median_value);
    endsubmit;
    import python=avgs data=workx.avgs;
    import python=lines data=workx.lines;
    import python=median_value data=workx.median_value;
    run;

    /**************************************************************************************************************************/
    /* SUMMARIZE                                                                                                              */
    /* ---------                                                                                                              */
    /* WORKX.AVGS total obs=2                                                                                                 */
    /*                                    AVG_                                                                                */
    /* Obs    SEX    COUNT    AVG_AGE    HEIGHT                                                                               */
    /*                                                                                                                        */
    /*  1      F       3        13.3      61.5                                                                                */
    /*  2      M       2        14.0      66.3                                                                                */
    /*                                                                                                                        */
    /*                                                                                                                        */
    /* CREATE TEXT FILE                                                                                                       */
    /* ----------------                                                                                                       */
    /*  d:/txt/class_export.txt                                                                                               */
    /*                                                                                                                        */
    /*  This is the 1st line                                                                                                  */
    /*  This is the 2nd line                                                                                                  */
    /*  This is the 3rd line                                                                                                  */
    /*  This is the 4th line                                                                                                  */
    /*  This is the 5th line                                                                                                  */
    /*                                                                                                                        */
    /*                                                                                                                        */
    /* CONVERT TEXT FILE TO PANDA DATAFRAME                                                                                   */
    /* -----------------------------------                                                                                    */
    /*  WORKX.LINES total obs=5                                                                                               */
    /*                                                                                                                        */
    /*                     txt                                                                                                */
    /*  0 This is the 1st line                                                                                                */
    /*  1 This is the 2nd line                                                                                                */
    /*  2 This is the 3rd line                                                                                                */
    /*  3 This is the 4th line                                                                                                */
    /*  4 This is the 5th line                                                                                                */
    /*                                                                                                                        */
    /*AUTOCREATE NUMBERS 1-10 and cmpute median                                                                               */
    /*-----------------------------------------                                                                               */
    /* WORKX.MEDIAN_VALUE total obs=1 17MAR2026:13:53:59                                                                      */
    /*                                                                                                                        */
    /* Obs    MEDIAN                                                                                                          */
    /*                                                                                                                        */
    /*  1       5.5                                                                                                           */
    /**************************************************************************************************************************/

    /*                                   _
     _ __  _ __ ___   ___ ___  ___ ___  | | ___   __ _
    | `_ \| `__/ _ \ / __/ _ \/ __/ __| | |/ _ \ / _` |
    | |_) | | | (_) | (_|  __/\__ \__ \ | | (_) | (_| |
    | .__/|_|  \___/ \___\___||___/___/ |_|\___/ \__, |
    |_|                                          |___/
    */

    1                                          Altair SLC         14:03 Tuesday, March 17, 2026

    NOTE: Copyright 2002-2025 World Programming, an Altair Company
    NOTE: Altair SLC 2026 (05.26.01.00.000758)
          Licensed to Roger DeAngelis
    NOTE: This session is executing on the X64_WIN11PRO platform and is running in 64 bit mode

    NOTE: AUTOEXEC processing beginning; file is C:\wpsoto\autoexec.sas
    NOTE: AUTOEXEC source line
    1       +  ï»¿ods _all_ close;
               ^
    ERROR: Expected a statement keyword : found "?"

    NOTE: AUTOEXEC processing completed


    Altair SLC

    The DATASETS Procedure

             Directory

    Libref           WORKX
    Engine           SAS7BDAT
    Physical Name    d:\wpswrkx
    1         proc datasets lib=workx kill;
    NOTE: No matching members in directory
    2         run;quit;
    NOTE: Procedure datasets step took :
          real time : 0.013
          cpu time  : 0.000


    3
    4         %utlfkil(d:/txt/class_export.txt);
    5
    6         options set=PYTHONHOME "D:\py314";
    7
    8         proc python;
    9         submit;
    10        import sqlite3
    11        import pandas as pd
    12        from pandasql import sqldf
    13
    14        # Connect directly to your SQLite database file
    15        conn = sqlite3.connect('d:/sqlite/mysqlite.db')
    16        conn.enable_load_extension(True)
    17        conn.load_extension('d:/dll/sqlean.dll')
    18
    19        # Read data from SQLite into pandas DataFrame
    20        avgs = pd.read_sql_query("""
    21            select
    22               sex,
    23               count(*) as count,
    24               round(avg(age),1)    as avg_age,
    25               round(avg(height),1) as avg_height
    26            from
    27               have
    28            group
    29               by sex
    30            """,conn)
    31        print(avgs)
    32
    33        conn.execute("""
    34            SELECT writefile(
    35                'd:/txt/class_export.txt',
    36                (
    37                    SELECT group_concat(line, char(10))
    38                    FROM have
    39                )
    40            )
    41        """)
    42
    43        lines = pd.read_sql_query("""
    44            SELECT value AS lines
    45            FROM json_each('["' || replace(readfile('d:/txt/class_export.txt'), char(10), '","') || '"]')
    46        """, conn)
    47        print(lines)
    48
    49        median_value = pd.read_sql_query("""
    50          WITH RECURSIVE nums(x) AS (
    51            SELECT 1
    52            UNION ALL
    53            SELECT x + 1 FROM nums WHERE x < 10
    54          ),
    55          med AS (
    56            SELECT
    57              x,
    58              ROW_NUMBER() OVER (ORDER BY x) AS r,
    59              COUNT(*) OVER () AS c
    60            FROM nums
    61          )
    62          SELECT AVG(x) AS median
    63          FROM med
    64          WHERE r IN ((c+1)/2, (c+2)/2)
    65        """,conn)
    66
    67        print(median_value);
    68        endsubmit;

    NOTE: Submitting statements to Python:


    69        import python=avgs data=workx.avgs;
    NOTE: Creating data set 'WORKX.avgs' from Python data frame 'avgs'
    NOTE: Data set "WORKX.avgs" has 2 observation(s) and 4 variable(s)

    70        import python=lines data=workx.lines;
    NOTE: Creating data set 'WORKX.lines' from Python data frame 'lines'
    NOTE: Data set "WORKX.lines" has 5 observation(s) and 1 variable(s)

    71        import python=median_value data=workx.median_value;
    NOTE: Creating data set 'WORKX.median_value' from Python data frame 'median_value'
    NOTE: Data set "WORKX.median_value" has 1 observation(s) and 1 variable(s)

    72        run;
    NOTE: Procedure python step took :
          real time : 1.277
          cpu time  : 0.062


    73
    ERROR: Error printed on page 1

    NOTE: Submitted statements took :
          real time : 1.393
          cpu time  : 0.156

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
