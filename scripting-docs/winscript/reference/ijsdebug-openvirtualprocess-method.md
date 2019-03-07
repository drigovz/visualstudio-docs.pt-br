---
title: 'Método ijsdebug:: Openvirtualprocess | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: daa5414153ee55a431294afaf7b167ee91839bfc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093984"
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