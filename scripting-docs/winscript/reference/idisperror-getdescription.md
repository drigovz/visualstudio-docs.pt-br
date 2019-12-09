---
title: 'IDispError:: GetDescription | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetDescription
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetDescription
ms.assetid: 04deaea6-0265-4e34-952e-634edba0e923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d1bb1c3516c2601707e1a0bcd69f4f8409514fe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573147"
---
# <a name="idisperrorgetdescription"></a>IDispError::GetDescription
Retorna uma descrição textual do erro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetDescription(  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrDescription`  
 fora Cadeia de caracteres que contém uma breve descrição do erro.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 O texto é retornado no idioma especificado pelo LCID (identificador de localidade) que foi passado para `IDispatchEx::InvokeEx` para o método que encontrou o erro.  
  
> [!NOTE]
> Este método não está implementado.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDispError](../../winscript/reference/idisperror-interface.md)  
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)