                                        RADLST
                            Version 5.5 [October 5, 1988]
 
 
             Author:  Thomas W. Burrows
                      Dept. of Nuclear Energy
                      National Nuclear Data Center
                      Bldg. 197-D
                      Brookhaven National Laboratory
                      Upton, NY 11973
                      Phone: 631-344-5084 FAX: 631-344-2806
                      INTERNET: "NNDCTB@BNL.GOV"
 
                      (Original authors: W.B. Ewbank and M.J. Kowalski, 
                        Nuclear Data Project, Oak Ridge National 
                        Laboratory; B.J. Barton, National Nuclear Data
                        Center, Brookhaven National Laboratory; and L.P.
                        Ekstrom and P. Andersson, Department of Nuclear
                        Physics, Lund University)
 
                  This program is designed to calculate the nuclear and atomic
             radiations  associated  with the radioactive decay of nuclei.  It
             uses as its primary input nuclear decay data in the ENSDF format.
             Listings  or computer files containing the energies, intensities,
             and dose rates  for  various  nuclear  radiations  are  produced.
             These outputs also containing the energies, intensities, and dose
             rates  of  the  associated  atomic  radiations.   Optionally  the
             continua    spectra   for   beta+-   decay   and   for   internal
             bremssstrahlung associated with beta+- and electron-capture decay
             may be calculated.
 
