---
title: 'Método ijsdebug:: Openvirtualprocess | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebug.OpenVirtualProcess
apilocation:
- jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97a055bf1550d74dc6b86d93ffdb9ca406afb43d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151941"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>Método IJsDebug::OpenVirtualProcess
Método de fábrica usado para criar um novo objeto de processo virtual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `processId`  
 [in] Id do processo para anexar o depurador.  
  
 `runtimeJsBaseAddress`  
 [in] O endereço básico no qual o tempo de execução do JavaScript carregado no processo de destino.  
  
 `pDataTarget`  
 [in] Interface fornecido para consultar o estado do processo do depurador.  
  
 `ppProcess`  
 [out] Novo objeto de processo de depuração  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="remarks"></a>Comentários  
 Retornará E_JsDEBUG_MISMATCHED_RUNTIME se Jscript9diag e Jscript9 não corresponderem.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebug](../../winscript/reference/ijsdebug-interface.md)