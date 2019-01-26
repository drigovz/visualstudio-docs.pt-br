---
title: IDebugCoreServer3::EnableAutoAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3c3132239ec684f947e702ce59f0a269095f990
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031167"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Permite que a anexação automática para os mecanismos de depuração especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `rgguidSpecificEngines`  
 [in] Matriz de GUIDs para cada mecanismo de depuração para marcar como anexação automática.  
  
 `celtSpecificEngines`  
 [in] O número de mecanismos especificado em `rgguidSpecificEngines`.  
  
 `pszStartPageUrl`  
 [in] A URL inicial para usar ao anexar a automática.  
  
 `pbstrSessionID`  
 [out] ID da sessão que foi anexado automaticamente.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro. Um código de erro é `E_AUTO_ATTACH_NOT_REGISTERED`, que indica se a fábrica de classes auto-attach não foi registrada.  
  
## <a name="remarks"></a>Comentários  
 Quando um programa associado com a URL especificada é iniciado, os mecanismos de depuração especificada são iniciados automaticamente e anexados.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)