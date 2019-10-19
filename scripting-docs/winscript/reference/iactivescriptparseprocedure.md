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
ms.openlocfilehash: c20947a125766547565d99c5762c20e23652da1a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561674"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Se o mecanismo de script do Windows permitir que o texto do código-fonte de procedimentos seja adicionado ao script, ele implementará a interface `IActiveScriptParseProcedure`. Para linguagens de script interpretadas que não têm um ambiente de criação independente, como o VBScript, isso fornece um mecanismo alternativo (diferente de `IActiveScriptParse` ou `IPersist` *) para adicionar procedimentos de script ao namespace.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
  
|||  
|-|-|  
|Método|Descrição|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Analisa o procedimento de código fornecido e adiciona o procedimento ao namespace.|  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de script ativo](../../winscript/reference/active-script-interfaces.md)