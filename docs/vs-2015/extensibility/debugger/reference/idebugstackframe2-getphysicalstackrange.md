---
title: 'IDebugStackFrame2:: GetPhysicalStackRange | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 99fc1e635691fa290d0a8e4506ef55d677e9ff78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547644"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém uma representação dependente de computador do intervalo de endereços físicos associados a um quadro de pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```csharp  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `paddrMin`  
 fora Retorna o endereço físico mais baixo associado a esse quadro de pilha.  
  
 `paddrMax`  
 fora Retorna o endereço físico mais alto associado a esse quadro de pilhas.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 As informações retornadas por esse método são usadas pelo SDM (Gerenciador de depuração de sessão) para classificar os quadros de pilha.  
  
 Supõe-se que a pilha de chamadas cresce, ou seja, que novos quadros de pilha são adicionados em endereços de memória cada vez mais baixos. Uma arquitetura de tempo de execução deve fornecer intervalos de pilha física que correspondam a essa suposição.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
