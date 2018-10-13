---
title: IDebugProcess2::GetInfo | Microsoft Docs
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
- IDebugProcess2::GetInfo
helpviewer_keywords:
- IDebugProcess2::GetInfo
ms.assetid: 46021dce-bb97-46c3-b0cc-e5b3b68acc35
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9f7cd13ba71d15e28d88005821020b38df29399
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186648"
---
# <a name="idebugprocess2getinfo"></a>IDebugProcess2::GetInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém uma descrição do processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetInfo(  
   PROCESS_INFO_FIELDS  Fields,  
   PROCESS_INFO*        pProcessInfo  
);  
```  
  
```csharp  
int GetInfo(  
   enum_PROCESS_INFO_FIELDS  Fields,  
   PROCESS_INFO[]            pProcessInfo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `Fields`  
 [in] Uma combinação de valores da [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) enumeração que especifica quais campos do `pProcessInfo` parâmetro devem ser preenchidos.  
  
 `pProcessInfo`  
 [out] Um [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) estrutura será preenchida com uma descrição do processo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)

