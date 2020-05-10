ALl these documents from IBM master the Mainframe 2019 contest


## Data set naming rules are:

* A data set name consists of one or more parts connected by periods.
*  Each part is called a qualifier.
* Each qualifier must begin with an uppercase alphabetic character (A to Z) or the special character @, #, or $.
* The remaining characters in each qualifier can be uppercase alphabetic, special, or numeric (0 to 9) characters.
* Each qualifier must be 1 to 8 characters in length.
* The maximum length of a complete data set name is 44 characters, including the periods.
* Most z/OS environments agree upon detailed data set naming standards.

### Invalid data set names are:

* .X
  Period is only used to separate qualifiers
* PREFIX.TeST1
  All lowercase alphabetic characters are invalid
* DEPT58.IDEAS.FUTURE.APPROVED.4#
  Qualifier cannot begin with a numeric
* A.B.C.D.E.F.G.H.I.J.K.L.M.N.O.P.Q.R.S.T.U.V.W.X.Y.Z
  Length is greater than 44
* MASTER.THE.MAINFRAME
  MAINFRAME qualifier is greater than 8 characters
  
 #### z/OS data sets are a collection of "records" and not a stream of bytes.
  When a z/OS program reads data, the program is reading one or more data records.
  When a z/OS program writes data, the program is writing data records.
  
 z/OS needs more than a data set name to create a data set such as:

* Record length
* Record format
*  Fixed length records or Variable length records
*  Blocksize - number of records in a block
* Data Set Organization
 * Sequential - a collection of records
 * Partitioned - a collection of members where the members contain records
 * VSAM - Virtual Storage Access Method
   flexibility to organize records in four unique types
   designed for high speed and high volume access to data

 Syntax involved in creating a data set includes:

* LRECL - logical record length
* RECFM - record format
* BLKSIZE - block size
* DSORG - data set organization
* SPACE - disk storage size limits
*  primary extent value
   - all data sets have 1 primary extent
*  secondary extent value
   - numerous secondary extents are automatically created after the primary extent
     is full
* UNIT and optionally VOL=SER=
  device type and disk volume label
* LIKE - uses attributes of a like data set name for creating new data set

 Commonly used mechanisms to create z/OS data sets are:

* JCL DD parameters
* ISPF Data Set Utility panel
* TSO ALLOCATE command
* System utility programs such as IDCAMS
* System services, Storage Managed Subsystem (SMS)

 newly created data set requires specific data set attribute information such as:

* What is the desired the record length (LRECL= value)
* Are the record length fixed in size or variable in size (RECFM= value)
* What is the desired data set organization (DSORG= value)
* What volume should be used to store the data set (VOL=SER= value)
* What is the volume type, disk or tape (UNIT= value)
* How much disk space should the data set be limited to consuming (SPACE= value)
