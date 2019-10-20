---
title: Suspensão automática de recursos
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd399d78ac43085d89958ba358954f9e6cefe521
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606533"
---
# <a name="automatic-feature-suspension"></a>Suspensão automática de recursos

Se a memória do sistema disponível cair em 200 MB ou menos, o Visual Studio exibirá a seguinte mensagem no editor de código:

![Texto de alerta suspendendo análise de solução completa](../code-quality/media/fsa_alert.png)

Quando o Visual Studio detecta uma condição de memória insuficiente, ele suspende automaticamente determinados recursos avançados para ajudá-lo a permanecer estável. O Visual Studio continua a funcionar como antes, mas seu desempenho está degradado.

Em uma condição de memória insuficiente, ocorrem as seguintes ações:

- A análise de solução completa C# para Visual e Visual Basic está desabilitada.

- O modo de baixa latência de GC ( [coleta](/dotnet/standard/garbage-collection/index) de lixo C# ) para Visual e Visual Basic está desabilitado.

- Os caches do Visual Studio são liberados.

## <a name="improve-visual-studio-performance"></a>Melhorar o desempenho do Visual Studio

Para obter dicas e truques sobre como melhorar o desempenho do Visual Studio ao lidar com soluções grandes ou condições de memória insuficiente, consulte [considerações de desempenho para soluções grandes](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Análise de solução completa suspensa

Por padrão, a análise de solução completa é habilitada para Visual Basic e C#desabilitada para Visual. No entanto, em uma condição de memória insuficiente, a análise de solução completa é desabilitada automaticamente para Visual Basic e Visual C#, independentemente de suas configurações na caixa de diálogo opções. No entanto, você pode reabilitar a análise de solução completa escolhendo o botão **reabilitar** na barra de informações quando ela for exibida, marcando a caixa de seleção **Habilitar análise de solução completa** no diálogo opções ou reiniciando o Visual Studio. A caixa de diálogo opções sempre mostra as configurações de análise de solução completas atuais. Para obter mais informações, consulte [como habilitar e desabilitar a análise completa da solução](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>Baixa latência de GC desabilitada

Para reabilitar o modo de baixa latência do GC, reinicie o Visual Studio. Por padrão, o Visual Studio habilita o modo de baixa latência do GC sempre que você está digitando para garantir que a digitação não bloqueie nenhuma operação GC. No entanto, se uma condição de memória insuficiente fizer com que o Visual Studio exiba o aviso de suspensão automática, o modo de baixa latência do GC será desabilitado para essa sessão. Reiniciar o Visual Studio habilita novamente o comportamento padrão do GC. Para obter mais informações, consulte <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Caches do Visual Studio liberados

Se você continuar a sessão de desenvolvimento atual ou reiniciar o Visual Studio, todos os caches do Visual Studio serão imediatamente esvaziados, mas começarão a ser repopulados. Os caches liberados incluem caches para os seguintes recursos:

- Localizar todas as referências

- Navegar para

- Adicionar usando

Além disso, os caches usados para operações internas do Visual Studio também são desmarcados.

> [!NOTE]
> O aviso de suspensão de recurso automático ocorre apenas uma vez por solução, não por sessão. Isso significa que, se você alternar de Visual Basic para C# Visual (ou vice-versa) e executar outra condição de memória insuficiente, poderá obter outro aviso de suspensão de recurso automático.

## <a name="see-also"></a>Consulte também

- [Como habilitar e desabilitar a análise de solução completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Conceitos básicos da coleta de lixo](/dotnet/standard/garbage-collection/fundamentals)
- [Considerações de desempenho para soluções grandes](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
