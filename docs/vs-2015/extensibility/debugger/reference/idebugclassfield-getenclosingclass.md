---
title: 'IDebugClassField:: GetEnclosingClass | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 896d3ecd5202bf85e6b9e86af31796c662a6eef1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190997"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém a classe que inclui essa classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppClassField`  
 fora Retorna um objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que representa a classe delimitadora. Retorna um valor nulo se não houver nenhuma classe delimitadora.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se a classe representada por esse objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) for uma classe aninhada, o `ppClassField` parâmetro retornará um `IDebugClassField` objeto que representa a classe de circunscrição. Por exemplo, dada essa definição de classe:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Chamar o `GetEnclosingClass` método no `IDebugClassField` objeto que representa a `NestedClass` classe retorna um `IDebugClassField` objeto que representa a classe `RootClass` .  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
