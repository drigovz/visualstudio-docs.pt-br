---
title: 'IDebugAddress:: GetAddress | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4d3263ca020f491e0c1cf20ee49792cacfbc362
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186682"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Retorna uma estrutura que descreve um objeto e sua localização dentro de seu escopo ou contêiner.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pAddress`  
 [entrada, saída] Uma estrutura de [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) que é preenchida por este método.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A estrutura de [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) é passada para esse método, que o preenche com as informações apropriadas. A forma como essas informações são interpretadas depende do tipo de informação retornado e do próprio manipulador de símbolos. Consulte [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) para obter mais detalhes.  
  
## <a name="see-also"></a>Consulte Também  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
