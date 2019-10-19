---
title: 'IActiveScriptSiteDebugEx:: OnCanNotJITScriptErrorDebug | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7358d2b372f0801b8c45816e1fc36018b37799b2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572185"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informa o host sobre um erro de tempo de execução de script quando o Gerenciador de depuração de processo não encontra um depurador de script just in time.  
  
 Para implementar um depurador em seu host, você deve tratar [IActiveScriptSiteDebug:: OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). Com base em uma ação do usuário, o host pode anexar o depurador e retornar ou retornar o início do depurador no parâmetro OnScriptErrorDebug `pfEnterDebugger`. Você também deve implementar essa interface para obter a notificação sobre o erro de tempo de execução, mesmo que não haja nenhum depurador externo que possa ser interpretado pelo Gerenciador de depuração de processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pErrorDebug`  
 no O erro de tempo de execução que ocorreu.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 fora Se deve chamar [IActiveScriptSiteDebug:: OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) se o usuário decidir continuar sem depuração.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Você também deve implementar essa interface para obter uma notificação.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSiteDebugEx Interface](../../winscript/reference/iactivescriptsitedebugex-interface.md)