---
title: IApplicationDebugger::onDebugOutput | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onDebugOutput
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onDebugOutput
ms.assetid: 978d8bcf-16dc-4f24-a6bc-206adee2b2e9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ffe4d56357a96dac8d5155ac2f8bd5182adef47e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151278"
---
# <a name="iapplicationdebuggerondebugoutput"></a>IApplicationDebugger::onDebugOutput
Manipula um evento de saída de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT onDebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pstr`  
 [in] Cadeia de caracteres para exibir no depurador.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 O depurador exibe normalmente `pstr` em uma janela de saída.  
  
 Esse método é chamado quando `IDebugApplication::DebugOutput` é chamado.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)