---
title: IDebugProperty::GetExtendedInfo | Microsoft Docs
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
ms.openlocfilehash: 707474f786a8f88c0e08d887f2c2b09c8aaedc8e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144856"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Obtém informações estendidas de propriedade.  
  
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
 [in] Contagem de objetos de informações estendidas.  
  
 `rgguidExtendedInfo`  
 [in] Uma matriz de `GUID`s é passado para que vários itens de informações estendidas podem ser recuperados ao mesmo tempo.  
  
 `pExtendedInfo`  
 [out] Retorna uma matriz de `VARIANT`s que pode ser usado para recuperar as informações de propriedade estendida.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um válidas `HRESULT`, normalmente `S_OK`.  
  
## <a name="remarks"></a>Comentários  
 Essa interface obtém informações para este objeto estendida. A API existe somente para fins de recuperação de informações que não se prestam a que está sendo recuperado pelo uso de `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)