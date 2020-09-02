---
title: 'IEnumDebugThreads2:: GetCount | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::GetCount
helpviewer_keywords:
- IEnumDebugThreads2::GetCount
ms.assetid: 81b7f139-d24e-4040-9adc-d664d77563ba
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1ffe42c0faf764fb54bfc2cdec9970f48c6440c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147791"
---
# <a name="ienumdebugthreads2getcount"></a>IEnumDebugThreads2::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Retorna o número de elementos na enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pcelt`  
 fora Retorna o número de elementos na enumeração.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método não faz parte da interface de enumeração com personalizada que especifica que apenas os `Next` métodos, `Clone` , `Skip` e `Reset` precisam ser implementados.  
  
## <a name="see-also"></a>Consulte Também  
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
