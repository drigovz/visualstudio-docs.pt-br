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
ms.openlocfilehash: 7a2b2f04e1088b9b06cb05015a6b0b4da5d60927
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153744"
---
# <a name="modules"></a>Módulos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Em termos da arquitetura do depurador, um **módulo**:  
  
- É um contêiner físico de código, como um arquivo executável ou uma DLL.  
  
- Pode recarregar seus símbolos e se descrever. As descrições de módulo são exibidas na janela módulos do IDE.  
  
- É representado por uma interface [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) , criada por um mecanismo de depuração para descrever o módulo.  
  
## <a name="see-also"></a>Consulte Também  
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
