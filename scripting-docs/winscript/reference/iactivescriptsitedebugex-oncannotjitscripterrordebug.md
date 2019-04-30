---
title: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Microsoft Docs
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
ms.openlocfilehash: 4c643478da37b5a66c22b201ef8f8248df02e4ec
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992339"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informa o host sobre um erro de tempo de execução de script quando o processo de Gerenciador de depuração não encontra um depurador de script Just In Time.  
  
 Para implementar um depurador em seu host, você deve tratar [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). Com base em uma ação do usuário, o host pode anexar o depurador e retornar ou retornar o início do depurador no OnScriptErrorDebug `pfEnterDebugger` parâmetro. Você também deve implementar essa interface para receber a notificação sobre o erro de tempo de execução, mesmo se não houver nenhum depuradores externas que podem ser interpretadas pelo Gerenciador de processos de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pErrorDebug`  
 [in] O erro de tempo de execução que ocorreu.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 [out] Se a chamada [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) se o usuário decidir continuar sem depurar.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Você também deve implementar essa interface para receber uma notificação.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSiteDebugEx Interface](../../winscript/reference/iactivescriptsitedebugex-interface.md)