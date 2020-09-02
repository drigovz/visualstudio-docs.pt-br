---
title: 'IDebugEngine3:: LoadSymbols | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29f8af5e258da923ec814e0a224dcf87cbbfae9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195938"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Carrega (conforme necessário) símbolos para todos os módulos que estão sendo depurados por esse mecanismo de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```csharp  
int LoadSymbols();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Nenhum.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna o código de erro.  
  
## <a name="remarks"></a>Comentários  
 Isso carrega os símbolos de depuração para todos os módulos referenciados por esse mecanismo de depuração. Os símbolos serão carregados somente se ainda não tiverem sido carregados. Os símbolos são pesquisados nos caminhos definidos por uma chamada para [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).  
  
## <a name="see-also"></a>Consulte Também  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
