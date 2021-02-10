---
title: Dicas de acessibilidade e truques do Visual Studio
description: Saiba mais sobre dicas e truques que podem ajudar a tornar o uso do IDE (ambiente de desenvolvimento integrado) do Visual Studio mais acessível para todos, incluindo pessoas com deficiências.
ms.date: 08/06/2019
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59206c206f04aaf3506771ee2310daebd0af273a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939741"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Dicas de acessibilidade e truques do Visual Studio

O Visual Studio tem recursos internos de acessibilidade que são compatíveis com leitores de tela e outras tecnologias assistenciais. Se você quiser usar atalhos de teclado para navegar na IDE ou temas de alto contraste para melhorar a visibilidade, encontrará várias dicas e truques a respeito disso nesta página.

Também mostramos como usar anotações para revelar informações úteis sobre o código e como configurar indicações de som para eventos de build e de ponto de interrupção.

> [!NOTE]
> Este tópico aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Acessibilidade do Visual Studio para Mac](/visualstudio/mac/accessibility).

## <a name="save-your-ide-settings"></a>Salvar as configurações do IDE

É possível personalizar sua experiência no IDE salvando seu layout de janela, esquema de mapeamento de teclado e outras preferências. Para obter mais informações, consulte [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Modificar o IDE para exibição de alto contraste

Para algumas pessoas, algumas cores são mais difíceis de enxergar. Se você deseja mais contraste ao codificar, mas não quer usar os temas típicos de "Alto Contraste", agora oferecemos o tema "Azul (Contraste extra)".

  ![Comparar o tema Azul e o tema Azul de Contraste Extra](media/blue-extra-contrast-theme.png "Captura de tela que mostra uma comparação entre o tema azul e o tema de contraste extra azul")

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Use anotações para revelar informações úteis sobre seu código

O editor do Visual Studio inclui vários "adornos" de texto que permitem saber as características e os recursos em determinados pontos em uma linha de código, como ícones de chave de fenda e lâmpada, "linhas sinuosas" de erros e avisos, indicadores e assim por diante. Você pode usar o conjunto de comandos "Mostrar Anotações de Linha" para ajudá-lo a descobrir esses adornos e, em seguida, navegar entre eles.

  ![Usar o conjunto de comandos Mostrar anotações de linha](media/show-line-annotations-command-set.png "Captura de tela do item de menu Mostrar anotações de linha")

## <a name="access-toolbars-by-using-keyboard-shortcuts"></a>Acessar barras de ferramentas usando atalhos de teclado

O Visual Studio IDE tem barras de ferramentas, assim como tem muitas janelas de ferramentas. Os atalhos de teclado a seguir ajudam a acessá-las.

|Recurso|Descrição|Atalho de teclado|
|-------------|-----------------| - |
|Barras de ferramentas do IDE|Selecione o primeiro botão na barra de ferramentas Standard.|**ALT**,  + **Tab** CTRL|
|Barras de ferramentas da janela de ferramentas|Mova o foco para a barra de ferramentas em uma janela de ferramentas. <br> <br> **OBSERVAÇÃO:** isso funciona para a maioria das janelas de ferramentas, mas somente quando o foco está em uma janela de ferramentas. Além disso, você deve escolher a tecla SHIFT antes da tecla ALT. Em algumas janelas de ferramentas, como a Team Explorer, você deve manter a tecla SHIFT pressionada por um momento antes de escolher a tecla ALT.|**Shift** + **ALT**|
|Barras de ferramentas|Acesse o primeiro item na barra de ferramentas Avançar (quando uma barra de ferramentas tem foco).|**Ctrl** + **Guia**|

### <a name="other-useful-keyboard-shortcuts"></a>Outros atalhos de teclado úteis

Alguns outros atalhos de teclado úteis estão indicados a seguir.

|Recurso|Descrição|Atalho de teclado|
|-------------|-----------------| - |
|IDE|Ativar e desativar o alto contraste. <br> <br> **Observação:** Atalho de teclado padrão do Windows|**ALT esquerda** + **Deslocamento** + à esquerda **PrtScn**|
|Caixa de diálogo|Marque ou desmarque a opção da caixa de seleção em uma caixa de diálogo. <br> <br> **Observação:** Atalho de teclado padrão do Windows|**Barra de espaços**|
|Menus de contexto|Abra um menu de contexto (clique com o botão direito do mouse). <br> <br> **Observação:** Atalho de teclado padrão do Windows|**Shift** + **F10**|
|Menus|Acesse rapidamente um item de menu usando as teclas de aceleração. Escolha a tecla **ALT** seguida das letras sublinhadas em um menu para ativar o comando. Por exemplo, para exibir a caixa de diálogo Abrir projeto no Visual Studio, escolha **ALT** + **F** + **O** + **P**.  <br><br> **Observação:** Atalho de teclado padrão do Windows|**ALT**  +  **[letra]**|
|Caixa de pesquisa|Usar o recurso de pesquisa no Visual Studio.|**Ctrl** + **P**|
|Janela caixa de ferramentas|Mover-se entre guias da Caixa de ferramentas.|**Ctrl** + **Seta para cima**<br /><br /> e<br /><br /> **Ctrl** + **Seta para baixo**|
|Janela caixa de ferramentas|Adicionar um controle da Caixa de ferramentas a um formulário ou designer.|**Enter**|
|Caixa de diálogo opções: ambiente > teclado|Excluir uma combinação de teclas inserida na opção **Pressionar teclas de atalho**.|**Backspace**|
|Janela de ferramentas Notificações|Abra a janela de ferramentas Notificações usando duas combinações de teclas de atalho de teclado, uma seguida pela outra. Em seguida, exiba uma notificação usando as teclas de direção para selecioná-la.| **Ctrl** + **&#92;**, **Ctrl** + **N**|

> [!NOTE]
> As caixas de diálogo e os comandos do menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da edição ou das configurações ativas.

## <a name="access-notifications-by-using-keyboard-shortcuts"></a>Acessar notificações usando atalhos de teclado

Quando uma notificação aparece na IDE, você pode acessar a janela Notificações usando atalhos de teclado da seguinte forma:

1. De qualquer lugar no IDE, pressione os dois atalhos de teclado a seguir em sequência, um após o outro: **Ctrl** + **&#92;** e depois **Ctrl** + **N**.

   A janela **Notificações** é aberta.

   ![Janela de ferramentas de notificações no IDE do Visual Studio](media/toast-notification.png "Captura de tela da janela de notificações no IDE do Visual Studio")

1. Use a tecla **Tab** ou as teclas de direção para selecionar uma notificação.

## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Use o miniaplicativo de som para definir indicações de build e de ponto de interrupção

Você pode usar o miniaplicativo de som no Windows para atribuir um som a eventos do programa Visual Studio. Especificamente, você pode atribuir sons aos seguintes eventos do programa:

* Ocorrências de ponto de interrupção
* Build cancelado
* Build com falha
* Build bem-sucedido

Aqui está como:

1. Na caixa **Pesquisar** em um computador executando o Windows 10, digite **Alterar sons do sistema**.

   ![Caixa de pesquisa no Windows 10](media/type-here-to-search.png "Captura de tela da caixa de pesquisa no Windows 10")

   (Como alternativa, se você tiver habilitado a Cortana, diga "Ei Cortana" e, em seguida, diga "Alterar sons do sistema".)

1. Clique duas vezes em **Alterar sons do sistema**.

   ![Resultados da pesquisa no Windows 10](media/change-system-sounds.png "Captura de tela dos resultados da pesquisa "alterar sistema sons" no Windows 10")

1. Na caixa de diálogo **Som**, clique na guia **Sons**.

1. Em **Eventos do Programa**, role até **Microsoft Visual Studio** e, em seguida, selecione os sons que você deseja aplicar aos eventos escolhidos.

   ![Guia Sons do miniaplicativo de som no Windows 10](media/sound-applet.png "Guia Sons do miniaplicativo de som no Windows 10")

1. Clique em **OK**.

::: moniker range="vs-2017"

> [!TIP]
> Para saber mais sobre atualizações de acessibilidade, confira a postagem no blog [Accessibility improvements in Visual Studio 2017 version 15.3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) (Melhorias de acessibilidade no Visual Studio 2017 versão 15.3).

::: moniker-end

## <a name="see-also"></a>Confira também

* [Recursos de acessibilidade do Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Como: personalizar menus e barras de ferramentas no Visual Studio](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
* [Acessibilidade (Visual Studio para Mac)](/visualstudio/mac/accessibility)
* [Acessibilidade da Microsoft](https://www.microsoft.com/Accessibility)
