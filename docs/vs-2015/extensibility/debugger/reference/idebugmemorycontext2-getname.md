---
title: 'IDebugMemoryContext2:: GetName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::GetName
helpviewer_keywords:
- IDebugMemoryContext2::GetName method
- GetName method
ms.assetid: 8c212556-7d9e-4d68-b2a9-8212f50d0287
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c499dc44e52fd7f23a6801e8836ffc1915c125f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146386"
---
# <a name="idebugmemorycontext2getname"></a>IDebugMemoryContext2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera o nome de usuário para este contexto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrName`  
 fora Retorna o nome do contexto de memória.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O nome de um contexto de memória normalmente não é usado.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
