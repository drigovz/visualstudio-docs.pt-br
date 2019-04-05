---
title: Módulos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 802a40c248df243adf1319c522278ad94d69eeed
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58923870"
---
# <a name="modules"></a>Módulos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Em termos de arquitetura do depurador, uma **módulo**:  
  
-   É um contêiner físico de código, como um arquivo executável ou uma DLL.  
  
-   Pode recarregar seus símbolos e descreva a mesmo. Descrições do módulo são exibidas na janela de módulos do IDE.  
  
-   É representado por um [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interface, criado por um mecanismo de depuração para descrever o módulo.  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