|            NOTE (20-Apr-1999):
|  
|            1.  The atomic mass data (RADMAS.DAT) has  been  updated  to  the
|                1995  Atomic  Mass  Update  (Audi  and Wapstra.  Nucl.  Phys.
|                A595, 409-480 (1995)).
|  
|            2.  The atomic data (MEDNEW.DAT) has been updated to the data  of
|                Schoefeld  and Janssen [Nucl.  Instr.  Phys.  Res.  A369, 527
|                (1996)].
|  
|            3.  The original data are available in  the  files  RADMASOLD.DAT
|                and MEDNEWOLD.DAT, respectively.
|  
 
             NOTE:  The auxiliary program TAILOR has be temporarily  withdrawn
             from distribution for modification.
 
 
 
 
 
 
 
 
 
 
                                          1

                                        RADLST
                            Version 5.5 [October 5, 1988]
 
 
             Input files:
 
                   1.  ENSDF formatted file.  The following  optional  records
                       as defined in cols.  1-9 of the record are allowed:
                      (a)  MERGE/ENDMERGE Specifies that the  radiations  from
                           the data sets contained between them will be merged
                           on output  (Ignored  if  the  data-base  option  is
                           selected)
                      (b)  PAGE Causes the radiation listing output  to  begin
                           on a new page for the following data set.
                      (c)  PARAMETER   Various   parameters   affecting    the
                           calculations  or output of the program may be given
                           in cols.  10-80 of this  record  which  immediately
                           precedes a data set and only affects that data set.
                           The parameters are:
                          (i)  ALLGAM Overrides the minimum  intensity  cutoff
                               for  radiations  and  outputs  all  gammas.  No
                               value should be given for this parameter.
                         (ii)  MAXEC Specifies the number of  electron-capture
                               branches  to be listed in the radiation listing
                               (default=0).
                        (iii)  MAT Specifies  a  material  number  for  ENDF-6
                               output  (default is based on the Z and A of the
                               parent).
                         (iv)  RIMIN Specifies the  minimum  intensity  cutoff
                               (in  percent)  for  radiations  (default=0.001%
                               except for the data-base option [0.1%]).
                          (v)  WEIGHT   Specifies   an   arbitrary   weighting
                               fraction.    Not  allowed  with  data-base  and
                               ENDF-6 options.
 
 
                       Sample input file:  RADLST.INP.  See the report for  an
                       explanation of what is tested within this sample input.
 
                   2.  Atomic  electron  binding  energies,  fluorescence  and
                       Auger-electron  yields:   One of the following two data
                       files must be present:
                      (a)  Direct access binary file (ATOMIC.DAT).  This  file
                           will  be  generated  by  the program if it does not
                           exist and the following file is available.
                      (b)  Sequential file (default name:  MEDNEW.DAT).   Data
                           file provided with distribution.
 
 
 
 
 
 
 
 
 
 
                                          2

                                        RADLST
                            Version 5.5 [October 5, 1988]
 
 
                   3.  Atomic mass data:  If  neither  of  the  two  following
                       files  is  present,  the  program will calculate atomic
                       masses based on the Garvey-Kelson formalism.
                      (a)  Direct access binary file (WAPSTB.DAT).  This  file
                           will  be  generated  by  the program if it does not
                           exist and the following file is available.
                      (b)  Sequential file (default name:  RADMAS.DAT).   Data
                           file provided with distribution.
 
 
 
             Output files:  With the exception of the report file, these files
                   are options.
 
                   1.  Report file:  The input data are listed  in  cols  2-81
                       and messages reporting possible problems or assumptions
                       made are given in cols 82-133.  Possible severe  errors
                       are noted on a line following the record in question.
 
                       After all relevant radiation data have  been  analyzed,
                       there  will be a summary of the energy deposited by the
                       radiations  and  recoiling  nuclei  and  a   comparison
                       between  the  sum  of  these deposited energies and the
                       energy expected from the branching ratios and Q values.
 
                   2.  Radiations listing:  Fortran-formatted file  containing
                       the  nuclear  and  atomic  radiations  obtained  by the
                       program.  See the report for additional details.
 
                   3.  Data-base file:  Presents the  data  generated  by  the
                       program  in  a fixed computer-readable format.  See the
                       report for additional details.
 
                   4.  ENDF-6 format file:  MT=1, MF=451 (comments) and  MT=8,
                       MF=457 (decay data) sections are generated.
 
                   Either the ENSDF-6  file  or  the  data-base  file  may  be
                   generated but not both.
 
             Terminal dialog:
 
                   1.  The program will  ask  which  output  files  should  be
                       generated  (defaults:   radiation listing; no ENDF-like
                       file or data-base file).
 
                   2.  Unless the data-base option is chosen, the user will be
                       asked  if  the  continua should be calculated (default:
                       no).
 
                   3.  The names  of  the  input  and  report  files  will  be
                       requested (defaults:  RADLST.INP and RADLST.RPT).
 
 
                                          3

                                        RADLST
                            Version 5.5 [October 5, 1988]
 
 
                   4.  If the binary data files are not present, the user will
                       be asked for the names of the sequential files.
 
                   5.  The user will be asked the names of the various  output
                       files to be generated (defaults:  ENSDF.RPT, NUDAT.OUT,
                       and ENDF.RAW).
 
                   6.  The source of the atomic data and the mass data will be
                       noted.
 
                   7.  As each data set or group of data sets are processed, a
                       summary  of  the  results  will  be  displayed  on  the
                       terminal.
 
 
             Sample terminal dialogs and outputs:  Following are  descriptions
                   of  the  sample  files included in the distribution.  NOTE:
                   This supersedes Appendix B  of  the  report.   The  various
                   outputs in these files are separated by "%%%%%" followed by
                   the type of output  and  in  some  cases  only  show  those
                   outputs where there are major differences.
 
                   1.  RADLST1.OUT:  Normal options
 
                   2.  RADLST2.OUT:  ENDF option
 
                   3.  RADLST3.OUT:  Data-base file option
 
                   4.  RADLST4.OUT:  Continua with bremsstrahlung chosen
 
                   5.  RADLST5.OUT:  ENDF with  continua  with  bremsstrahlung
                       chosen
 
 
             Compilation and  loading  instructions:   This  program  requires
                   subroutines from the NSDFLIB.ANS package.
 
             Additional documentation:
                   T.W. Burrows. THE PROGRAM RADLST. Brookhaven National 
                   Laboratory Report BNL-NCS-52142 (1988)
 
                                      Version History
             5     11-Jun-86  Conversion of MEDNEW 4(55)[11-SEP-85] to
                              FORTRAN-77 with some guidance from the
                              Swedish FORTRAN-77 Version [SEP-83].
             5.1    4-AUG-86  Modified to run correctly on both TOPS-10 and
                              VAX-11/780 VMS.
             5.1a   6-AUG-86  Added coding so that program may be spawned on
                              VAX-11/780 VMS.
             5.1b   3-SEP-86  Corrected bugs found when generating VAX data
                              base.
             5.2   18-SEP-86  Added machine dependent code.
 
                                          4

                                        RADLST
                            Version 5.5 [October 5, 1988]
 
 
             5.3   12-NOV-86  Added modules to calculate continuous spectra
                              for B+- and associated internal Bremsstrahlung.
             5.3a  27-FEB-87  Corrected problems in decrementing counts for
                              positrons and electron capture.
             5.3b   6-MAR-87  Added modules to calculate internal
                              Bremsstrahlung from electron capture.
             5.4    2-APR-87  First exportable version.
             5.4a  22-APR-87  Modified subroutine ENDCON:
                              a. Corrected errors.
                              b. Added possibility for log-log.
                              c. Compressed interpolation table.
             5.4b   1-JUL-87  General cleanup:
                              a. Program reorganized functionally.
                                 1. Markers added to allow removal of
                                    undesired functions.
                                 2. All variables explicitly defined.
                              b. Corrected misinterpretation of intensities
                                 for STYP=2 in subroutine ENDOUT.
             5.4c  11-SEP-87  a. Added check for blank normalization record.
                              b. Added "ECP" and "B-N" to decay modes, as
                                 distinct types.
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
                                          5

                                        RADLST
                            Version 5.5 [October 5, 1988]
 
 
             5.4d  30-OCT-87  a. Corrected error in label order of X rays in
                                 MEDOUT and NUDOUT.
                              b. Corrected logic in SIGNIF to handle X=0.
                              c. Added acknowledgement and disclaimer.
             5.4e  11-DEC-87  a. Checked fundamental constants for consistency
                                 with 1986 adjustment.
                              b. Combined redundant WARNINGS and MESSAGES.
                              c. Tightened up coding based on analysis of
                                 progam by RXVP80 provided by C. Nordberg
                                 (NEADB).
                              d. Fixed VAX-specific problem on reading input
                                 files which do not have write priveleges by
                                 adding READONLY keyword.
             5.4f   8-FEB-88  a. Fixed incorrect labelling of Auger electrons.
                              b. Fixed logic in GAMPRO which caused multiple
                                 counting of conversion electron intensities
                                 when there were several GAMMA continuation
                                 records. 
                              c. Added check in READ so that ratios would not
                                 be misinterpreted as values.
             5.4g  21-MAR-88  a. Corrected problems in decrementing counts for
                                 negatrons.
                              b. Added check to subroutine NUDOUT and check
                                 and warning to PARPRO for missing parent
                                 half-life.
             5.4h  22-MAY-88  Added check for gross energy mismatch and logic
                                 to suppress output for NUDAT if this occurs
                                    ==== LAST OF Version 5.4 ====
                                          (not distributed)
             5.5    5-OCT-88  a. Added option for outputting in MIRD format
                                                    
                              b. Implemented USNDN FP suggestions for
                                treatment of multiply placed gammas
 
                                        Disclaimer
 
                  Neither the Brookhaven Science Associates, Inc., nor the  US
             Department  of  Energy  make  any  warranty  or  assume any legal
             responsibility for the results produced by the program.
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
                                          6
