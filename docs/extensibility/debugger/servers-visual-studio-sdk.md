---
title: Servidores (Visual Studio SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56ec28d0d9202bfd72d31e95c53038dd1fa475e9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111773"
---
# <a name="servers-visual-studio-sdk"></a>Servidores (SDK do Visual Studio)
Na arquitetura do depurador, uma *server*:

- É um contêiner de portas e os fornecedores de porta e comunica as portas e fornecedores de porta para o Gerenciador de sessão de depuração (SDM) e mecanismos de depuração.

- Pode identificar-se por nome e enumerar suas portas e os fornecedores de porta.

- É representado por um [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interface, que só é implementada pelo Visual Studio (uma instância de um servidor para cada instância de execução do Visual Studio).

## <a name="see-also"></a>Consulte também
- [Portas](../../extensibility/debugger/ports.md)
- [Fornecedores de porta](../../extensibility/debugger/port-suppliers.md)
- [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)