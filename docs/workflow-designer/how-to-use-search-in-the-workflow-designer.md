---
title: 'Como: Usar a pesquisa no Designer de Fluxo de Trabalho'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 0a80bfecaa288eabc0161d0262535a7912411f78
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949560"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Como: Usar a pesquisa no Designer de Fluxo de Trabalho

Para facilitar a criação de fluxos de trabalho maiores e mais complexos, você pode pesquisar dentro do Designer de fluxo de trabalho para localizar itens por palavra-chave. Observe que o designer não suporta substitui.

## <a name="quick-find"></a>Localização Rápida

Localização rápida localiza o seguinte no designer:

- Propriedades de objetos de <xref:System.Activities.Activity> , de objetos, <xref:System.Activities.Statements.FlowNode> de objetos <xref:System.Activities.Statements.State> , das transições, e outros itens personalizados de controle de fluxo.

- Variáveis

- Arguments

- Expressões

### <a name="use-quick-find"></a>Usar a localização rápida

1. Com o designer de fluxo de trabalho aberto, pressione **Ctrl + F**, ou selecione **editar** > **localizar e substituir** > **localização rápida**.

2. Insira o termo de pesquisa para o **localizar** caixa de texto e clique em **Localizar próximo**.

3. O termo de pesquisa está localizado no fluxo de trabalho atual. A imagem a seguir mostra um nome de exibição de atividade que está sendo localizado no designer:

   ![Resultado de pesquisa no designer de fluxo de trabalho](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Localizar nos arquivos

Localizar em arquivos localiza cadeias de caracteres em arquivos de fluxo de trabalho, incluindo arquivos XAML.

### <a name="use-find-in-files"></a>Usar Localizar em arquivos

1. No Visual Studio, pressione **Ctrl**+**Shift**+**F**, ou selecione **editar**  >   **Localizar e substituir** > **localizar nos arquivos**.

2. Inserir o item de pesquisa para o **localizar** caixa de texto e clique em **Localizar tudo**.

3. O resultado de alterações é mostrado na **localizar o resultado** modo de exibição. Clicar duas vezes em um item de resultado navegará para a atividade que contém a correspondência no designer de fluxo de trabalho.