---
title: 'IDebugReference2:: SetValueAsString | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsString
helpviewer_keywords:
- IDebugReference2::SetValueAsString
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b36b579f46739fd6ff554f2087be07ccd6bb69d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178168"
---
# <a name="idebugreference2setvalueasstring"></a>IDebugReference2::SetValueAsString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Define o valor de uma referência de uma cadeia de caracteres. Reservado para uso futuro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   DWORD     dwRadix,  
   DWORD     dwTimeout  
);  
```  
  
```csharp  
int SetValueAsString (   
   string pszValue,  
   uint   dwRadix,  
   uint   dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszValue`  
 no O valor como uma cadeia de caracteres.  
  
 `dwRadix`  
 no A base a ser usada na formatação de qualquer informação numérica.  
  
 `dwTimeout`  
 no Tempo máximo, em milissegundos, a aguardar antes de retornar deste método. Use `INFINITE` para aguardar indefinidamente.  
  
## <a name="return-value"></a>Valor Retornado  
 Sempre retorna `E_NOTIMPL`.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
