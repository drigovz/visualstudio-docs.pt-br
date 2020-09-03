---
title: Suspensão automática de recurso | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9c80ba76ba2da978c9cb475299ba0fc9e614120
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655143"
---
# <a name="automatic-feature-suspension"></a>Suspensão automática de recursos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Se a memória do sistema disponível cair em 200 MB ou menos, o Visual Studio exibirá a mensagem a seguir no editor de código.

 ![Texto de alerta suspendendo análise de solução completa](../code-quality/media/fsa-alert.png "FSA_Alert")

 Quando o Visual Studio detecta uma condição de memória insuficiente, ele suspende automaticamente determinados recursos avançados para ajudá-lo a permanecer estável. Quando esse aviso de suspensão de recurso avançado for exibido, o Visual Studio continuará a funcionar como antes, mas seu desempenho será ligeiramente degradado.

 Em uma condição de memória insuficiente, ocorre o seguinte:

- A análise completa da solução para Visual C# e Visual Basic está desabilitada.

- O modo de baixa latência de GC ( [coleta de lixo](https://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9) ) para Visual C# e Visual Basic estão desabilitados.

- Os caches do Visual Studio são liberados.

## <a name="improve-visual-studio-performance"></a>Melhorar o desempenho do Visual Studio
 Para obter dicas e truques sobre como melhorar o desempenho do Visual Studio ao lidar com soluções grandes ou condições de memória insuficiente, consulte [considerações de desempenho para soluções grandes](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Análise de solução completa suspensa
 Por padrão, a análise de solução completa é habilitada para Visual Basic e desabilitada para o Visual C#. No entanto, em uma condição de memória insuficiente, a análise de solução completa é desabilitada automaticamente para o Visual Basic e o Visual C#, independentemente de suas configurações na caixa de diálogo opções. No entanto, você pode reabilitar a análise de solução completa escolhendo o botão **reabilitar** na barra de informações quando ela for exibida, marcando a caixa de seleção **Habilitar análise de solução completa** no diálogo opções ou reiniciando o Visual Studio. A caixa de diálogo opções sempre mostra as configurações de análise de solução completas atuais. Para obter mais informações, consulte [como habilitar e desabilitar a análise completa da solução](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>Baixa latência de GC desabilitada
 Para reabilitar o modo de baixa latência do GC, reinicie o Visual Studio.  Por padrão, o Visual Studio habilita o modo de baixa latência do GC sempre que você está digitando para garantir que a digitação não bloqueie nenhuma operação GC. No entanto, se uma condição de memória insuficiente fizer com que o Visual Studio exiba o aviso de suspensão automática, o modo de baixa latência do GC será desabilitado para essa sessão. Reiniciar o Visual Studio reabilitará o comportamento padrão do GC. Para obter mais informações, consulte <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Caches do Visual Studio liberados

Todos os caches do Visual Studio são imediatamente esvaziados, mas começarão a ser repopulados se você continuar a sessão de desenvolvimento atual ou reiniciar o Visual Studio. Os caches liberados incluem caches para os recursos a seguir.

- Localizar todas as referências

- Navegar para

- Adicionar usando

Além disso, os caches usados para operações internas do Visual Studio também são desmarcados.

> [!NOTE]
> O aviso de suspensão de recurso automático ocorre apenas uma vez por solução, não por sessão. Isso significa que, se você alternar de Visual Basic para Visual C# (ou vice-versa) e executar outra condição de memória insuficiente, poderá obter outro aviso de suspensão de recurso automático.

## <a name="see-also"></a>Confira também

- [Como habilitar e desabilitar a análise de solução completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Noções básicas sobre a coleta de lixo](https://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [Considerações de desempenho para soluções grandes](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)