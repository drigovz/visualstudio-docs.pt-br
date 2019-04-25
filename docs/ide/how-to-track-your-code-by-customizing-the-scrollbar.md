---
title: Modo de mapa e modo de barra da barra de rolagem
ms.date: 09/25/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77f7db396b814eb9163c055b8fadb8793432acee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548256"
---
# <a name="how-to-customize-the-scroll-bar"></a>Como: Personalizar a barra de rolagem

Quando se trabalha com longos arquivos de código, às vezes torna-se difícil manter o controle de onde está tudo no arquivo. É possível personalizar a barra de rolagem do editor de código para ter um panorama geral do que está acontecendo no código.

## <a name="annotations"></a>Anotações

Você pode selecionar se a barra de rolagem deve mostrar anotações, como alterações de código, pontos de interrupção, indicadores, erros e posição do cursor.

   1. Abra a página de opções **Barras de rolagem** escolhendo **Ferramentas** > **Opções** > **Editor de Texto** > **Todos os Idiomas** > **Barras de rolagem**.

   2. Selecione **Mostrar anotações sobre a barra de rolagem vertical** e selecione as anotações que deseja ver. As anotações disponíveis são:

      - alterações
      - marcas
      - erros
      - posição do cursor

      > [!TIP]
      > A opção **Exibir marcas** inclui pontos de interrupção e indicadores.

Experimente abrir um arquivo de código grande e substituir algumas partes do texto que ocorrem em vários locais no arquivo. A barra de rolagem mostra o efeito das substituições, de modo que você pode desfazer suas alterações se tiver substituído algo que não deveria.

Esta é a aparência da barra de rolagem após o usuário pesquisar por uma cadeia de caracteres. Observe que todas as instâncias da cadeia de caracteres são exibidas na barra de rolagem.

![A barra de rolagem do Visual Studio após a pesquisa de uma cadeia de caracteres](../ide/media/enhancedscrollbarsearch.png)

Esta é a barra de rolagem após a substituição de todas as instâncias da cadeia de caracteres. As marcas vermelhas na barra de rolagem mostram em que local a substituição de texto introduziu erros.

![A barra de rolagem do Visual Studio depois da substituição de uma cadeia de caracteres com erros](../ide/media/enhancedscrollbarreplace.png)

## <a name="display-modes"></a>Modos de exibição

A barra de rolagem tem dois modos: o modo de barra e o modo de mapa.

### <a name="bar-mode"></a>Modo de barra

O *modo de barra* exibe indicadores de anotação na barra de rolagem. Clicar na barra de rolagem rola a página para cima ou para baixo, mas não avança para aquele local no arquivo.

### <a name="map-mode"></a>Modo de mapa

No *modo de mapa*, quando você clica em um local na barra de rolagem, o cursor avança para aquele local no arquivo em vez de simplesmente rolar para cima ou para baixo em uma página. As linhas de código são mostradas em miniatura na barra de rolagem. É possível escolher a largura da coluna do mapa selecionando um valor em **Visão geral do Código-fonte**. Para habilitar uma visualização maior do código quando você parar o ponteiro no mapa, selecione a opção **Mostrar Dica de Ferramenta de Visualização**. As regiões recolhidas ficam sombreadas de forma diferente e são expandidas quando você clica duas vezes nelas.

> [!TIP]
> Você pode desabilitar a exibição de código em miniatura no modo de mapa definindo a opção **Visão geral do código-fonte** como **Desabilitada**. Se a opção **Mostrar dica de ferramenta de visualização** estiver selecionada, você ainda verá uma visualização do código nesse local ao passar o ponteiro do mouse sobre a barra de rolagem, e o cursor ainda avançará para esse local no arquivo quando você clicar.

A imagem a seguir mostra o exemplo de pesquisa quando o modo de mapa está ativado e a largura está definida como **Média**:

![Barra de rolagem do Visual Studio no modo de mapa](../ide/media/enhancedscrollbar.png)

A imagem a seguir mostra a opção **Mostrar dica de ferramenta de visualização**:

![Barra de rolagem do Visual Studio com uma dica de ferramenta](../ide/media/enhancedscrollbarsearchtooltip.png)

## <a name="see-also"></a>Consulte também

- [Recursos do Editor de Códigos](../ide/writing-code-in-the-code-and-text-editor.md)