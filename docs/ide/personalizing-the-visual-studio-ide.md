---
title: Personalizar o IDE
ms.date: 11/20/2017
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36e5e8f59474a9a2fcbfef7a1c6b3d75febe3086
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708765"
---
# <a name="personalize-the-visual-studio-ide"></a>Personalizar o IDE do Visual Studio

Você pode personalizar o Visual Studio de várias maneiras para dar o melhor suporte ao seu próprio estilo e requisitos de desenvolvimento. Muitas das configurações usam perfis móveis entre as instâncias do Visual Studio&mdash;consulte [Configurações sincronizadas](../ide/synchronized-settings-in-visual-studio.md). Este artigo descreve de forma breve as diferentes personalizações e o local em que é possível encontrar mais informações.

> [!NOTE]
> Este tópico aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Personalizar o IDE do Visual Studio para Mac](/visualstudio/mac/customizing-the-ide).

## <a name="default-settings"></a>Configurações padrão

Escolha uma coleção padrão de configurações que otimiza o Visual Studio para seu tipo de desenvolvimento. Para obter mais informações, confira [Configurações do ambiente](environment-settings.md).

## <a name="general-environment-options"></a>Opções do ambiente geral

Muitas opções de personalização são expostas pela caixa de diálogo [Opções de Ambiente](../ide/reference/environment-options-dialog-box.md). Há duas maneiras de acessar essa caixa de diálogo:

- Na barra de menus, escolha **Ferramentas** > **Opções** e, se o nó **Ambiente** ainda não estiver expandido, expanda-o.

- Digite `environment` na caixa **Início rápido** e escolha **Ambiente --> Geral** na lista de resultados.

   > [!TIP]
   > Quando a caixa de diálogo for exibida, você poderá pressionar **F1** para obter ajuda sobre as diversas configurações nessa página.

## <a name="environment-color-themes"></a>Temas de cores do ambiente

Para alterar o tema de cores entre claro, escuro e azul, digite `environment` na caixa **Início Rápido** e, em seguida, escolha **Ambiente --> Geral**. Na caixa de diálogo **Opções**, altere a opção **Tema de cores**.

Para alterar as opções de colorização no editor, digite `environment` na caixa **Início Rápido** e, em seguida, escolha **Ambiente --> Fontes e Cores**. Confira [Como: Alterar fontes e cores](../ide/how-to-change-fonts-and-colors-in-visual-studio.md).

### <a name="main-menu-casing"></a>Maiúsculas e minúsculas do menu principal

É possível alterar o uso de maiúsculas e minúsculas do menu principal optando por **Primeira letra de cada palavra em maiúscula** ("Arquivo") ou **Tudo em maiúscula** ("ARQUIVO"). Digite `environment` na caixa **Início Rápido**, selecione **Ambiente --> Geral** e, em seguida, altere a opção **Aplicar o estilo de capitalização de título à barra de menus**.

### <a name="customize-menus-and-toolbars"></a>Personalizar menus e barras de ferramentas

Para adicionar ou remover itens do menu ou da barra de ferramentas, confira [Como: Personalizar menus e barras de ferramentas](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

::: moniker range="vs-2017"

## <a name="start-page"></a>Página inicial

Para criar uma página inicial personalizada para você e sua equipe, confira [Personalizar a página inicial](../ide/customizing-the-start-page-for-visual-studio.md).

::: moniker-end

## <a name="window-layouts"></a>Layouts de janela

Você pode definir e salvar vários layouts de janela e mudar entre eles. Por exemplo, você pode definir um layout para codificação e outro para depuração. Para organizar as posições e o comportamento da janela e salvar os layouts personalizados, confira [Personalizar layouts de janela](../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="external-tools"></a>Ferramentas externas

É possível personalizar o menu **Ferramentas** para iniciar ferramentas externas. Para obter mais informações, confira [Gerenciar ferramentas externas](../ide/managing-external-tools.md).

## <a name="see-also"></a>Consulte também

- [Configurações do ambiente](environment-settings.md)
- [Visão geral do IDE do Visual Studio](../get-started/visual-studio-ide.md)
- [Início Rápido: Introdução ao IDE do Visual Studio](../ide/quickstart-ide-orientation.md)
- [Personalizar o IDE do Visual Studio para Mac](/visualstudio/mac/customizing-the-ide)