---
title: 'Método IJsDebug:: OpenVirtualProcess | Microsoft Docs'
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
ms.openlocfilehash: 3de39beb28a68ec3b8e0d76b17a7e914a464ecfe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577742"
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
 no ID do processo para o qual anexar o depurador.  
  
 `runtimeJsBaseAddress`  
 no O endereço base no qual o tempo de execução do JavaScript foi carregado no processo de destino.  
  
 `pDataTarget`  
 no Interface fornecida pelo depurador para consultar o estado do processo.  
  
 `ppProcess`  
 fora Novo objeto de processo de depuração  
  
## <a name="return-value"></a>Valor retornado  
  
## <a name="remarks"></a>Comentários  
 Retorna E_JsDEBUG_MISMATCHED_RUNTIME se Jscript9diag e Jscript9 não correspondem.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebug](../../winscript/reference/ijsdebug-interface.md)