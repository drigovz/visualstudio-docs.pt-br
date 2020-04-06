---
title: Fornecedores Portuários | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6313a7afce9ed272177a26d8da1a9d1516c8022e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738302"
---
# <a name="port-suppliers"></a>Fornecedores portuários
Na arquitetura dedepurador, um *fornecedor de portas:*

- É contido por um servidor e fornece portas mediante solicitação a esse servidor.

- Pode adicionar e remover portas do servidor de contenção.

- Pode enumerar todas as portas que forneceu ao servidor.

- É representado por uma interface [IDebugPortSupplier2,](../../extensibility/debugger/reference/idebugportsupplier2.md) que é registrada no Visual Studio através do registro. Esta interface pode ser obtida ligando para [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornece um fornecedor de porta padrão e uma porta padrão. Se uma porta personalizada precisar ser implementada, um fornecedor de porto personalizado também precisa ser implementado para fornecer essas portas personalizadas.

## <a name="see-also"></a>Confira também
- [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Portas](../../extensibility/debugger/ports.md)
- [Conceitos de depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
