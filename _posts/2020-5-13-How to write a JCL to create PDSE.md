 ## How to write a JCL to create PDSE ALSO ADD ANOTHER USEFUL LINK



![image-20200513202224103](/images/image-20200513202224103.png)



or other way, need to test

![image-20200513202320642](/images/image-20200513202320642.png)

## TEST ABOVE, FOUND THESE ISSUES, GOOLGE ANOTHER ONE
<https://www.techagilist.com/mainframe/partitioned-data-set-extended-pdse/>

## Final works

//Z80092B JOB ,NOTIFY=$SYSUID
//STEP10  EXEC PGM=IEFBR14
//SYSPRINT DD SYSOUT=*
//SYSIN      DD DSN=Z80092.MY.LOAD,
//    DISP=(NEW,CATLG,DELETE),
//    UNIT=SYSDA,SPACE=(CYL,(10,10,10)),
//    DCB=(LRECL=80,BLKSIZE=4096,DSORG=PO,RECFM=U),
//    DSNTYPE=LIBRARY
//**********************************************************
//**           CREATE A PDSE MEMBER                       **
//**********************************************************
//STEP20  EXEC PGM=ICEGENER
//SYSUT1    DD *
//SYSUT2    DD DSN=Z80092.MY.LOAD(TRY),DISP=SHR
//SYSPRINT  DD SYSOUT=*
//SYSIN     DD DUMMY
