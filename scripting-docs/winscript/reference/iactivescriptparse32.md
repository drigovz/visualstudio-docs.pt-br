---
title: IActiveScriptParse32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9f44239b4e423588b8455b93b87e4084a9c7d1c4
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347639"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Se o Script do Windows mecanismo permite miniscripts de código de texto bruto a ser adicionado ao script ou permite que o texto da expressão a ser avaliada em tempo de execução, ele implementa o `IActiveScriptParse32` interface. Para linguagens de script interpretadas que não têm nenhum ambiente de criação independente, como o VBScript, isso fornece um mecanismo alternativo (diferente de `IPersist*`) para obter o código de script no mecanismo de script e para anexar os fragmentos de script ao objeto de vários eventos.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Adiciona um scriptlet de código ao script.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Inicializa o mecanismo de script.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Analisa o scriptlet de código fornecido, adicionando declarações para o espaço de nome e avaliar o código conforme apropriado.|