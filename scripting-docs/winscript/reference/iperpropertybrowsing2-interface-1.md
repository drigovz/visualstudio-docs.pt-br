---
title: Interface IPerPropertyBrowsing2 1 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2 interface
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 156cf9a1e104b8a2d7ffe4e48bd39642ef1abbd0
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159576"
---
# <a name="iperpropertybrowsing2-interface-1"></a>Interface 1 IPerPropertyBrowsing2
Acessa as informações nas páginas de propriedades oferecidas por um objeto.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|`GetDisplayString`|Retorna uma cadeia de caracteres de texto que descreve a propriedade especificada.|  
|`MapPropertyToPage`|Retorna o CLSID da página de propriedades que permite a manipulação da propriedade especificada.|  
|`GetPredefinedStrings`|Retorna uma matriz de cadeias de caracteres de contado (`LPOLESTR` ponteiros) listando as descrições dos valores permitidos que pode aceitar a propriedade especificada.|  
|`SetPredefinedValue`|Define o valor da propriedade como o valor predefinido identificado pelo token `dwCookie.`|  
  
## <a name="requirements"></a>Requisitos  
 Header: dbgprop.h