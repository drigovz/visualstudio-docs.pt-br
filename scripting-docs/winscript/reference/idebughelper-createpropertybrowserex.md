---
title: IDebugHelper::CreatePropertyBrowserEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowserEx
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowserEx
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3590fe05ef82f094dd5706f9f527b247d95eda8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097728"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Retorna um navegador de propriedade que envolve uma VARIANTE e permite a conversão personalizada de valores VARIANT ou tipos VARTYPE em cadeias de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pvar`  
 [in] Variante de raiz para procurar.  
  
 `bstrName`  
 [in] Nome a ser atribuído a raiz.  
  
 `pdat`  
 [in] Thread no qual as propriedades da solicitação. Se esse parâmetro for NULL, nenhum empacotamento é executada.  
  
 `pdf`  
 [in] Objeto que oferece formatação personalizada para variantes.  
  
 `ppdob`  
 [out] O navegador de propriedade.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna um navegador de propriedade que envolve uma VARIANTE e permite a conversão personalizada de valores VARIANT ou tipos VARTYPE em cadeias de caracteres.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [Interface IDebugHelper](../../winscript/reference/idebughelper-interface.md)   
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)