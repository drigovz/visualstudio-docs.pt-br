---
title: IActiveScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 340a76dbb6d81c78463fa644dafcbe8097508561
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346703"
---
# <a name="iactivescript"></a>IActiveScript
Fornece os métodos necessários para inicializar o mecanismo de script. O mecanismo de script deve implementar o `IActiveScript` interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Informa ao mecanismo de script da [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) site fornecido pelo host.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Recupera o objeto de site associado com o mecanismo de Script do Windows.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Coloca o mecanismo de script no estado especificado.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Recupera o estado atual do mecanismo de script.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Faz com que o mecanismo de script abandonar a qualquer script carregado no momento, perder seu estado e liberar quaisquer ponteiros de interface, que ele tem a outros objetos, portanto, inserindo um estado fechado.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Adiciona o nome de um item de nível raiz para o namespace do mecanismo de script.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Adiciona uma biblioteca de tipos para o namespace para o script.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Recupera o `IDispatch` interface para o script em execução.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Recupera um identificador de script-mecanismo-definidas para o thread em execução no momento.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Recupera um identificador de script-mecanismo-definidas para o thread associado o determinado thread do Microsoft Win32.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Recupera o estado atual de um thread de script.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Interrompe a execução de um thread em execução do script.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Clona o mecanismo de script atual (menos qualquer estado de execução atual), retornando um mecanismo de script carregado com nenhum site no thread atual.|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de interfaces de script do Windows](../../winscript/reference/windows-script-interfaces-reference.md)