---
title: Módulos | Microsoft Docs
description: Este artigo descreve a definição e a função de um módulo na arquitetura do depurador no Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 57202231c1bbfc7712d322b8cc7a30e3f64c87af
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606639"
---
# <a name="modules"></a>Módulos
Em termos da arquitetura do depurador, um *módulo*:

- É um contêiner físico de código, como um arquivo executável ou uma DLL.

- Pode recarregar seus símbolos e se descrever. As descrições de módulo são exibidas na janela módulos do IDE.

- É representado por uma interface [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) , criada por um mecanismo de depuração para descrever o módulo.

## <a name="see-also"></a>Confira também
- [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
