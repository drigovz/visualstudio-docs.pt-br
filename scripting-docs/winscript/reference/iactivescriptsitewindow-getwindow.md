---
title: IActiveScriptSiteWindow::GetWindow | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 268a54ccdcbd70ed159758720db0735f16d81492
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097378"
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
 [out] Endereço de uma variável que recebe o identificador de janela.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK` se for bem-sucedido, ou `E_FAIL` se ocorreu um erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é semelhante ao `IOleWindow::GetWindow` método.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)