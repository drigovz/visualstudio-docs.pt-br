---
title: Tarefas de depuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d41f53ab1392ea3c31908faf65a871fa100fbb3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738961"
---
# <a name="debug-tasks"></a>Tarefas de depuração
Para depurar um programa, ele deve ser lançado e um motor de depuração (DE) deve ser anexado a ele, ou então o DE deve ser anexado a um programa lançado anteriormente. Uma vez anexado, o DE deve gerar certos eventos de inicialização. Em resposta, o pacote de depuração tenta vincular os pontos de interrupção definidos no IDE. Quando o programa atinge um ponto de interrupção vinculado, ele pára e espera pela entrada do usuário.

## <a name="in-this-section"></a>Nesta seção
 [Problemas de segurança](../../extensibility/debugger/security-issues.md) Discute as etapas de segurança necessárias para depurar um programa.

 [Lançar um programa](../../extensibility/debugger/launching-a-program.md) Fornece instruções passo-a-passo sobre como especificar um DE, que chama o sistema operacional para iniciar o programa.

 [Anexar diretamente a um programa](../../extensibility/debugger/attaching-directly-to-a-program.md) Descreve o processo usado para depurar um programa em um processo que já está sendo executado.

 [Envie eventos de startup após um lançamento](../../extensibility/debugger/sending-startup-events-after-a-launch.md) Lista os eventos que ocorrem uma vez que o DE é anexado ao programa, até que o programa esteja em seu ponto de entrada principal e esteja pronto para depuração.

 [Controle da execução](../../extensibility/debugger/control-of-execution.md) Explica como o DE normalmente envia um evento de ponto de entrada, um evento completo de carga ou um evento de parada, dependendo das circunstâncias.

 [Pontos de interrupção de vinculação](../../extensibility/debugger/binding-breakpoints.md) Descreve como, se o usuário define um ponto de ruptura, o IDE formula a solicitação e solicita a sessão de depuração para criar o ponto de ruptura.

 [Avaliar expressões](../../extensibility/debugger/evaluating-expressions.md) Explica como as expressões são criadas e o que acontece quando uma expressão é avaliada.

 [Visualize e visualize dados](../../extensibility/debugger/visualizing-and-viewing-data.md) Explica como visualizadores de tipo e visualizadores personalizados são suportados pelo avaliador de expressão (EE).

## <a name="related-sections"></a>Seções relacionadas
 [Conceitos de depurador](../../extensibility/debugger/debugger-concepts.md) Descreve os principais conceitos arquitetônicos de depuração.

 [Componentes do depurador](../../extensibility/debugger/debugger-components.md) Fornece uma visão geral dos componentes de depuração do Visual Studio, que incluem o DE, EE e o manipulador de símbolos (SH).

 [Contextos de depuração](../../extensibility/debugger/debugger-contexts.md) Explica como o DE opera simultaneamente dentro de contextos de avaliação de código, documentação e expressão. Descreve, para cada um dos três contextos, a localização, posição ou avaliação relevantes para ele.

## <a name="see-also"></a>Confira também
 [Introdução](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
