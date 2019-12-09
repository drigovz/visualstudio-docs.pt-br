---
title: IActiveScriptParse | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParse interface
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81f64352c15dce233058d49b70e35da7e2238688
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561644"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Se o mecanismo de script do Windows permitir que o código de texto bruto de scriptlets seja adicionado ao script ou permitir que o texto da expressão seja avaliado em tempo de execução, ele implementará a interface `IActiveScriptParse`. Para linguagens de script interpretadas que não têm um ambiente de criação independente, como o VBScript, isso fornece um mecanismo alternativo (diferente de `IPersist*`) para obter o código de script no mecanismo de script e anexar fragmentos de script a vários eventos de objeto .  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Inicializa o mecanismo de script.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Adiciona um Scriptlet de código ao script.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analisa o scriptlet de código fornecido, adicionando declarações ao espaço de nome e avaliando o código conforme apropriado.|  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de script ativo](../../winscript/reference/active-script-interfaces.md)