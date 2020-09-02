---
title: 'IDebugProgramHost2:: gethostid | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostId
helpviewer_keywords:
- IDebugProgramHost2::GetHostId
ms.assetid: 7702e221-feb1-446b-a224-cb46c420987e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4e7421ceed436f90612889ba7b80a21ee3079c2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165151"
---
# <a name="idebugprogramhost2gethostid"></a>IDebugProgramHost2::GetHostId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém o identificador do processo que hospeda este programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetHostId(   
   AD_PROCESS_ID* pdwId  
);  
```  
  
```csharp  
int GetHostId(   
   AD_PROCESS_ID[] pdwId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwId`  
 [entrada, saída] Uma estrutura de [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) que é preenchida com as informações do identificador do processo.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
