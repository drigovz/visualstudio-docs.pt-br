---
title: IDispError::GetSource | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetSource
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetSource
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a84640f020a1ff255b8c7e5dd753752e0d310a7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446887"
---
# <a name="idisperrorgetsource"></a>IDispError::GetSource
Retorna o identificador programático do dependente de idioma para a classe ou um aplicativo que gerou o erro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrSource`  
 [out] Cadeia de caracteres que contém um identificador programático, na forma `progname.objectname`.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método é usado para determinar a classe ou um aplicativo onde ocorreu a exceção. O identificador programático pode ser retornado no idioma especificado pelo identificador de localidade (LCID) fornecido no momento da invocação.  
  
> [!NOTE]
> Este método não está implementado.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDispError](../../winscript/reference/idisperror-interface.md)