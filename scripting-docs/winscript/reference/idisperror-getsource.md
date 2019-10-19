---
title: 'IDispError:: GetSource | Microsoft Docs'
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
ms.openlocfilehash: 07c87585a92415f0b910210a56efa47e6f91417b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573096"
---
# <a name="idisperrorgetsource"></a>IDispError::GetSource
Retorna o identificador programático dependente de idioma para a classe ou o aplicativo que gerou o erro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrSource`  
 fora Cadeia de caracteres que contém um identificador programático, no formato `progname.objectname`.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método é usado para determinar a classe ou o aplicativo em que ocorreu a exceção. O identificador programático pode ser retornado no idioma especificado pelo LCID (identificador de localidade) fornecido no momento da invocação.  
  
> [!NOTE]
> Este método não está implementado.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDispError](../../winscript/reference/idisperror-interface.md)