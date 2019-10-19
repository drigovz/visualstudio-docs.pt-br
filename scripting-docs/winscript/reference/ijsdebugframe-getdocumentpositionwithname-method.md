---
title: 'Método IJsDebugFrame:: GetDocumentPositionWithName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithName
apilocation:
- jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b818ca4dc1ec4402973026668972507861c86f22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575118"
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>Método IJsDebugFrame::GetDocumentPositionWithName
Retorna a posição atual deste quadro de pilhas no documento de nível de usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pDocumentName`  
 fora Para scripts estáticos, uma URL para o documento. Para scripts dinâmicos, um nome que contém o tipo de script (por exemplo, código de avaliação, código de função etc.) é retornado.  
  
 `pLine`  
 [fora] posição de linha baseada em 1 dentro do documento.  
  
 `pColumn`  
 [fora] posição de linha baseada em 1 dentro do documento.  
  
## <a name="return-value"></a>Valor retornado  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)