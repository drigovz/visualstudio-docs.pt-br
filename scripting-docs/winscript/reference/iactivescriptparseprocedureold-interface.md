---
title: IActiveScriptParseProcedureOld Interface | Microsoft Docs
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
ms.openlocfilehash: 99fa06086bfad56b266b043716e82181aa4c97d5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160622"
---
# <a name="iactivescriptparseprocedureold-interface"></a>Interface IActiveScriptParseProcedureOld
Permite que o texto do código fonte para obter os procedimentos a serem adicionados ao script. Para linguagens de script interpretadas que não têm um ambiente de criação independente, como o VBScript, isso fornece um mecanismo alternativo (diferente de `IActiveScriptParse` ou `IPersist*`) para adicionar os procedimentos de script para o espaço para nome.  
  
> [!NOTE]
>  Essa interface é preterida em favor do `IActiveScriptParseProcedure` interface.  
  
## <a name="methods"></a>Métodos  
 Além dos métodos herdados de `IUnknown`, o `IActiveScriptParseProcedureOld` interface expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analisa o procedimento de código fornecido e adiciona o procedimento para o espaço para nome.|  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)