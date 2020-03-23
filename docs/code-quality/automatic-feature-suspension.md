---
title: Suspensão automática de recursos
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8480eb57a08905c2a593adbab519ae793638888
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431235"
---
# <a name="automatic-feature-suspension"></a>Suspensão automática de recursos

Se a memória disponível do sistema cair para 200 MB ou menos, o Visual Studio exibirá a seguinte mensagem no editor de código:

![Texto de alerta suspendendo análise completa da solução](../code-quality/media/fsa_alert.png)

Quando o Visual Studio detecta uma condição de memória baixa, ele suspende automaticamente certos recursos avançados para ajudá-lo a permanecer estável. Visual Studio continua a funcionar como antes, mas sua performance está degradada.

Em uma condição de memória baixa, as seguintes ações ocorrem:

- A análise de código ao vivo para Visual C# e Visual Basic é reduzida a um escopo mínimo.

- [O](/dotnet/standard/garbage-collection/index) modo de baixa latência da Coleta de Lixo (GC) para visual C# e Visual Basic está desativado.

- Os caches do Visual Studio estão liberados.

## <a name="improve-visual-studio-performance"></a>Melhorar o desempenho do Visual Studio

Para obter dicas e truques sobre como melhorar o desempenho do Visual Studio ao lidar com grandes soluções ou condições de baixa memória, consulte [considerações de desempenho para grandes soluções](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>A análise de código ao vivo é reduzida a um escopo mínimo

Por padrão, a análise de código vivo é executada para documentos e projetos abertos. Você pode personalizar este escopo de análise para ser reduzido ao documento atual ou aumentado para toda a solução. Para obter mais informações, [consulte Como: Configurar o escopo de análise de código ao vivo para código gerenciado](./configure-live-code-analysis-scope-managed-code.md). Em uma condição de memória baixa, o Visual Studio força que o escopo de análise ao vivo seja reduzido ao documento atual. No entanto, você pode reativar seu escopo de análise preferido escolhendo o botão **Reativar** na barra de informações quando ele aparecer ou reiniciar o Visual Studio. A caixa de diálogo Opções sempre mostra as configurações atuais do escopo de análise de código ao vivo.

## <a name="gc-low-latency-disabled"></a>GC de baixa latência desativado

Para reativar o modo de baixa latência GC, reinicie o Visual Studio. Por padrão, o Visual Studio habilita o modo de baixa latência GC sempre que você estiver digitando para garantir que sua digitação não bloqueie nenhuma operação de GC. No entanto, se uma condição de memória baixa fizer com que o Visual Studio exiba o aviso de suspensão automática, o modo de baixa latência GC será desativado para essa sessão. Reiniciar o Visual Studio reativa o comportamento padrão do GC. Para obter mais informações, consulte <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Caches do Visual Studio lavados

Se você continuar sua sessão de desenvolvimento atual ou reiniciar o Visual Studio, todos os caches do Visual Studio serão imediatamente esvaziados, mas começarão a repovoar. Os caches lavados incluem caches para os seguintes recursos:

- Localizar todas as referências

- Navegar para

- Adicionar usando

Além disso, os caches usados para operações internas do Visual Studio também são limpos.

> [!NOTE]
> O aviso automático de suspensão do recurso ocorre apenas uma vez por solução, não por sessão. Isso significa que se você mudar de Visual Basic para Visual C# (ou vice-versa) e correr para outra condição de memória baixa, você pode possivelmente obter outro aviso automático de suspensão de recurso.

## <a name="see-also"></a>Confira também

- [Como: Configurar o escopo de análise de código ao vivo para código gerenciado](./configure-live-code-analysis-scope-managed-code.md)
- [Noções básicas sobre a coleta de lixo](/dotnet/standard/garbage-collection/fundamentals)
- [Considerações de desempenho para grandes soluções](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
