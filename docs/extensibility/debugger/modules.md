---
title: Módulos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 611d067030cd935f6957a976c8a3aa2b7d4f8ae3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925395"
---
# <a name="modules"></a>Módulos
Em termos de arquitetura do depurador, uma *módulo*:

- É um contêiner físico de código, como um arquivo executável ou uma DLL.

- Pode recarregar seus símbolos e descreva a mesmo. Descrições do módulo são exibidas na janela de módulos do IDE.

- É representado por um [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interface, criado por um mecanismo de depuração para descrever o módulo.

## <a name="see-also"></a>Consulte também
- [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)