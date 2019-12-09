---
title: 'IDebugProperty:: GetExtendedInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetExtendedInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 130d11c8ed6bb21210d129bb9aace779db3bd54b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562394"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Obtém informações estendidas para a propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cInfos`  
 no Contagem de objetos de informações estendidos.  
  
 `rgguidExtendedInfo`  
 no Uma matriz de `GUID`s é passada para que vários itens de informações estendidas possam ser recuperados ao mesmo tempo.  
  
 `pExtendedInfo`  
 fora Retorna uma matriz de `VARIANT`s que pode ser usada para recuperar as informações de propriedade estendida.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um `HRESULT` válido, geralmente `S_OK`.  
  
## <a name="remarks"></a>Comentários  
 Esta interface obtém informações estendidas para este objeto. A API existe somente para fins de recuperação de informações que não se prestam para serem recuperadas pelo uso de `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)