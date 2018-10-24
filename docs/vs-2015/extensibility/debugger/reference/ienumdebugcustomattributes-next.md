---
title: IEnumDebugCustomAttributes::Next | Microsoft Docs
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
- IEnumCustomAttributes::Next
helpviewer_keywords:
- IEnumDebugCustomAttributes::Next
ms.assetid: e36f856b-2619-42d1-b73e-4f2390fc22bd
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 34b37e4213e5072497dc0d9f0de3eda97dc7e034
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879734"
---
# <a name="ienumdebugcustomattributesnext"></a>IEnumDebugCustomAttributes::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera um número especificado de atributos personalizados em uma sequência de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Next (   
   ULONG      celt,  
   CODE_PATH* rgelt,  
   ULONG*     pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint                        celt,   
   out IDebugCustomAttribute[] rgelt,   
   ref uint                    pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] O número de elementos a serem recuperados. Também especifica o tamanho máximo da `rgelt` matriz.  
  
 `rgelt`  
 [out] Uma matriz de [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) objetos a serem preenchidos.  
  
 `pceltFetched`  
 [out] Retorna o número de elementos realmente retornados em `rgelt`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se menos do que o número solicitado de elementos podem ser retornados; caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)

