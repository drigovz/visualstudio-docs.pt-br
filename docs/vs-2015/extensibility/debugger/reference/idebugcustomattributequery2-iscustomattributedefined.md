---
title: 'IDebugCustomAttributeQuery2:: IsCustomAttributeDefined | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6ef6a04d263e322d408bb7d7c95da1929d89010c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62569313"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Determina se um atributo personalizado existe por nome.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```csharp  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszCustomAttributeName`  
 no Uma cadeia de caracteres que contém o nome do atributo personalizado a ser localizado.  
  
## <a name="return-value"></a>Valor Retornado  
 Retorna S_OK se o atributo personalizado for definido nesse campo; caso contrário, retorna S_FALSE.  
  
## <a name="remarks"></a>Comentários  
 Para obter os bytes de atributo associados ao atributo personalizado, chame o método [GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) .  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
