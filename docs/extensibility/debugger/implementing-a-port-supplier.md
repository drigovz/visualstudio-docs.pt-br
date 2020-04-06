---
title: Implementando um Fornecedor portuário | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8218e372ad3aece922811bc20cfd7650f33296f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738560"
---
# <a name="implement-a-port-supplier"></a>Implementar um fornecedor portuário
Um fornecedor portuário fornece portas a pedido ao gerenciador de depuração de sessão (SDM). Um fornecedor de porta deve ser implementado ao depurar para uma máquina não-DCOM ou quando um novo dispositivo precisar de suporte. Por exemplo, para fornecer depuração a um celular, você pode configurar um fornecedor de portas que forneça portas, que se conectam ao celular (talvez por meio de IR ou uma conexão celular) e enumerar os processos e programas em execução no telefone.

 Para depurar programas em máquinas baseadas no Windows (incluindo depuração remota), o Visual Studio fornece fornecedores de portas para processos nativos e de ClR (Common Language Runtime, tempo de execução de idiomas comuns), portanto não há necessidade de configurar seu próprio fornecedor de portas nesses casos.

## <a name="in-this-section"></a>Nesta seção
 [Implementar e registrar um fornecedor portuário](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) Discute como o SDM interage com o fornecedor portuário e seus portos.

 [Interfaces de fornecedores de portas necessárias](../../extensibility/debugger/required-port-supplier-interfaces.md) Documenta as interfaces que você deve implementar para obter um fornecedor de porta.

## <a name="related-sections"></a>Seções relacionadas
 [Conceitos de depurador](../../extensibility/debugger/debugger-concepts.md) Descreve os principais conceitos arquitetônicos de depuração.

## <a name="see-also"></a>Confira também
 [Extensibilidade do depurador visual studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
