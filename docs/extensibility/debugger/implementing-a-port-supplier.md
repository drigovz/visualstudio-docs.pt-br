---
title: Implementando um fornecedor de porta | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d6875baf72d94494a1abaea9260e344b236f83c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925579"
---
# <a name="implement-a-port-supplier"></a>Implementar um fornecedor de porta
Um fornecedor de porta fornece portas de solicitação para o Gerenciador de sessão de depuração (SDM). Um fornecedor de porta deve ser implementado durante a depuração de uma máquina não-DCOM ou quando um novo dispositivo necessita de suporte. Por exemplo, para fornecer um telefone celular de depuração, você pode configurar um fornecedor de porta que fornece as portas, o qual conectar-se para o telefone celular (talvez por meio do IR ou uma conexão de célula) e enumera os processos e programas em execução no telefone.

 Para depuração de programas em computadores baseados em Windows (incluindo a depuração remota), o Visual Studio fornece os fornecedores de porta para nativo e processos de tempo de execução de linguagem comum (CLR), portanto, não há nenhuma necessidade de configurar seu próprio fornecedor de porta nesses casos.

## <a name="in-this-section"></a>Nesta seção
 [Implementar e registrar um fornecedor de porta](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) discute como o SDM interage com o fornecedor de porta e suas portas.

 [As interfaces de fornecedor porta necessárias](../../extensibility/debugger/required-port-supplier-interfaces.md) documenta as interfaces que você deve implementar para obter um fornecedor de porta.

## <a name="related-sections"></a>Seções relacionadas
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md) descreve os principais conceitos de arquiteturas de depuração.

## <a name="see-also"></a>Consulte também
 [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)