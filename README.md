# CBT336
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. GitHub repos will be deleted and created during this period...

```
//***FILE 336 CONTAINS A COLLECTION OF UTILITIES,  MACROS,  TSO     *   FILE 336
//*           COMMANDS,  USERMODS,  AND OTHER STUFF FROM RICE       *   FILE 336
//*           UNIVERSITY.                                           *   FILE 336
//*                                                                 *   FILE 336
//*          RICE UNIVERSITY RUNS MVS/SP 1.1.1 WITH BASE-LEVEL      *   FILE 336
//*          JES2 (EJE1102),  AND ALL OF THIS IS WORKING AT THAT    *   FILE 336
//*          LEVEL.  (WE ALSO RUN UICC'S JTIP AND ACF2, WHICH ARE   *   FILE 336
//*          OCCASIONALLY REFERENCED.  WE THINK WE HAVE REMOVED     *   FILE 336
//*          ALL SERIOUS DEPENDENCIES ON THESE PRODUCTS.)  SOME     *   FILE 336
//*          OF THIS IS UPDATED/CORRECTED VERSIONS OF STUFF WE      *   FILE 336
//*          ORIGINALLY GOT FROM THE 1-23-82 VERSION OF THE MODS    *   FILE 336
//*          TAPE.  THEREFORE SOME OF IT MAY HAVE BEEN SUPERSEDED   *   FILE 336
//*          OR COMPLICATED BY OTHER CHANGES TO THE SAME PROGRAMS   *   FILE 336
//*          SINCE THEN.                                            *   FILE 336
//*                                                                 *   FILE 336
//*          THIS COLLECTION INCLUDES:                              *   FILE 336
//*                                                                 *   FILE 336
//*               TAPESCAN,  A TAPE SCANNING/COPYING UTILITY        *   FILE 336
//*               ESPECIALLY SUITED TO DIAGNOSIS OF OVER-WRITTEN    *   FILE 336
//*               OR OTHERWISE SCREWED-UP TAPES.  THIS VERSION OF   *   FILE 336
//*               TAPESCAN INCLUDES EXTENSIVE SUPPORT FOR           *   FILE 336
//*               ANSI-LABELLED TAPES, AND A LOT OF SECURITY        *   FILE 336
//*               SUPPORT (INCLUDING PASSWORD, EXPIRATION DATE      *   FILE 336
//*               AND ACF2 SECURITY CHECKING).                      *   FILE 336
//*                                                                 *   FILE 336
//*               DISKUTIL,  AN IEHPROGM REPLACEMENT.               *   FILE 336
//*                                                                 *   FILE 336
//*               SEQCOPY,  AN IEBGENER REPLACEMENT.                *   FILE 336
//*                                                                 *   FILE 336
//*               PRINTPDS,  A UTILITY TO PRINT ALL MEMBERS         *   FILE 336
//*               OF A PDS, NO MATTER WHAT RECORD FORMAT.  IT       *   FILE 336
//*               PRODUCES A TABLE OF CONTENTS AND AN ALIAS         *   FILE 336
//*               CROSS-REFERENCE.                                  *   FILE 336
//*                                                                 *   FILE 336
//*               MAPDISK,  ANOTHER VTOC MAPPING UTILITY            *   FILE 336
//*               (UNRELATED TO OTHERS OF THE SAME NAME).           *   FILE 336
//*                                                                 *   FILE 336
//*               A VERSION OF DYNAMIC MLPA (OR MODREP)  WITH       *   FILE 336
//*               SOME HORRIBLE BUGS FIXED.  (NOW WE KNOW WHY       *   FILE 336
//*               IT STOPPED WORKING WHEN WE INSTALLED              *   FILE 336
//*               LOW-MEMORY PROTECTION!)                           *   FILE 336
//*                                                                 *   FILE 336
//*               CLUTSPAR,  A FRIENDLIER VERSION OF IKJPARS.       *   FILE 336
//*               TRY IT, AND YOU WON'T WANT TO GO BACK!  NOTE      *   FILE 336
//*               THAT CLUTSPAR DOES NOT SUPPORT ANY TSO/E          *   FILE 336
//*               FEATURES SUCH AS THE PARSE INTERFACE TO THE       *   FILE 336
//*               HELP COMMAND, DUE TO LACK OF INFORMATION ON       *   FILE 336
//*               HOW THEY WORK.  (CLUTSPAR IS A FRAGMENT OF A      *   FILE 336
//*               PROJECT CALLED TSU, WHICH STARTED OUT AS A        *   FILE 336
//*               MECHANISM FOR WRITING TSO COMMAND PROCESSORS      *   FILE 336
//*               IN PL/I, AND EVENTUALLY SPROUTED REPLACEMENTS     *   FILE 336
//*               FOR MAJOR PORTIONS OF TSO.  TSU AS A WHOLE HAS    *   FILE 336
//*               NEVER QUITE BECOME CLEAN ENOUGH TO RELEASE,       *   FILE 336
//*               BUT CLUTSPAR IS SUCH AN ENORMOUS IMPROVEMENT      *   FILE 336
//*               OVER THE COMPETITION THAT WE DECIDED TO MAKE      *   FILE 336
//*               IT AN EXCEPTION.)                                 *   FILE 336
//*                                                                 *   FILE 336
//*               THE LANGUAGE INDEPENDENT ENVIRONMENT (LIE),       *   FILE 336
//*               A SET OF MACROS AND ROUTINES TO LET YOU WRITE     *   FILE 336
//*               ASSEMBLER SUBROUTINES WHICH CAN TAKE ADVANTAGE    *   FILE 336
//*               OF SERVICES OF THE PL/I ENVIRONMENT, PLUS A       *   FILE 336
//*               PSEUDO-PL/I ENVIRONMENT MANUFACTURER, TO          *   FILE 336
//*               PROVIDE THE SAME SERVICES IN THE ABSENCE OF       *   FILE 336
//*               PL/I.  CLUTSPAR IS A PSEUDO-PL/I APPLICATION      *   FILE 336
//*               IN THIS SENSE.                                    *   FILE 336
//*                                                                 *   FILE 336
//*               THE XSEND TSO COMMAND,  FOR IMPROVED              *   FILE 336
//*               COMMUNICATION WITH LOGGED-ON TSO USERS.  NOW      *   FILE 336
//*               YOU CAN SEND WITH WAIT AND BREAK OUT OF IT IF     *   FILE 336
//*               YOU GET TIRED OF WAITING!  XSEND INCLUDES A       *   FILE 336
//*               USER SVC FOR CONTROLLED USE OF TPUT HIGHP (TO     *   FILE 336
//*               SEND BELLS/ALARM TO TELL A NOINTERCOM USER        *   FILE 336
//*               SOMEONE WANTS TO "SPEAK" TO HIM).                 *   FILE 336
//*                                                                 *   FILE 336
//*               LISTM,  A NICE TSO COMMAND TO LIST PDS MEMBER     *   FILE 336
//*               NAMES.                                            *   FILE 336
//*                                                                 *   FILE 336
//*               LISTU,  A NICE TSO COMMAND TO LIST TSO USERS      *   FILE 336
//*               (SORTED BY USERID).                               *   FILE 336
//*                                                                 *   FILE 336
//*               UPUT, UPROMPT AND UGET,  MACROS TO USE AS         *   FILE 336
//*               REPLACEMENTS FOR TPUT AND TGET THAT INTERFACE     *   FILE 336
//*               TO THE PUTLINE/PUTGET SERVICE ROUTINES.  THEY     *   FILE 336
//*               MAKE CONVERSION OF OLD TSO CODE SO IT WILL        *   FILE 336
//*               RUN UNDER A BATCH TMP MUCH EASIER.                *   FILE 336
//*                                                                 *   FILE 336
//*               XWTO,  A MACRO TO ALLOW WTO MESSAGES TO BE        *   FILE 336
//*               BUILT FROM SEGMENTS WITHOUT HAVING TO COMPUTE     *   FILE 336
//*               ALL THE OFFSETS.                                  *   FILE 336
//*                                                                 *   FILE 336
//*               UHB MACROS,  A SET OF UTILITY MACROS TO MAKE      *   FILE 336
//*               WRITING BIG MACRO APPLICATIONS (LIKE XWTO         *   FILE 336
//*               TURNED OUT TO BE) MUCH EASIER.                    *   FILE 336
//*                                                                 *   FILE 336
//*               A JULIAN ROUTINE (ORIGINALLY WRITTEN TO BE        *   FILE 336
//*               CALLED FROM COBOL) TO CONVERT DATES BETWEEN       *   FILE 336
//*               JULIAN AND GREGORIAN FORMAT, AND TO DETERMINE     *   FILE 336
//*               THE DAY OF THE WEEK.  THIS ROUTINE IS NOT ALL     *   FILE 336
//*               THAT INTERESTING, BUT IT IS USED BY SOME OF       *   FILE 336
//*               THE OTHER SUBMISSIONS.                            *   FILE 336
//*                                                                 *   FILE 336
//*               SAVEX AND RETURNX MACROS,  YET ANOTHER            *   FILE 336
//*               EXAMPLE OF AN EXTENDED SAVE AND RETURN.           *   FILE 336
//*               AGAIN, NOT THAT INTERESTING, BUT USED ALL         *   FILE 336
//*               OVER BY OUR OTHER CODE.                           *   FILE 336
//*                                                                 *   FILE 336
//*          THE ABOVE ARE (EXCEPT FOR THE XSEND SVC AND            *   FILE 336
//*          CLUTSPAR) ALL APPLICATIONS, AND REQUIRE NO SMP         *   FILE 336
//*          WORK.                                                  *   FILE 336
//*                                                                 *   FILE 336
//*          WE ARE ALSO PROVIDING SMP-PACKAGED SYSMODS TO          *   FILE 336
//*          SUPPORT:  PACKAGED SYSMODS TO SUPPORT:                 *   FILE 336
//*                                                                 *   FILE 336
//*               A MODIFICATION TO THE JES2 $DF COMMAND TO         *   FILE 336
//*               ALLOW SELECTIONS OF THE TYPES OF DATA SETS        *   FILE 336
//*               TO BE DISPLAYED.  THIS MOD ALSO INTRODUCES        *   FILE 336
//*               THE $XF COMMAND, WHICH DISPLAYS EACH JOB          *   FILE 336
//*               WITH OUTPUT OF THE SPECIFIED KIND.                *   FILE 336
//*                                                                 *   FILE 336
//*               A BIG MOD TO JES2 OUTPUT PROCESSING TO            *   FILE 336
//*               PROVIDE COUNTS OF THE ACTUAL NUMBER OF PAGES      *   FILE 336
//*               PRINTED FOR A JOB, BASED ON DEFINITIONS OF        *   FILE 336
//*               FORMS AND CARRIAGE TAPE LAYOUTS CONTAINED         *   FILE 336
//*               IN THE JES2 INITIALIZATION PARAMETERS.            *   FILE 336
//*                                                                 *   FILE 336
//*               A MOD TO TSO FUNCTIONAL ACCOUNTING (SMF TYPE      *   FILE 336
//*               32 RECORDS) TO RECORD RESPONSE-TIME-RELATED       *   FILE 336
//*               INFORMATION IN PLACE OF SOME OF THE MORE          *   FILE 336
//*               ESOTERIC PRESENT INFORMATION, AND TO NOT          *   FILE 336
//*               REQUIRE A PRE-ASSEMBLED LIST OF INTERESTING       *   FILE 336
//*               COMMANDS.  INCLUDED IS A REPORT PROGRAM TO        *   FILE 336
//*               SUMMARIZE THE RECORDS CONTAINED IN A BATCH        *   FILE 336
//*               OF SMF DATA.                                      *   FILE 336
//*                                                                 *   FILE 336
//*               A VERSION OF THE MOD TO ADD THE MAXIMUM           *   FILE 336
//*               CONDITION CODE TO THE JES2 NOTIFY MESSAGE.        *   FILE 336
//*                                                                 *   FILE 336
//*               A JES2 MOD TO DISPLAY THE CONVERTER ABEND         *   FILE 336
//*               CODE WHEN THE CONVERTER CRASHES.  (NOW WHO        *   FILE 336
//*               WOULD EVER WANT TO KNOW A THING LIKE THAT?)       *   FILE 336
//*                                                                 *   FILE 336
//*               A MOD TO REMOVE "CN(00)" FROM NOTIFY              *   FILE 336
//*               MESSAGES (AND ANYTHING ELSE SENT VIA              *   FILE 336
//*               INTERNAL SEND COMMANDS).                          *   FILE 336
//*                                                                 *   FILE 336
//*               A MOD TO STAMP A NEW FORMAT 1 DSCB WITH           *   FILE 336
//*               THE USERID OF ITS CREATOR (FROM THE SMF           *   FILE 336
//*               USERID FIELD).  WITH ACF2 (AND THE RIGHT          *   FILE 336
//*               ACF2 OPTIONS), THIS WILL BE THE ACF2              *   FILE 336
//*               LOGONID.                                          *   FILE 336
//*                                                                 *   FILE 336
```
