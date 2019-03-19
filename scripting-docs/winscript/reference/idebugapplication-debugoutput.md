---
title: IDebugApplication::DebugOutput | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.DebugOutput
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::DebugOutput
ms.assetid: 6c02939c-3c2d-474a-ab15-49a37e22b4a7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a67a16e3fd4868726087df6f2596571d14630f80
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147989"
---
# <a name="idebugapplicationdebugoutput"></a>IDebugApplication::DebugOutput
Faz com que a cadeia de caracteres fornecida a ser exibido pelo ambiente de desenvolvimento integrado (IDE) do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT DebugOutput(  
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
 Esse método permite que um mecanismo de linguagem implementar o suporte à depuração de saída específico do idioma. A cadeia de caracteres normalmente é exibida na janela de saída do depurador.  
  
 Esse método faz com que `IApplicationDebugger::onDebugOutput` a ser chamado.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)