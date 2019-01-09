---
title: 'Método ijsdebugframe:: Getstackrange | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetStackRange
apilocation:
- jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 049be8a665dae396d4e92fe847e757b266dc6025
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090279"
---
# <a name="ijsdebugframegetstackrange-method"></a>Método IJsDebugFrame::GetStackRange
Retorna o intervalo de endereços absoluto do registro de ativação JavaScript lógico.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pStart`  
 [out] Baixo, a maioria dos ponteiro de pilha do quadro.  
  
 `pEnd`  
 [out] Principais a maioria dos ponteiros do quadro.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="remarks"></a>Comentários  
 Esse método é útil para reunir rastreamentos de pilha intercalados, coletados de vários tempos de execução. O início, fim ponteiros de pilha podem abranger vários registros de ativação de computador físico (para quadros de tempo de execução do JavaScript interpretados). Iniciar > terminar à medida que a pilha cresce de alto para baixo endereço.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)