---
title: Fornecedores de porta | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8074bedf411b99997ddb93a16f4acbf72e63114b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889369"
---
# <a name="port-suppliers"></a>Fornecedores de porta
Na arquitetura do depurador, uma *fornecedor de porta*:

- Está contido por um servidor e fornece as portas na solicitação para esse servidor.

- Adicione e remova as portas do servidor que contém.

- Pode enumerar todas as portas que ele tenha fornecido para o servidor.

- É representado por um [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interface, que está registrado com o Visual Studio por meio do registro. Essa interface pode ser obtida chamando [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Fornece um fornecedor de porta padrão e uma porta padrão. Se uma porta personalizada precisa ser implementado, um fornecedor de porta personalizado também precisa ser implementada para fornecer essas portas personalizadas.

## <a name="see-also"></a>Consulte também
- [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Portas](../../extensibility/debugger/ports.md)
- [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)