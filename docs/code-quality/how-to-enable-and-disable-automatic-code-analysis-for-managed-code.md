---
title: Habilitar ou desabilitar a análise de código
ms.date: 10/25/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ec0a8a3f04830115d343fcef611cfbd338163395
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551041"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Como: Habilitar e desabilitar a análise automática de código para código gerenciado

Você pode configurar a análise de código (estático) para ser executada após cada compilação de um projeto de código gerenciado. Você pode definir diferentes propriedades de análise de código para cada configuração de compilação, por exemplo, Debug e Release.

Este artigo se aplica somente à análise herdada e não à análise de código em tempo real usando [analisadores de código](roslyn-analyzers-overview.md).

## <a name="to-enable-or-disable-automatic-code-analysis"></a>Para habilitar ou desabilitar a análise automática de código

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto e escolha **Propriedades**.

1. Na caixa de diálogo Propriedades do projeto, escolha a guia **análise de código** .

   > [!TIP]
   > Os tipos de projeto mais recentes, como .NET Core e .NET Standard aplicativos, não têm uma guia de **análise de código** . A análise herdada não está disponível para esses tipos de projeto, mas você pode obter a análise de código ao vivo usando [analisadores de código baseados em .net Compiler Platform](roslyn-analyzers-overview.md). Para suprimir avisos de analisadores de código, consulte a observação no final deste artigo.

1. Especifique o tipo de compilação na **configuração** e a plataforma de destino na **plataforma**.

1. Para habilitar ou desabilitar a análise automática de código, marque ou desmarque a caixa de seleção **Habilitar análise de código na compilação** .

> [!NOTE]
> A caixa de seleção **Habilitar análise de código na compilação** afeta apenas a análise herdada. Ele não afeta os [analisadores de código baseados em .net Compiler Platform](roslyn-analyzers-overview.md), que sempre são executados no Build se você os instalou como um pacote NuGet. Se você quiser limpar erros do analisador do **lista de erros**, poderá suprimir todas as violações atuais escolhendo **analisar** > **executar análise de código e suprimir problemas ativos** na barra de menus. Para obter mais informações, consulte [suprimir violações](use-roslyn-analyzers.md#suppress-violations).
