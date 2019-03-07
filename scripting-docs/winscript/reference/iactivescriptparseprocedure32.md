---
title: IActiveScriptParseProcedure32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 10cdff328216d06a3326dd3595ef8fc78bc9cfc9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348107"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Se o mecanismo de Script do Windows permite que o texto do código fonte para obter os procedimentos a serem adicionados ao script, ele implementa o `IActiveScriptParseProcedure32` interface. Para linguagens de script interpretadas que não têm nenhum ambiente de criação independente, como o VBScript, isso fornece um mecanismo alternativo (diferente de `IActiveScriptParse32` ou `IPersist`*) para adicionar os procedimentos de script ao namespace.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|||  
|-|-|  
|Método|Descrição|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Analisa o procedimento de código fornecido e adiciona o procedimento para o namespace.|  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de script ativo](../../winscript/reference/active-script-interfaces.md)