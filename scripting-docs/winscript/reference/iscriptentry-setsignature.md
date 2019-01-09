---
title: IScriptEntry::SetSignature | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 660f667d3542ff2cb9a7e96444d98b3082218a2a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089499"
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
Conjuntos de informações de tipo para um `IScriptEntry` objeto de função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pti`  
 [in] As informações de tipo.  
  
 `iMethod`  
 [in] O índice de método no `ITypeInfo` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Definir informações de tipo por meio `IScriptEntry::SetSignature` ou [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Informações de tipo também podem ser geradas pela entrada com base na representação interna de função.  
  
## <a name="see-also"></a>Consulte também  
 [IScriptEntry Interface](../../winscript/reference/iscriptentry-interface.md)