---
Description: Allows the callback object to specify a help text string for menu items or toolbar buttons. Used by IShellFolderViewCB::MessageSFVCB.
title: SFVM\_GETHELPTEXT message
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# SFVM\_GETHELPTEXT message

Allows the callback object to specify a help text string for menu items or toolbar buttons. Used by [**IShellFolderViewCB::MessageSFVCB**](https://msdn.microsoft.com/en-us/library/Bb774968(v=VS.85).aspx).


```C++
SFVM_GETHELPTEXT 

    wParam = (WPARAM)(int) idCmd,cchMax;

    lParam = (LPARAM)(LPTSTR) pszText;

            
```



## Parameters

<dl> <dt>

*idCmd\_cchMax* \[in\]
</dt> <dd>

The low-order word of this parameter holds the command ID. The high-order word holds the number of characters in the *pszText* buffer.

</dd> <dt>

*pszText* \[out\]
</dt> <dd>

A null-terminated string containing the help text.

</dd> </dl>

## Requirements



|                                     |                                                                                     |
|-------------------------------------|-------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows 2000 Professional \[desktop apps only\]<br/>                          |
| Minimum supported server<br/> | Windows 2000 Server \[desktop apps only\]<br/>                                |
| Header<br/>                   | <dl> <dt>Shlobj.h</dt> </dl> |



 

 



