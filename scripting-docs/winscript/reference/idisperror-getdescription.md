---
title: IDispError::GetDescription | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: fa0c837be9a98829551b9c7820faf154779479e4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096948"
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
 [out] Cadeia de caracteres que contém uma breve descrição do erro.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 O texto é retornado no idioma especificado pelo identificador de localidade (LCID) que foi passado para `IDispatchEx::InvokeEx` para o método que encontrou o erro.  
  
> [!NOTE]
>  Este método não está implementado.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDispError](../../winscript/reference/idisperror-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)