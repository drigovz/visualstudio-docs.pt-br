---
title: 'IScriptEntry:: SetSignature | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetSignature
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e381e642462fe56e661de9da0d8974dc7bf18b18
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575345"
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
Define informações de tipo para um objeto de função `IScriptEntry`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pti`  
 no As informações de tipo.  
  
 `iMethod`  
 no O índice do método no objeto `ITypeInfo`.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Você define informações de tipo usando `IScriptEntry::SetSignature` ou [IScriptNode:: CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). As informações de tipo também podem ser geradas pela entrada com base na representação de função interna.  
  
## <a name="see-also"></a>Consulte também  
 [IScriptEntry Interface](../../winscript/reference/iscriptentry-interface.md)