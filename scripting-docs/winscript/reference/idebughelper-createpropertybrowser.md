---
title: IDebugHelper::CreatePropertyBrowser | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowser
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowser
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99aa03470b49d02ee9f0ac1548bd1f8e27d0ab34
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562492"
---
# <a name="idebughelpercreatepropertybrowser"></a>IDebugHelper::CreatePropertyBrowser
Retorna um navegador de propriedades que encapsula uma variante.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pvar`  
 no Variante de raiz para procurar.  
  
 `bstrName`  
 no Nome para dar a raiz.  
  
 `pdat`  
 no Thread no qual as propriedades de solicitação são solicitadas. Se esse parâmetro for NULL, nenhum marshaling será executado.  
  
 `ppdob`  
 fora O navegador de propriedades.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna um navegador de propriedades que encapsula uma variante.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)   
   de [interface IDebugHelper](../../winscript/reference/idebughelper-interface.md)  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)