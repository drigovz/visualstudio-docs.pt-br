---
title: Implementando um fornecedor de porta | Microsoft Docs
description: Saiba mais sobre como implementar um fornecedor de porta, que é necessário ao depurar para um computador não DCOM ou quando um novo dispositivo requer suporte.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8bec31bb49433b7058ca7021091582f89933f0b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947678"
---
# <a name="implement-a-port-supplier"></a>Implementar um fornecedor de porta
Um fornecedor de porta fornece portas na solicitação para o SDM (Gerenciador de depuração de sessão). Um fornecedor de porta deve ser implementado durante a depuração em um computador não DCOM ou quando um novo dispositivo precisar de suporte. Por exemplo, para fornecer depuração para um telefone celular, você pode configurar um fornecedor de porta que fornece portas, que se conectam ao telefone celular (talvez por meio de IR ou uma conexão de célula) e enumeram os processos e programas em execução no telefone.

 Para depurar programas em computadores baseados no Windows (incluindo depuração remota), o Visual Studio fornece fornecedores de porta para processos nativos e CLR (Common Language Runtime), portanto, não é necessário configurar seu próprio fornecedor de porta nesses casos.

## <a name="in-this-section"></a>Nesta seção
 [Implementar e registrar um fornecedor de porta](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) Discute como o SDM interage com o fornecedor da porta e suas portas.

 [Interfaces de fornecedor de porta necessárias](../../extensibility/debugger/required-port-supplier-interfaces.md) Documenta as interfaces que você deve implementar para obter um fornecedor de porta.

## <a name="related-sections"></a>Seções relacionadas
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md) Descreve os principais conceitos de arquitetura da depuração.

## <a name="see-also"></a>Consulte também
 [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
