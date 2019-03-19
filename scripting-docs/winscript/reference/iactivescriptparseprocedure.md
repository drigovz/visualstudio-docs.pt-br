---
title: IActiveScriptParseProcedure | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParseProcedure interface
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ed07ce5ed48abfb377dde5fc4d5dc128d881b4a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151343"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Se o mecanismo de Script do Windows permite que o texto do código fonte para obter os procedimentos a serem adicionados ao script, ele implementa o `IActiveScriptParseProcedure` interface. Para linguagens de script interpretadas que não têm nenhum ambiente de criação independente, como o VBScript, isso fornece um mecanismo alternativo (diferente de `IActiveScriptParse` ou `IPersist`*) para adicionar os procedimentos de script ao namespace.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|||  
|-|-|  
|Método|Descrição|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Analisa o procedimento de código fornecido e adiciona o procedimento para o namespace.|  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de script ativo](../../winscript/reference/active-script-interfaces.md)