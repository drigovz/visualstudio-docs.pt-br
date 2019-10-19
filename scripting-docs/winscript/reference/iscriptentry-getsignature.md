---
title: 'IScriptEntry:: getsignature | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetSignature
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7b07ac64ce7e427a793f0af0db9a7905441d39b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575415"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Retorna informações de tipo para um objeto de função `IScriptEntry`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppti`  
 fora Informações de tipo associadas a este `IScriptEntry` objeto de função.  
  
 `piMethod`  
 fora Índice de método no objeto `ITypeInfo`.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Você define informações de tipo usando [IScriptEntry:: SetSignature](../../winscript/reference/iscriptentry-setsignature.md) ou [IScriptNode:: CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). As informações de tipo também podem ser geradas pela entrada com base na representação de função interna.  
  
## <a name="see-also"></a>Consulte também  
 [IScriptEntry Interface](../../winscript/reference/iscriptentry-interface.md)