---
title: 'IPerPropertyBrowsing2:: getdisplaystring | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetDisplayString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetDisplayString
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc702ad15d1aba04bf991c04b585728afde4fb41
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571457"
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
Obtém uma cadeia de caracteres para os tipos de exibição que não são inerentemente visíveis o texto retornado é um nome que descreve a propriedade e pode ser exibido na interface do usuário do chamador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dispid`  
 no Identificador de expedição da propriedade cujo nome de exibição é solicitado.  
  
 `pBstr`  
 fora Ponteiro para a `BSTR` que contém o nome de exibição da propriedade identificada por `dispID`.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um `HRESULT` válido, geralmente `S_OK`.  
  
## <a name="remarks"></a>Comentários  
 A cadeia de caracteres retornada não é um valor válido da propriedade. É apenas uma exibição de cadeia de caracteres da propriedade.  
  
## <a name="see-also"></a>Consulte também  
 [Interface 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)