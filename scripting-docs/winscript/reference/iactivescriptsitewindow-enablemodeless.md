---
title: 'IActiveScriptSiteWindow:: EnableModeless | Microsoft Docs'
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
ms.openlocfilehash: 756bda6209b6209ff14f6d67fef18faaed0b5618
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574138"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
Faz com que o host habilite ou desabilite sua janela principal, bem como qualquer caixa de diálogo sem janela restrita.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fEnable`  
 no Sinalizar que, se `TRUE`, habilitará as caixas de diálogo principal e sem janela restrita ou, se `FALSE`, as desabilitará.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna `S_OK` se tiver êxito ou `E_FAIL` se ocorreu um erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é idêntico ao método `IOleInPlaceFrame::EnableModeless`.  
  
 Chamadas para este método podem ser aninhadas.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)