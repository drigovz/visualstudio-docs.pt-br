---
title: Interface IActiveScriptSiteDebugEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e390b610d6912de0078b817c9dfb503e5924a374
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54797420"
---
# <a name="iactivescriptsitedebugex-interface"></a>Interface IActiveScriptSiteDebugEx

Implementar essa interface junto com o `IActiveScriptSiteDebug` se você estiver escrevendo um host que precisa receber uma notificação de um erro de tempo de execução em um aplicativo e, opcionalmente, anexar ao aplicativo para depuração de interface. O Gerenciador de depuração do processo fornece notificação por meio de `IActiveScriptDebug` se o depurador de scripts um Just-In-Time for encontrado no computador. Se nenhum Just-In-Time de depurador de script é encontrado, o PDM fornece notificação por meio de `IActiveScriptDebugEx` em vez disso.

Para obter uma notificação de um erro de tempo de execução, o host deve tratar `ActiveScriptSiteDebug::OnScriptErrorDebug`. Com base em uma ação do usuário, você pode, em seguida, decidir se deseja anexar o depurador interno e o retorno, ou para retornar o início do depurador no OnScriptErrorDebug `pfEnterDebugger` parâmetro.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable

|Método|Descrição|
|------------|-----------------|
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Informa o host sobre um erro de tempo de execução de script quando o processo de Gerenciador de depuração não encontra um depurador Just In Time externo.|