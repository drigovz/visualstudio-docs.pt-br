---
title: IActiveScriptErrorDebug Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug interface
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 936770859d3bdfe81c84245d32ae63346b142a01
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009526"
---
# <a name="iactivescripterrordebug-interface"></a>Interface IActiveScriptErrorDebug
Fornece informações de contexto de documento para erros de tempo de compilação e exceções de tempo de execução. O `IActiveScriptError::QueryInterface` método suporta a `IActiveScriptErrorDebug` interface.  
  
 Além dos métodos herdados de `IActiveScriptError`, o `IActiveScriptErrorDebug` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|Fornece o contexto de documento para esse erro.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|Fornece o registro de ativação está em vigor para erros de tempo de execução.|