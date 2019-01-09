---
title: 'Método ijsdebugprocess:: Createbreakpoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateBreakPoint
apilocation:
- jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 661e584133f4ec3c4e571d157a63844c5b1145b7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097559"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>Método IJsDebugProcess::CreateBreakPoint
Define o ponto de interrupção na posição do documento especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `documentId`  
 [in] Ponteiro para IDebugDocumentText.  
  
 `characterOffset`  
 [in] Deslocamento de caractere desde o início do arquivo.  
  
 `characterCount`  
 [in] Comprimento do texto do documento dentro do qual o ponto de interrupção deve ser inserido.  
  
 `isEnabled`  
 [in] Especifica se o ponto de interrupção está habilitado.  
  
 `ppDebugBreakPoint`  
 [out] Objeto que representa o ponto de interrupção que foi criado.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)