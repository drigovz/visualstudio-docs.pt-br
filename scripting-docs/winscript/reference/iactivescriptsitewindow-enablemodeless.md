---
title: IActiveScriptSiteWindow::EnableModeless | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.EnableModeless
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_EnableModeless
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f15135273b98a65903a5d03de87c541fc032cce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992920"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
Faz com que o host habilitar ou desabilitar a janela principal, bem como todas as caixas de diálogo sem janela restrita.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fEnable`  
 [in] Sinalizador que, se `TRUE`, permite que a janela principal e as caixas de diálogo sem janela restrita ou, se `FALSE`, desabilita-as.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK` se for bem-sucedido, ou `E_FAIL` se ocorreu um erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é idêntico de `IOleInPlaceFrame::EnableModeless` método.  
  
 Chamadas para esse método podem ser aninhadas.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)