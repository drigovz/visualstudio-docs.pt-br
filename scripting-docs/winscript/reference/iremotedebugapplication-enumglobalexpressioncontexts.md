---
title: IRemoteDebugApplication::EnumGlobalExpressionContexts | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 92ab12dc9944c328e744c7f39252facb8e91a3f7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944277"
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