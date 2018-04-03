---
UID: NC:wudfwdm.PINTERFACE_REFERENCE
title: PINTERFACE_REFERENCE
author: windows-driver-content
description: The InterfaceReference routine increments the reference count on a driver-defined interface.
old-location: kernel\interfacereference.htm
old-project: kernel
ms.assetid: 21737c1a-dd9d-4011-85c0-7ff871265ed5
ms.author: windowsdriverdev
ms.date: 2/24/2018
ms.keywords: InterfaceReference, InterfaceReference routine [Kernel-Mode Driver Architecture], PINTERFACE_REFERENCE, drvr_interface_d7092619-d2e6-4ca6-bbd3-f857d775f73e.xml, kernel.interfacereference, wdm/InterfaceReference
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: callback
req.header: wudfwdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h, Miniport.h, Wudfwdm.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	UserDefined
api_location:
-	Wdm.h
api_name:
-	InterfaceReference
product:
- Windows
targetos: Windows
req.typenames: WDF_USB_REQUEST_TYPE, *PWDF_USB_REQUEST_TYPE
req.product: Windows 10 or later.
---

# PINTERFACE_REFERENCE callback


## -description


The <i>InterfaceReference</i> routine increments the reference count on a driver-defined interface.


## -prototype


````
PINTERFACE_REFERENCE InterfaceReference;

VOID InterfaceReference(
  _In_ PVOID Context
)
{ ... }
````


## -parameters




### -param Context [in]

A pointer to interface-specific context information. The caller passes the value that is passed as the <b>Context</b> member of the <a href="..\wdm\ns-wdm-_interface.md">INTERFACE</a> structure for the interface.


## -returns



None




## -remarks



You can use the <a href="..\wudfwdm\nc-wudfwdm-pinterface_dereference.md">InterfaceDereference</a> routine to decrement the reference count for the interface.

The driver that exports the interface is responsible for calling <i>InterfaceReference</i> to increment the reference count before the driver exports the interface. For example, the driver that initially exported the interface in response to an <a href="https://msdn.microsoft.com/library/windows/hardware/ff551687">IRP_MN_QUERY_INTERFACE</a> request calls <i>InterfaceReference</i>. Also, a driver that passes a pointer to the interface to another driver must call <i>InterfaceReference</i>.




## -see-also

<a href="https://msdn.microsoft.com/library/windows/hardware/ff551687">IRP_MN_QUERY_INTERFACE</a>



<a href="..\wdm\ns-wdm-_interface.md">INTERFACE</a>



<a href="..\wudfwdm\nc-wudfwdm-pinterface_dereference.md">InterfaceDereference</a>



 

 


