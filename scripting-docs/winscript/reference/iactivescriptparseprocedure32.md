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
ms.openlocfilehash: 1993cbef966a4d73a2a3ed55c3317db444702232
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574869"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Se o mecanismo de script do Windows permitir que o texto do código-fonte de procedimentos seja adicionado ao script, ele implementará a interface `IActiveScriptParseProcedure32`. Para linguagens de script interpretadas que não têm um ambiente de criação independente, como o VBScript, isso fornece um mecanismo alternativo (diferente de `IActiveScriptParse32` ou `IPersist` *) para adicionar procedimentos de script ao namespace.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
  
|||  
|-|-|  
|Método|Descrição|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Analisa o procedimento de código fornecido e adiciona o procedimento ao namespace.|  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de script ativo](../../winscript/reference/active-script-interfaces.md)