---
title: IDebugProgram2::EnumCodeContexts | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3a49d35d6ea4263aab4e9fcdce2581a736e5cc5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830165"
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera uma lista dos contextos de código para uma posição especificada em um arquivo de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT EnumCodeContexts(   
   IDebugDocumentPosition2*  pDocPos,  
   IEnumDebugCodeContexts2** ppEnum  
);  
```  
  
```csharp  
int EnumCodeContexts(   
   IDebugDocumentPosition2     pDocPos,  
   out IEnumDebugCodeContexts2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pDocPos`  
 [in] Uma [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) objeto que representa uma posição abstrata em um arquivo de origem conhecido para o IDE.  
  
 `ppEnum`  
 [out] Retorna um [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) objeto que contém uma lista de contextos de código.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método permite que a depuração de sessão (SDM) Gerenciador ou IDE para mapear uma posição de arquivo de origem em uma posição de código. Mais de um contexto de código será retornado se a origem gera vários blocos de código (por exemplo, modelos de C++).  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)

