---
title: Módulos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: abdf76c7f5f031d2ef7f3bcac2bae8a2c508b783
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738352"
---
# <a name="modules"></a>Módulos
Em termos da arquitetura de depurador, um *módulo:*

- É um recipiente físico de código, como um arquivo executável ou um DLL.

- Pode recarregar seus símbolos e descrever a si mesmo. As descrições dos módulos são exibidas na janela Módulos do IDE.

- É representado por uma interface [IDebugModule2,](../../extensibility/debugger/reference/idebugmodule2.md) criada por um mecanismo de depuração para descrever o módulo.

## <a name="see-also"></a>Confira também
- [Conceitos de depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
