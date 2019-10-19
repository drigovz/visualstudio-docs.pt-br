---
title: 'IDebugHelper:: CreatePropertyBrowserEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 4d64d9dad54e029dc4c76e8b7e6c7a3f0299b0cb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576496"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Retorna um navegador de propriedades que encapsula uma variante e permite a conversão personalizada de valores VARIAntes ou de tipos VARTYPE em cadeias de caracteres.  
  
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
 no Variante de raiz para procurar.  
  
 `bstrName`  
 no Nome para dar a raiz.  
  
 `pdat`  
 no Thread no qual as propriedades de solicitação são solicitadas. Se esse parâmetro for NULL, nenhum marshaling será executado.  
  
 `pdf`  
 no Objeto que fornece formatação personalizada para variantes.  
  
 `ppdob`  
 fora O navegador de propriedades.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna um navegador de propriedades que encapsula uma variante e permite a conversão personalizada de valores VARIAntes ou tipos VARTYPE em cadeias de caracteres.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugHelper:: CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)    
 @No__t_1 de [interface IDebugHelper](../../winscript/reference/idebughelper-interface.md)  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)