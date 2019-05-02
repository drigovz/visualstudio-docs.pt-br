---
title: IDebugPointerObject::SetBytes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d467b037f4e2affea53a142304507f876630999
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58928281"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Define o valor apontado por uma série de bytes consecutivos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwStart`  
 [in] Um deslocamento, em bytes, desde o início do objeto apontado.  
  
 `dwCount`  
 [in] O número de bytes a ser definido.  
  
 `pBytes`  
 [in] Uma matriz de bytes que representa o novo valor. Esse valor é armazenado no objeto, começando no deslocamento especificado.  
  
 `pdwBytes`  
 [out] Retorna que o número de bytes realmente definido.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é usado se o ponteiro, conforme representado por este [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) aponta para um tipo primitivo ou uma matriz de tipos primitivos (ou seja, uma matriz que pode ser representado por uma simple sequência de bytes). Isso `IDebugPointerObject` objeto não pode ser uma referência nula (ele deve apontar para um endereço na memória).  
  
## <a name="see-also"></a>Consulte também  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
