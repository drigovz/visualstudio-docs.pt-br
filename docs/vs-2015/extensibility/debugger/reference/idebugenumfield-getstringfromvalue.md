---
title: 'IDebugEnumField:: GetStringFromValue | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecdd60c363e30afbe4c61e8e18660a17a06a5ce8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188990"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esse método obtém o nome da constante de enumeração de acordo com seu valor.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```csharp  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `value`  
 no O valor para o qual obter o nome da constante de enumeração.  
  
 `pbstrValue`  
 fora Retorna o nome da constante de enumeração.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna `S_FALSE` se o valor não tem nenhum nome associado ou retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se houver mais de um nome associado ao mesmo valor, o primeiro nome definido na enumeração será retornado.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
