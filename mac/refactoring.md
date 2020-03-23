---
title: Código de refatoração
description: Como refinar código usando o Visual Studio para Mac e ações rápidas.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 5a87b87f3a14462daec1e069fe222164818d2a19
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "67691292"
---
# <a name="refactoring"></a>Refatoração

Refatorar o código é uma maneira para reorganizar, reestruturar e esclarecer o código existente e garantir que o comportamento geral do código não se altere.

Refatorar produz uma base de código mais íntegra, tornando-a mais utilizável, saudável, legível e fácil de manter tanto para você quanto para qualquer outro desenvolvedor ou usuário que poderia consultar o código.

A integração do Visual Studio para Mac com o Roslyn, a plataforma de compilador .NET do software livre da Microsoft, permite realizar mais operações de refatoração.

## <a name="renaming"></a>Renomear

O comando de refatoração *Renomear* pode ser usado em qualquer identificador de código (por exemplo, um nome de classe, nome de propriedade, etc.) para localizar todas as ocorrências do identificador em questão e alterá-las. Para renomear um símbolo, clique com o botão direito do mouse nele e escolha **Renomear...** ou use a associação de teclas **Cmd (⌘) + R**:

![Renomear um item de menu](media/refactoring-renaming1.png)

Isso destaca o símbolo e todas as referências a ele. Quando você começar a digitar um novo nome, ele será alterado automaticamente em todas as referências no código e você poderá confirmar as alterações pressionando **Enter**:

![Renomear e identificador](media/refactoring-renaming2.png)

## <a name="quick-actions"></a>Ações rápidas

As Ações Rápidas permitem refatorar, gerar ou, de outro modo, modificar o código de maneira fácil com uma única ação.

É possível usar as Ações rápidas para:

* Aplicar uma correção de código para uma violação de regra do analisador de código
* Suprimir uma violação de regra do analisador de código
* Aplicar uma refatoração (por exemplo, embutir uma variável temporária)
* Gerar um código (por exemplo, introduzir uma variável local)

Ações rápidas podem ser aplicadas ![usando o](media/quick-actions-light-bulb-icon.png) ícone ![da lâmpada](media/quick-actions-screwdriver-icon.png) da lâmpada ou ícones da chave de fenda da chave de fenda, ou pressionando **Opção ()Digite**+**Enter** quando o cursor estiver em uma linha de código para a qual uma ação está disponível. Você verá uma lâmpada erro ![ícone de lâmpada de erro](media/quick-actions-error-light-bulb-icon.png) se houver um rabisco vermelho, indicando um erro e o Visual Studio terá uma solução disponível para esse erro.

Para qualquer idioma, terceiros podem oferecer diagnósticos e sugestões personalizados, por exemplo, como parte de um SDK, e as lâmpadas do Visual Studio são acesas de acordo com essas regras.

### <a name="quick-action-icons"></a>Ícones de Ação Rápida
O ícone exibido quando uma Ação Rápida fica disponível oferece uma indicação do tipo de correção ou que a refatoração está disponível. O ícone de *chave de fenda* ![ícone de chave de fenda](media/quick-actions-screwdriver-icon.png) indica apenas que há ações disponíveis para alterar o código, mas você não deve necessariamente usá-las. O ícone de *lâmpada amarela* ![ícone de lâmpada](media/quick-actions-light-bulb-icon.png) indica que há ações disponíveis que você *deve* executar para melhorar o seu código. O ícone de *lâmpada de erro* ![ícone de lâmpada de erro](media/quick-actions-error-light-bulb-icon.png) indica que há uma ação disponível que corrige um erro no seu código.

### <a name="to-see-a-light-bulb-or-screwdriver"></a>Para ver uma lâmpada ou chave de fenda

- Se uma correção estiver disponível, lâmpadas serão exibidas espontaneamente quando você passar o mouse no local de um erro.

   ![Lâmpada com o mouse focalizando](media/refactoring-lightbulb-hover.png)

- Lâmpadas e chaves de fenda são exibidas na margem esquerda do editor quando você move o cursor para uma linha de código para o qual uma Ação Rápida está disponível.

- **Opção de pressione (2)**+**Digite** em qualquer lugar em uma linha para ver uma lista de Ações rápidas e refatorações disponíveis.

![Exibir itens de contexto](media/refactoring-context-action.png)

Focalizar uma das ações de contexto fornecerá uma visualização do que será adicionado ou removido do código.

![Itens de contexto Option Enter](media/refactoring-image2a.png)

Para habilitar essas opções, você deverá selecionar *Habilitar a análise de código-fonte de arquivos abertos* nas opções de **Visual Studio para Mac > Preferências > Editor de Texto > Análise de Código-Fonte**:

![Habilitar a análise de código-fonte](media/refactoring-options.png)

Há mais de 100 ações possíveis que podem ser sugeridas, as quais são habilitadas ou desabilitadas navegando para **Visual Studio para Mac > Preferências > Análise de código-fonte > C# > Ações de Código** e marcando ou desmarcando a caixa ao lado da ação:

![Ações da Análise de código-fonte C#](media/refactoring-image3a.png)

### <a name="common-quick-actions"></a>Ações rápidas comuns

Você pode aprender mais sobre as ações rápidas comuns no artigo [Ações Rápidas Comuns](/visualstudio/ide/common-quick-actions).

## <a name="source-analysis"></a>Análise de código-fonte

A análise de código-fonte examinará o código em tempo real sublinhando possíveis erros e violações de estilo e fornecendo correções automáticas como ações de contexto.

Você pode exibir todos os resultados da análise de código-fonte para qualquer arquivo a qualquer momento exibindo a barra de rolagem à direita do editor de texto:

![Barra lateral da Análise de código-fonte](media/refactoring-image4a.png)

Se você clicar no círculo na parte superior, poderá percorrer cada sugestão, com os problemas de gravidade mais alto sendo mostrados primeiro. Focalizar um resultado ou linha individual exibirá o problema que poderá ser corrigido por meio de ações de contexto:

![Item da análise de código-fonte](media/refactoring-image5.png)

## <a name="related-video"></a>Vídeo relacionados

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Confira também

- [Ações rápidas (Visual Studio no Windows)](/visualstudio/ide/quick-actions)
- [Refatorar o código (Visual Studio no Windows)](/visualstudio/ide/refactoring-in-visual-studio)