---
description: "Learn more about: Equates and Structure Layouts"
title: "Equates and Structure Layouts2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0037fb76-c9b0-41ce-9a52-aa80b1bf93c3
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Equates and Structure Layouts
Many standard operating system device driver error codes are used (for example, "invalid function"), together with a new set of device driver-specific errors. Return codes below 0x80 reflect serious failures.  
  
```  
/* Copyright Data Connection Ltd. 1989 */_  
/*****************************************************************************/  
/* Link Device Driver interface constants and structures. */  
/*****************************************************************************/  
/*****************************************************************************/  
/* WIN32  16/04/92  SW   Added more helpful names from WIN32 hdr file        */  
/* IHV    03/06/92  MF2  Add semfisui.h                                      */  
/*****************************************************************************/  
  
/*****************************************************************************/  
/* This include file is used in 5 subsystems                   */  
/*                                                             */  
/* - the NT   driver                         LINK_NTDRIVER     */  
/* - the X25  link service for NT            LINK_NTX25        */  
/* - the SDLC link service for NT            LINK_NTSDLC       */  
/* - the X25  link service for OS/2          LINK_OS2X25       */  
/* - the SDLC link service for OS/2          LINK_OS2SDLC      */  
/*                                                             */  
/* (The OS/2 driver doesn't count because it is in assembler). */  
/*                                                             */  
/* These are distinguished by #defines as set in the following */  
/*                                                             */  
/*****************************************************************************/  
  
#ifdef        IMADRIVER  
  #define     LINK_NTDRIVER  
#else  
  #ifdef      SDLC  
    #ifdef    WIN32  
      #define LINK_NTSDLC  
    #else  
      #define LINK_OS2SDLC  
    #endif  
  #else  
    #ifdef    WIN32  
      #define LINK_NTX25  
    #else  
      #define LINK_OS2X25  
    #endif  
  #endif  
#endif  
/*****************************************************************************/  
/* Device function codes for DosDevIOCtl to link device driver               */  
/*****************************************************************************/  
#ifdef WIN32                /* WIN32 constants defined in semfisui.h         */  
#define IoctlCodeSetEvent               0x410  
#define IoctlCodeSetLinkChar            0x420  
#define IoctlCodeSetV24                 0x430  
#define IoctlCodeTxFrame                0x440  
#define IoctlCodeAbortTransmit          0x450  
#define IoctlCodeAbortReceiver          0x460  
#define IoctlCodeSetInterfaceRecord     0x610 /*IRMdl?*/  
#define IoctlCodeGetV24                 0x623  
#define IoctlCodeRxFrame                0x633  
#define IoctlCodeReadInterfaceRecord    0x643   /*IRMdl?*/  
#else  
//obsolete names from previous version  
//#define CELDDSSH 0x41       /* Set Semaphore Handle                          */  
//#define CELDDSLC 0x42       /* Set Link Characteristics                      */  
//#define CELDDSVS 0x43       /* Set V24 Output status                         */  
//#define CELDDTXF 0x44       /* Transmit a frame of data                      */  
//#define CELDDATX 0x45       /* Abort Transmitter                             */  
//#define CELDDARX 0x46       /* Abort Receiver                                */  
//#define CELDDGIR 0x61       /* Get Interface Record Address                  */  
//#define CELDDGVS 0x62       /* Get V24 Input Status                          */  
//#define CELDDRXF 0x63       /* Receive a frame of data                       */  
//#define CELDDCAT 0x82       /* Device function category code                 */  
//  
// new names  
  
#define IoctlCodeSetEvent               0x41  
#define IoctlCodeSetLinkChar            0x42  
#define IoctlCodeSetV24                 0x43  
#define IoctlCodeTxFrame                0x44  
#define IoctlCodeAbortTransmit          0x45  
#define IoctlCodeAbortReceiver          0x46  
#define IoctlCodeSetInterfaceRecord     0x61  
#define IoctlCodeGetV24                 0x62  
#define IoctlCodeRxFrame                0x63  
  
#endif  
  
/*****************************************************************************/  
/* Constants for the driver-specific IOCtl return codes.                     */  
/*****************************************************************************/  
#define CEDNODMA 0xff80     /* Warning (NO DMA!) from set link chrctrstcs    */  
/*****************************************************************************/  
/* Equates for the link options byte 1.                                      */  
/*****************************************************************************/  
#define CEL4WIRE 0x80  
#define CELNRZI  0x40  
#define CELPDPLX 0x20  
#define CELSDPLX 0x10  
#define CELCLOCK 0x08  
#define CELDSRS  0x04  
#define CELSTNBY 0x02  
#define CELDMA   0x01  
  
/*****************************************************************************/  
/* Equates for the driver set link characteristics byte 1.                   */  
/*****************************************************************************/  
#define CED4WIRE 0x80  
#define CEDNRZI  0x40  
#define CEDHDLC  0x20  
#define CEDFDPLX 0x10  
#define CEDCLOCK 0x08  
#define CEDDMA   0x04  
#define CEDRSTAT 0x02  
#define CEDCSTAT 0x01  
  
/* Nicer names for NT-style code */  
  
#define LinkOption_4Wire           CED4WIRE  
#define LinkOption_NRZI            CEDNRZI  
#define LinkOption_HDLC            CEDHDLC  
#define LinkOption_FullDuplex      CEDFDPLX  
#define LinkOption_InternalClock   CEDCLOCK  
#define LinkOption_DMA             CEDDMA  
#define LinkOption_ResetStatistics CEDRSTAT  
  
/*****************************************************************************/  
/* Equates for the output V24 interface flags.                               */  
/*****************************************************************************/  
#define CED24RTS 0x01  
#define CED24DTR 0x02  
#define CED24DRS 0x04  
#define CED24SLS 0x08  
#define CED24TST 0x10  
  
/* Nicer names for NT-style code */  
  
#define IR_OV24RTS  CED24RTS  
#define IR_OV24DTR  CED24DTR  
#define IR_OV24DSRS CED24DRS  
#define IR_OV24SlSt CED24SLS  
#define IR_OV24Test CED24TST  
  
/*****************************************************************************/  
/* Equates for the input V24 interface flags.                                */  
/*****************************************************************************/  
#define CED24CTS 0x01  
#define CED24DSR 0x02  
#define CED24DCD 0x04  
#define CED24RI  0x08  
  
/* Nicer names for NT-style code */  
  
#define IR_IV24CTS  CED24CTS  
#define IR_IV24DSR  CED24DSR  
#define IR_IV24DCD  CED24DCD  
#define IR_IV24RI   CED24RI  
#define IR_IV24Test 0x10  
  
/*****************************************************************************/  
/* Structure for the device driver interface record.                         */  
/*****************************************************************************/  
  
#define CEDSTCRC  0         /* Frames received with incorrect CRC            */  
#define CEDSTOFL  1         /* Frames received longer than the maximum       */  
#define CEDSTUFL  2         /* Frames received less than 4 octets long       */  
#define CEDSTSPR  3         /* Frames received ending on a non-octet bndry   */  
#define CEDSTABT  4         /* Aborted frames received                       */  
#define CEDSTTXU  5         /* Transmitter interrupt underruns               */  
#define CEDSTRXO  6         /* Receiver    interrupt overruns                */  
#define CEDSTDCD  7         /* DCD (RLSD) lost during frame reception        */  
#define CEDSTCTS  8         /* CTS lost while transmitting                   */  
#define CEDSTDSR  9         /* DSR drops                                     */  
#define CEDSTHDW 10         /* Hardware failures - adapter errors            */  
  
#define CEDSTMAX 11  
  
#define SA_CRC_Error       CEDSTCRC  
#define SA_RxFrameTooBig   CEDSTOFL  
#define SA_RxFrameTooShort CEDSTUFL  
#define SA_Spare           CEDSTSPR  
#define SA_RxAbort         CEDSTABT  
#define SA_TxUnderrun      CEDSTTXU  
#define SA_RxOverrun       CEDSTRXO  
#define SA_DCDDrop         CEDSTDCD  
#define SA_CTSDrop         CEDSTCTS  
#define SA_DSRDrop         CEDSTDSR  
#define SA_HardwareError   CEDSTHDW  /* e.g. CmdBufferFull not set  */  
  
#define SA_Max_Stat        CEDSTMAX  
  
#ifdef WIN32  
  
typedef struct         _INTERFACE_RECORD  
{  
  int                   RxFrameCount;   /* incremented after each frame rx'd */  
  int                   TxMaxFrSizeNow; /* max available frame size av. now  */  
                                        /* (changes after each Tx DevIoctl   */  
                                        /* to DD or after Tx completed)      */  
  int                   StatusCount;    /* How many status events have been  */  
                                        /* triggered.                        */  
  UCHAR                 V24In;          /* Last 'getv24i/f' value got        */  
  UCHAR                 V24Out;         /* Last 'setv24 outputs' value set   */  
  
/*       The values for the indexes into the link statistics array of the */  
/*       various types of statistic. */  
  
  int                   StatusArray[SA_Max_Stat];  
  
}                       IR,  
                     * PIR;  
  
#else  
typedef struct teifrec {  
  
        USHORT    RxFrameCount;  
        USHORT    TxMaxFrSizeNow;  
        USHORT    StatusCount;  
        UCHAR     V24In;  
        UCHAR     V24Out;  
        USHORT    StatusArray[CEDSTMAX];  
  
        }TEIFREC;  
  
typedef TEIFREC far * TEIFRPTR;  
#endif  
  
/*****************************************************************************/  
/* Structure for the set link characteristics parameter block.               */  
/*****************************************************************************/  
  
#ifdef WIN32  
typedef struct  _SLPARMS  
{  
        int     SLFrameSize;            /* max frame size on link - must be  */  
                                        /* in range 270 to ?2K-ish           */  
        LONG    SLDataRate;             /* not used by us - external clocks  */  
        UCHAR   SLOurAddress1;          /* ) e.g C1/FF or 00/00 or 01/03     */  
        UCHAR   SLOurAddress2;          /* )                                 */  
        UCHAR   SLLinkOptionsByte;      /* see documentation & LinkOption_*  */  
        UCHAR   SLSpare1;  
}  
                SLPARMS;  
#else  
  
typedef struct teslcrec {  
  
        USHORT  SLFrameSize;  
        ULONG   SLDataRate;  
        UCHAR   SLOurAddress1;  
        UCHAR   SLOurAddress2;  
        UCHAR   SLLinkOptionsByte;  
        UCHAR   SLSpare1;  
  
        }TESLCREC;  
  
#endif  
  
/*****************************************************************************/  
/* DEVICEIOCTL macros                                                        */  
/*****************************************************************************/  
#ifdef WIN32  
/* NT_SUCCESS ripped of from DDK's ntdef.h, which we do not want to include  */  
/* for now temporarily (12/5/92)                                             */  
#define NT_SUCCESS(Status) ((NTSTATUS)(Status) >= 0)  
  
#define SETEVENTHANDLE(H) NtDeviceIoControlFile(                   \  
                seldrvrh,                   \  
                H,                          \  
                ( PVOID ) NULL,             \  
                ( PVOID ) NULL,             \  
                &IoStatus,                  \  
                IoctlCodeSetEvent,          \  
                ( PVOID ) NULL,             \  
                0L,                         \  
                ( PVOID ) NULL,             \  
                0L                          \  
               )  
  
#define SETINTERFACERECORD(R) NtDeviceIoControlFile(   \  
                seldrvrh,                   \  
                ( PVOID ) NULL,             \  
                ( PVOID ) NULL,             \  
                ( PVOID ) NULL,             \  
                &IoStatus,                  \  
                IoctlCodeSetInterfaceRecord,           \  
                                            \  
                &R,                         \  
                sizeof(R),                  \  
                ( PVOID ) NULL,             \  
                0L                          \  
               )  
  
#define SETV24STATUS NtDeviceIoControlFile(            \  
                seldrvrh,                   \  
                ( PVOID ) NULL,             \  
                ( PVOID ) NULL,             \  
                ( PVOID ) NULL,             \  
                &IoStatus,                  \  
                IoctlCodeSetV24,            \  
                NULL,             \  
                0L,                         \  
                &pInterfaceRecord->V24Out,  \  
                1L                          \  
               )  
  
/*****************************************************************************/  
/* The above change is temporary!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!*/  
/*****************************************************************************/  
  
#define GETV24STATUS NtDeviceIoControlFile(   \  
                  seldrvrh,                   \  
                  ( PVOID ) NULL,             \  
                  ( PVOID ) NULL,             \  
                  ( PVOID ) NULL,             \  
                  &IoStatus,                  \  
                  IoctlCodeGetV24,            \  
                  ( PVOID ) NULL,             \  
                  0L,                         \  
                  ( PVOID ) NULL,             \  
                  0L                          \  
                 )  
  
#define SETLINKCHARACTERISTICS(A) NtDeviceIoControlFile(      \  
                seldrvrh,                   \  
                NULL,                       \  
                ( PVOID ) NULL,             \  
                ( PVOID ) NULL,             \  
                &IoStatus,                  \  
                IoctlCodeSetLinkChar,       \  
                &A,                         \  
                sizeof(A),                  \  
                ( PVOID ) NULL,             \  
                0L                          \  
               )  
  
#define TRANSMITFRAME(A,B) NtDeviceIoControlFile(             \  
                 seldrvrh,                 \  
                 NULL,                     \  
                 ( PVOID ) NULL,           \  
                 ( PVOID ) NULL,           \  
                 &IoStatus,                \  
                 IoctlCodeTxFrame,         \  
                 ( PVOID ) NULL,           \  
                 0L,                       \  
                 A,                        \  
                 B                         \  
                )  
  
#define RECEIVEFRAME(A,B) NtDeviceIoControlFile(              \  
                 seldrvrh,             \  
                 NULL,                 \  
                 ( PVOID ) NULL,       \  
                 ( PVOID ) NULL,       \  
                 &IoStatus,            \  
                 IoctlCodeRxFrame,     \  
                 ( PVOID ) NULL,       \  
                 0L,                   \  
                 A,                    \  
                 B                     \  
                )  
  
#define READINTERFACERECORD NtDeviceIoControlFile( \  
                 seldrvrh,             \  
                 NULL,                 \  
                 ( PVOID ) NULL,       \  
                 ( PVOID ) NULL,       \  
                 &IoStatus,            \  
                 IoctlCodeReadInterfaceRecord, \  
                 ( PVOID ) NULL,       \  
                 0L,                   \  
                 &InterfaceRecord,     \  
                 sizeof(InterfaceRecord) \  
                )  
  
#else  
#define NT_SUCCESS(R) ((R) == 0)  
  
#define SETEVENTHANDLE(H)  DosDevIOCtl(NULL,           \  
                   &H,                                 \  
                   IoctlCodeSetEvent,                  \  
                   CELDDCAT,                           \  
                   seldrvrh)  
  
#define GETINTERFACERECORD(P) DosDevIOCtl(NULL,        \  
                   &P,                                 \  
                   IoctlCodeGetInterfaceRecord,        \  
                   CELDDCAT,                           \  
                   seldrvrh)  
  
#define SETV24STATUS DosDevIOCtl(NULL,                 \  
                   NULL,                               \  
                   IoctlCodeSetV24,                    \  
                   CELDDCAT,                           \  
                   seldrvrh)  
  
#define GETV24STATUS DosDevIOCtl(NULL,                 \  
                     NULL,                             \  
                     IoctlCodeGetV24,                  \  
                     CELDDCAT,                         \  
                     seldrvrh)  
  
#define SETLINKCHARACTERISTICS(A) DosDevIOCtl((long) NULL,  \  
                   (char far *) &A,                         \  
                   IoctlCodeSetLinkChar,                    \  
                   CELDDCAT,                                \  
                   seldrvrh)  
  
#define TRANSMITFRAME(F,L) DosDevIOCtl(F,              \  
                   &L,                                 \  
                   IoctlCodeTxFrame,                   \  
                   CELDDCAT,                           \  
                   seldrvrh)  
  
#define RECEIVEFRAME(F,L)  DosDevIOCtl(F,              \  
                           &L,                         \  
                           IoctlCodeRxFrame,           \  
                           CELDDCAT,                   \  
                           seldrvrh)  
#endif  
  
//############################################################################  
  
/*****************************************************************************/  
/* INFO_ : additional information error codes put in IoStatus.Information    */  
/*****************************************************************************/  
  
#define INFO_CANT_ALLOCATE_SPINLOCK      1  
#define INFO_CANT_CONNECT_INTERRUPT      2  
#define INFO_HARDWARE_INIT_FAILURE       3  
#define INFO_SET_EVENT_NO_EVENT          4  
#define INFO_HARDWARE_CMD_TIMEOUT        5  
#define INFO_LINKCHAR_BUF_WRONG_SIZE     6  
#define INFO_FRAME_BUF_TOO_BIG           7  
#define INFO_FRAME_BUF_TOO_SMALL         8  
#define INFO_NO_CLOCKS                   9  
#define INFO_NO_DMA_FDX                 10  
#define INFO_CANT_ALLOCATE_MDL          11  
#define INFO_CANT_ALLOCATE_MEMORY       12  
#define INFO_DMA_BUFFER_UNUSABLE        14  
#define INFO_TX_BUFFER_FULL             15  
#define INFO_TX_FRAME_TOO_BIG           16  
#define INFO_TX_FRAME_TOO_SMALL         17  
#define INFO_READ_IR_BUFFER_WRONG_SIZE  18  
#define INFO_NEEDS_MCA_BUS              19  
#define INFO_NEEDS_ISA_BUS              20  
  
```
