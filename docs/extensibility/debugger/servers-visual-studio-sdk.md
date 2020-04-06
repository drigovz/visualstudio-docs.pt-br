---
title: Servidores (Visual Studio SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32fdbb5afca40c3b4fced468d2f9ef0ea5226c00
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712890"
---
# <a name="servers-visual-studio-sdk"></a>Servidores (SDK do Visual Studio)
Na arquitetura dedepurador, um *servidor:*

- É um contêiner de portos e fornecedores portuários e comunica portos e fornecedores portuários para o gerenciador de depuração de sessão (SDM) e motores de depuração.

- Pode identificar-se pelo nome e enumerar seus portos e fornecedores portuários.

- É representado por uma interface [IDebugCoreServer2,](../../extensibility/debugger/reference/idebugcoreserver2.md) que só é implementada pelo Visual Studio (uma instância de um servidor para cada instância do Visual Studio em execução).

## <a name="see-also"></a>Confira também
- [Portas](../../extensibility/debugger/ports.md)
- [Fornecedores portuários](../../extensibility/debugger/port-suppliers.md)
- [Conceitos de depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
