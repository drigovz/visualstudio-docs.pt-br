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
ms.openlocfilehash: a987b4be3430f2ed8b0562f41b51a94797f96dc4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009332"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Se o Script do Windows mecanismo permite miniscripts de código de texto bruto a ser adicionado ao script ou permite que o texto da expressão a ser avaliada em tempo de execução, ele implementa o `IActiveScriptParse` interface. Para linguagens de script interpretadas que não têm nenhum ambiente de criação independente, como o VBScript, isso fornece um mecanismo alternativo (diferente de `IPersist*`) para obter o código de script no mecanismo de script e para anexar os fragmentos de script ao objeto de vários eventos.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Inicializa o mecanismo de script.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Adiciona um scriptlet de código ao script.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analisa o scriptlet de código fornecido, adicionando declarações para o espaço de nome e avaliar o código conforme apropriado.|  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de script ativo](../../winscript/reference/active-script-interfaces.md)