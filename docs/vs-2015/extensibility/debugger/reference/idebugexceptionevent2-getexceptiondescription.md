---
title: IDebugExceptionEvent2::GetExceptionDescription | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetExceptionDescription
helpviewer_keywords:
- IDebugExceptionEvent2::GetExceptionDescription
ms.assetid: d07d458f-5729-47e4-9b77-1bd59c61a75a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 98590c0493f8910d31ed059a72dad68caedf6929
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58928274"
---
# <a name="idebugexceptionevent2getexceptiondescription"></a>IDebugExceptionEvent2::GetExceptionDescription
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém uma descrição que pode ser exibida da exceção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetExceptionDescription(   
   BSTR* pbstrDescription  
);  
```  
  
```csharp  
int GetExceptionDescription(   
   out string pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrDescription`  
 [out] Retorna uma descrição que pode ser exibida da exceção.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A cadeia de caracteres retornada desse método é geralmente o nome da exceção e é mostrada na **saída** janela quando a exceção ocorrer.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
