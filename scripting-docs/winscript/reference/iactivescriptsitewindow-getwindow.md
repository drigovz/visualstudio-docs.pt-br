---
title: 'IActiveScriptSiteWindow:: GetWindow | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.GetWindow
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_GetWindow
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8263db447c7692ec7b0982127d63b4bea588a4b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574348"
---
# <a name="iactivescriptsitewindowgetwindow"></a>IActiveScriptSiteWindow::GetWindow
Recupera o identificador para uma janela que pode atuar como o proprietário de uma janela pop-up que o mecanismo de script deve exibir.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `phwnd`  
 fora Endereço de uma variável que recebe o identificador de janela.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna `S_OK` se tiver êxito ou `E_FAIL` se ocorreu um erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é semelhante ao método `IOleWindow::GetWindow`.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)