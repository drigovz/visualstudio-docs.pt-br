---
title: 'IDebugEnumField:: GetValueFromStringCaseInsensitive | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: efe94a721c432cb1284df299ca267271ab5bef4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188927"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esse método usa uma pesquisa que não diferencia maiúsculas de minúsculas para retornar o valor associado ao nome de uma constante de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetValueFromStringCaseInsensitive(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromStringCaseInsensitive(  
   string    pszValue,   
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszValue`  
 no Uma cadeia de caracteres que especifica o nome para o qual obter o valor. Observe que para C++, essa é uma cadeia de caracteres larga.  
  
 `pValue`  
 fora Retorna o valor numérico associado.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará `S_OK` ; caso contrário, retornará `S_FALSE` , se o nome não fizer parte da enumeração ou um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método não diferencia maiúsculas de minúsculas. Se uma pesquisa com diferenciação de maiúsculas e minúsculas for necessária (por exemplo, em uma linguagem como C++, em que os nomes diferenciam maiúsculas de minúsculas), use [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
