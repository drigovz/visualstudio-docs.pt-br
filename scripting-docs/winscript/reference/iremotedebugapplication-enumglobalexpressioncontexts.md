---
title: IRemoteDebugApplication::EnumGlobalExpressionContexts | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.EnumGlobalExpressionContexts
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::EnumGlobalExpressionContexts
ms.assetid: 61598a34-f409-42a2-810d-a9e92e2f4861
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a7e4f3e7cffe7c127b7ad4fdde47e58e6bc2a31c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091267"
---
# <a name="iremotedebugapplicationenumglobalexpressioncontexts"></a>IRemoteDebugApplication::EnumGlobalExpressionContexts
Enumera os contextos de expressão global para todos os idiomas em execução neste aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT EnumGlobalExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppedec`  
 [out] Enumerador que lista os contextos de expressão global para todos os idiomas em execução neste aplicativo.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método enumera os contextos de expressão global para todos os idiomas em execução neste aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [IRemoteDebugApplication Interface](../../winscript/reference/iremotedebugapplication-interface.md)