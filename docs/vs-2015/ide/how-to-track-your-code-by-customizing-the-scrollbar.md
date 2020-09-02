---
title: Como acompanhar o código personalizando a barra de rolagem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a9ebe7ec-4b6f-4ba2-a79e-80fab3db485b
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a852b0e5ac6c6a677caab97279a0b0cb0299d27f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670633"
---
# <a name="how-to-track-your-code-by-customizing-the-scrollbar"></a>Como acompanhar o código personalizando a barra de rolagem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando você está trabalhando com arquivos de código longo, pode ser difícil manter controle de tudo. Você pode personalizar a barra de rolagem da janela de código para ter um panorama geral do que está acontecendo em seu código.

### <a name="to-show-annotations-on-the-scroll-bar"></a>Para mostrar anotações na barra de rolagem

1. É possível configurar a barra de rolagem para mostrar alterações de código, pontos de interrupção, erros e indicadores.

     Abra a página Opções da **barra de rolagem** (**ferramentas, editor de texto de opções. Todos os idiomas** ou um idioma específico ou uma  **barra de rolagem** de tipo na janela inicialização rápida).

2. Selecione **Mostrar anotações sobre a barra de rolagem vertical** e selecione as anotações que deseja ver. (A opção **Marks** inclui pontos de interrupção e indicadores.)

3. Agora experimente. Abra um arquivo de código grande e substitua algo que ocorra em vários lugares no arquivo. A barra de rolagem mostra o efeito das substituições, de modo que você pode desfazer suas alterações se tiver substituído algo que não deveria.

     Esta é a aparência da barra de rolagem após o usuário pesquisar por uma cadeia de caracteres. Observe que todas as instâncias da cadeia de caracteres são exibidas.

     ![A barra de rolagem após pesquisar uma cadeia de caracteres.](../ide/media/enhancedscrollbarsearch.png "EnhancedScrollbarSearch")

     Esta é a barra de rolagem após a substituição de todas as instâncias da cadeia de caracteres. Você pode ver imediatamente que a operação causou alguns problemas.

     ![A barra de rolagem após a substituição de uma cadeia de caracteres com erros](../ide/media/enhancedscrollbarreplace.png "EnhancedScrollbarReplace")

### <a name="to-set-the-display-mode-for-the-scroll-bar"></a>Para definir o modo de exibição para a barra de rolagem

1. A barra de rolagem tem dois modos, o modo de barra (padrão) e o modo de mapa. O modo de barra exibe apenas indicadores de anotação na barra de rolagem. No modo de mapa, as linhas de código são representadas na barra de rolagem. Você pode escolher sua largura e se elas mostram o código subjacente quando você posiciona o ponteiro sobre elas. Quando você clica em um local na barra de rolagem, o cursor se move para esse local no código. Regiões recolhidas são sombreadas de forma diferente; elas são expandidas quando você clica duas vezes nelas.

     Na página de opções **Barra de Rolagem**, selecione **Usar modo de barra para barra de rolagem vertical** ou **Usar modo de mapa para barra de rolagem vertical**. Você pode escolher a largura no menu suspenso **visão geral da origem** .

     Veja qual é a aparência do exemplo de pesquisa quando o modo de mapa está ativado e a largura está definida como Médio:

     ![A barra de rolagem no modo de mapa](../ide/media/enhancedscrollbar.png "EnhancedScrollbar")

2. No modo de mapa, para habilitar visualizações do código quando você move o cursor para cima e para baixo na barra de rolagem, selecione a opção **Mostrar Dica de Ferramenta de Visualização**. A aparência é a seguinte:

     ![A barra de rolagem com uma dica de ferramenta](../ide/media/enhancedscrollbarsearchtooltip.png "EnhancedScrollbarSearchTooltip")

     Se quiser manter o comportamento de rolagem do modo de mapa e a dica de ferramenta de visualização, mas não quiser ter a visão de geral do código-fonte, você pode definir **Visualização do código-fonte** como **Desativado**.
