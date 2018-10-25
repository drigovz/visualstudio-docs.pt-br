---
title: IDebugModule2::GetInfo | Microsoft Docs
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
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c90872f2fe73c406cdd1536db29540bc5f5ac4a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876991"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém informações sobre esse módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp#  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFields`  
 [in] Uma combinação de sinalizadores do [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) enumeração que especificam quais campos de `pInfo` devem ser preenchidos.  
  
 `pInfo`  
 [no, out] Um [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) estrutura será preenchida com uma descrição do módulo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) estrutura contém o nome do módulo que é exibido na **módulos** janela.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)

