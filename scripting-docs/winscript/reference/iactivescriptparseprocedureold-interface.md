---
title: Interface IActiveScriptParseProcedureOld | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4558a0cab2aea9b56db2759bb80b1287cd33ce87
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571431"
---
# <a name="iactivescriptparseprocedureold-interface"></a>Interface IActiveScriptParseProcedureOld
Permite que o texto do código-fonte de procedimentos seja adicionado ao script. Para linguagens de script interpretadas que não têm um ambiente de criação independente, como o VBScript, isso fornece um mecanismo alternativo (diferente de `IActiveScriptParse` ou `IPersist*`) para adicionar procedimentos de script ao espaço de nome.  
  
> [!NOTE]
> Essa interface foi preterida em favor da interface `IActiveScriptParseProcedure`.  
  
## <a name="methods"></a>Métodos  
 Além dos métodos herdados de `IUnknown`, a interface `IActiveScriptParseProcedureOld` expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analisa o procedimento de código fornecido e adiciona o procedimento ao espaço de nome.|  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)