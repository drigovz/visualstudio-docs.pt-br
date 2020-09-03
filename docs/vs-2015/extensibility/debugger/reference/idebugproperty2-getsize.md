---
title: 'IDebugProperty2:: GetSize | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetSize
helpviewer_keywords:
- IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e6c9118a9ce5a6dddb284d41b3c0b23ca8275f06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193459"
---
# <a name="idebugproperty2getsize"></a>IDebugProperty2::GetSize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém o tamanho, em bytes, do valor da propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetSize (   
   DWORD* pdwSize  
);  
```  
  
```csharp  
int GetSize (   
   out uint pdwSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwSize`  
 fora Retorna o tamanho, em bytes, do valor da propriedade.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna o código de erro. Retorna `S_GETSIZE_NO_SIZE` se a propriedade não tem tamanho.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
