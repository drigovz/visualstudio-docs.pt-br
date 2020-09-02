---
title: 'IDebugEngine2:: setlocale | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6b071bcc68b383854e1e5a12f3ae2cc08ea86f19
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195920"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Define a localidade do mecanismo de depuração (DE).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(   
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `wLangID`  
 no Especifica a localidade do idioma. Por exemplo, 1033 para inglês.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado pelo SDM (Gerenciador de depuração de sessão) para propagar as configurações de localidade do IDE para que as cadeias de caracteres retornadas por sejam localizadas corretamente.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
