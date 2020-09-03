---
title: 'IDebugProgramHost2:: GetHostName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb7ceae40282115dc455691789c3882a1620e829
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165119"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém o título, nome amigável ou nome de arquivo do processo de hospedagem deste programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```csharp  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwType`  
 no Um valor da enumeração de [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) .  
  
 `pbstrHostName`  
 fora Retorna o nome solicitado do processo de hospedagem.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Em uma implementação típica desse método, o `dwType` parâmetro é ignorado e um nome amigável do computador host é retornado. Outra implementação possível é passar o `dwType` parâmetro para uma chamada para o método [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) para obter o nome.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
