---
title: IDebugApplication::CreateApplicationNode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.CreateApplicationNode
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::CreateApplicationNode
ms.assetid: 1a1414f6-df14-4c56-b39a-8384cf16174a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02a15a67d8f8b6171e9f5893c7f8cd15f79776b1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144778"
---
# <a name="idebugapplicationcreateapplicationnode"></a>IDebugApplication::CreateApplicationNode
Cria um novo nó de aplicativo que está associado um provedor de documento específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CreateApplicationNode(  
   IDebugApplicationNode**  ppdanNew  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppdanNew`  
 [out] O nó de aplicativo associado a este provedor de documento.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 O novo nó de aplicativo não estiver visível até que ele seja anexado a um nó pai.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugApplication Interface](../../winscript/reference/idebugapplication-interface.md)