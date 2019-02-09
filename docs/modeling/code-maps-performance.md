---
title: Mapas de código estão lentos
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f53376d1cff79dd69b7fb17704c4ddae8803c46
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913178"
---
# <a name="improve-performance-for-code-maps"></a>Melhorar o desempenho de mapas de código

Quando você gera um mapa pela primeira vez, o Visual Studio indexa todas as dependências que encontra. Esse processo pode levar algum tempo, especialmente para grandes soluções, mas melhora o desempenho posterior. Se o código for alterado, o Visual Studio só reindexará o código atualizado. Para minimizar o tempo necessário para o mapa concluir a renderização, considere as seguintes sugestões:

- [Mapear as dependências que lhe interessam.](#create-a-code-map-to-see-specific-dependencies)

- Antes de gerar o mapa para uma solução inteira, reduza o escopo da solução.

- Desativar a compilação automática para a solução selecionando **Skip Build** na barra de ferramentas de mapa de código.

- Desativar a adição automática de itens de pai, selecionando **pais incluem** na barra de ferramentas de mapa de código.

   ![Ignorar o Build e pais incluem botões](../modeling/media/codemapsfilterskipbuildicons.png)

- Edite o arquivo de mapa de código diretamente para remover os nós e links que você não precisa. Alterar o mapeamento não afeta o código subjacente. Consulte [Personalizar mapa de códigos editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Pode levar mais tempo para criar mapas ou adicionar itens a um mapa de **Gerenciador de soluções** quando um item de projeto **Copy to Output Directory** estiver definida como **copiar sempre**. Para aumentar o desempenho, altere essa propriedade para **copiar se mais recente** ou `PreserveNewest`. Ver [compilações incrementais](../msbuild/incremental-builds.md).

O mapa concluído mostra dependências apenas para código compilado com êxito. Se ocorrerem erros de compilação para determinados componentes, esses erros são exibidos no mapa. Certifique-se de que um componente é efetivamente compilado e tem dependências nele antes de tomar decisões arquitetônicas com base no mapa.