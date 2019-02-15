---
title: Novidades no Visual Studio 2019
titleSuffix: ''
description: Saiba mais sobre os novos recursos do Visual Studio 2019.
ms.date: 02/08/2019
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 4667fd19f59453e9efc856aefeaaf8d43aff302d
ms.sourcegitcommit: 61dc40d6c707f8c79779ec1091b296530d5a7b81
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987412"
---
# <a name="whats-new-in-visual-studio-2019-preview"></a>Novidades no Visual Studio 2019 Preview

**Atualizado para a [Versão Prévia 2](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)**

>[!div class="button"]
>[Baixar a versão prévia](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+preview)

O Visual Studio 2019 Preview inclui vários aprimoramentos gerais, juntamente com os novos recursos que otimizam a produtividade do desenvolvedor e colaboração em equipe. Esteja você usando o Visual Studio pela primeira vez ou tendo usado-o por anos, você poderá tirar proveito de seus recursos para todos os aspectos do ciclo de vida de desenvolvimento&mdash;desde criação de projetos simplificada e gerenciamento de integridade do código até fluxos de trabalho de colaboração em equipe e de software livre.<br/><br/>

>[!VIDEO https://channel9.msdn.com/Events/Connect/Microsoft-Connect--2018/D190/player]

Eis uma recapitulação de alto nível do que o Visual Studio tem a oferecer:

* **[Produtividade pessoal e de equipe](#personal-and-team-productivity)**. Produtividade para todos onde isso mais importa.
* **[Suporte de desenvolvimento moderno](#modern-development-support)**. Suporte para seus projetos atuais e soluções futuras.
* **[Inovação contínua](#continuous-innovation)**. Crie código inteligente, com um suporte igualmente inteligente e que conta com o poder da nuvem.

> [!NOTE]
> Para obter uma lista completa dos novos recursos e das novas funcionalidades do Visual Studio 2019 Preview, confira as [notas sobre a versão](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017). E para um resumo de quais são as novidades em nossa segunda versão prévia, consulte a postagem no blog [O Visual Studio 2019 Preview 2 já está disponível](https://blogs.msdn.microsoft.com/visualstudio/2019/01/24/visual-studio-2019-preview-2-is-now-available/).

## <a name="personal-and-team-productivity"></a>Produtividade pessoal e de equipe

É um fato que melhorias de desempenho são primordiais com cada versão do Visual Studio, mas tão importante quanto elas é a melhora da sua produtividade. Aqui está como podemos ajudar com isso.

### <a name="new-start-window"></a>Nova janela de início

A primeira coisa que você observará quando abrir o Visual Studio 2019 será sua nova janela de início.

   ![A nova janela de início no Visual Studio 2019](media/start-window.png)

Essa nova janela de início apresenta opções para clonar ou fazer check-out de código, abrir um projeto ou solução, abrir uma pasta local ou criar um novo projeto. Apresentar essas opções em uma caixa de diálogo simples ajuda tanto iniciantes quanto usuários avançados do Visual Studio a acessar o código mais rapidamente.

Para obter mais informações, confira a postagem no blog [Get to code: How we designed the new Visual Studio start window](https://blogs.msdn.microsoft.com/visualstudio/2018/12/13/get-to-code-how-we-designed-the-new-visual-studio-start-window/) (Direto ao código: como projetamos a nova janela de início do Visual Studio).

### <a name="better-search"></a>Melhor pesquisa

Anteriormente conhecida como Início Rápido, nossa nova experiência de pesquisa é mais rápida e eficaz. Agora, os resultados da pesquisa são exibidos dinamicamente conforme você digita. Além disso, os resultados da pesquisa incluem os atalhos de teclado para comandos, de modo que você pode memorizá-los mais facilmente para uso futuro.

   ![O novo recurso de pesquisa no Visual Studio 2019](media/search-feature.png)

Se você está procurando por comandos, configurações, documentação ou outras coisas úteis, o novo recurso de pesquisa torna mais fácil encontrar o que você está procurando.

### <a name="one-click-code-cleanup"></a>Limpeza de código em um único clique

Juntamente com um novo indicador de integridade do documento, temos um novo comando de limpeza de código. Você pode usar esse novo comando para identificar e depois corrigir avisos e sugestões com o clique de um botão.

   ![O novo recurso de limpeza de código no Visual Studio de 2019](media/code-cleanup.png)

A limpeza formatará o código e aplicará quaisquer correções de código conforme sugerido pelas [configurações atuais](code-styles-and-quick-actions.md), [arquivos .editorconfig](create-portable-custom-editor-options.md) ou [analisadores de Roslyn](../code-quality/roslyn-analyzers-overview.md).

### <a name="debugger-improvements"></a>Melhorias no depurador

#### <a name="search-within-a-watch-window-and-format-watch-values"></a>Pesquisar em uma janela Inspeção e formatar valores da Inspeção

Você provavelmente já esteve lá antes, procurando na janela Inspeção por uma cadeia de caracteres entre um conjunto de valores. No Visual Studio 2019 Preview, adicionamos pesquisa às janelas Inspeção, Locais e Autos para ajudá-lo a encontrar os objetos e os valores que você está procurando.

Você também pode formatar o modo como um valor é exibido dentro das janelas Inspeção, Locais e Autos.  Clique duas vezes em um dos itens em qualquer uma das janelas e adicione uma vírgula (",") para acessar a lista suspensa de especificadores de formato possíveis, cada um dos quais inclui uma descrição de seu efeito pretendido.

   ![A nova janela Inspeção e o novo recurso de formatação de valores no Visual Studio 2019](media/search-watch-window.png)

Para obter mais informações, confira [Aprimorado no Visual Studio 2019: Pesquisar Objetos e Propriedades na postagem de blog Janelas de Inspeção, Autos e Locais](https://blogs.msdn.microsoft.com/visualstudio/2019/01/28/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/).

### <a name="visual-studio-live-share"></a>Visual Studio Live Share

O [Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) é um serviço para desenvolvedores que permite compartilhar uma base de código e seu contexto com um membro da equipe e ter uma colaboração bidirecional instantânea diretamente no Visual Studio. Com o Live Share, um membro da equipe pode ler, navegar, editar e depurar um projeto compartilhado com ele de forma fácil e segura.

E com o Visual Studio 2019 Preview, esse serviço é instalado por padrão.

   ![Um arquivo GIF animado que mostra o recurso de colaboração Live Share no Visual Studio 2019](media/live-share-collaboration.gif)

Para obter mais informações, confira a postagem no blog [Visual Studio Live Share for real-time code reviews and interactive education](https://blogs.msdn.microsoft.com/visualstudio/2018/12/06/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) (Visual Studio Live Share para revisões de código em tempo real e educação interativa).

## <a name="modern-development-support"></a>Suporte de desenvolvimento moderno

### <a name="manage-pull-requests-prs-from-the-ide"></a>Gerenciar PRs (solicitações de pull) do IDE

Estamos introduzindo uma nova extensão que você pode baixar para usar com o Visual Studio 2019 Preview. Com essa nova extensão, você pode examinar, executar e até mesmo depurar solicitações de pull de sua equipe sem sair do IDE [(ambiente de desenvolvimento integrado)](../get-started/visual-studio-ide.md) do Visual Studio. Damos suporte a código no Azure Repos atualmente, mas estamos expandindo para dar suporte a GitHub e melhorar a experiência geral.

Para começar agora mesmo, você pode baixar a extensão [Solicitações de pull para o Visual Studio](https://aka.ms/pr4vs) do Visual Studio Marketplace.

### <a name="develop-with-net-core-3-preview"></a>Desenvolver com a versão prévia do .NET Core 3

A versão prévia do Visual Studio 2019 dá suporte à criação de aplicativos [.NET Core 3](https://dotnet.microsoft.com/download/dotnet-core/3.0) para qualquer plataforma. Continuaremos a dar suporte ao desenvolvimento multiplataforma em C++ e ao desenvolvimento móvel do .NET para iOS e Android com Xamarin e a melhorá-los.

   ![Desenvolver aplicativos com a versão prévia do .NET Core 3 no Visual Studio 2019](media/dot-net-core-three-dev.png)

Para obter mais informações, consulte as seguintes páginas:

* Notas de versão do [.NET Core 3 (versão prévia 1)](https://github.com/dotnet/core/blob/master/release-notes/3.0/preview/3.0.0-preview1.md) e do [.NET Core 3 (versão prévia 2)](https://github.com/dotnet/core/blob/master/release-notes/3.0/preview/3.0.0-preview2.md)
* Postagem no blog [Anúncio do .NET Core 3 (versão prévia 1)](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/) e [Anúncio do .NET Core 3 (versão prévia 2)](https://blogs.msdn.microsoft.com/dotnet/2019/01/29/announcing-net-core-3-preview-2/)

## <a name="continuous-innovation"></a>Inovação contínua

### <a name="per-monitor-aware-pma-rendering"></a>Renderização PMA (com reconhecimento por monitor)

Se você usa monitores configurados com fatores de escala de exibição diferentes ou se conecta remotamente a um computador com fatores de escala de exibição diferentes daqueles do seu dispositivo principal, você pode notar que o Visual Studio parece desfocado ou é renderizado na escala errada.

Com o lançamento do Visual Studio 2019 Preview, estamos dando os primeiros passos para tornar o Visual Studio um aplicativo PMA (com reconhecimento por monitor). Criamos o trabalho de base que permitirá que o Visual Studio seja renderizado corretamente, independentemente de quais fatores de escala de exibição você usar.

   ![Renderização PMA (com reconhecimento por monitor) no Visual Studio 2019](media/per-monitor-aware-dpi-scaling.png)

Para saber mais, confira a postagem no blog [Better multi-monitor experience with Visual Studio 2019 (Experiência ideal de Vários Monitores com o Visual Studio 2019)](https://blogs.msdn.microsoft.com/visualstudio/2019/02/07/a-better-multi-monitor-experience-with-visual-studio-2019/).

### <a name="visual-studio-intellicode"></a>Visual Studio IntelliCode

O [Visual Studio IntelliCode](/visualstudio/intellicode/) é uma extensão que aprimora os esforços de desenvolvimento de software, usando IA (inteligência artificial). O IntelliCode treina em 2.000 projetos de código-fonte aberto no GitHub, sendo cada um com mais de 100 estrelas, para gerar suas recomendações.

Aqui estão algumas maneiras em que o Visual Studio IntelliCode pode ajudar a aumentar sua produtividade:

* Fornecer conclusões de código com percepção de contexto
* Orientar os desenvolvedores a aderir aos padrões e estilos de sua equipe
* Encontrar problemas de código difíceis de detectar
* Concentrar revisões de código chamando atenção para áreas que realmente importam

 ![Exemplo de sugestão do IntelliSense](media/intellicode-intellisense-suggestion.png)

Quando fizemos a primeira versão prévia da extensão do IntelliCode para Visual Studio, ela era inicialmente compatível apenas com C#. Agora, adicionamos suporte para C++ e XAML no Visual Studio também.

E se você usa C#, também adicionamos a capacidade de treinar um modelo personalizado em seu próprio código.

Para obter mais informações sobre as atualizações recentes, confira a postagem no blog [Visual Studio IntelliCode supports more languages and learns from your code](https://blogs.msdn.microsoft.com/visualstudio/2018/12/05/visual-studio-intellicode-supports-more-languages-and-learns-from-your-code/) (O Visual Studio IntelliCode dá suporte a mais idiomas e aprende com o código). Para obter mais informações sobre a extensão e como baixá-la, confira a página [Visual Studio IntelliCode – Versão Prévia](https://go.microsoft.com/fwlink/?linkid=872707) no Microsoft DevLabs.

## <a name="give-us-feedback"></a>Fornecer comentários

Por que enviar comentários à equipe do Visual Studio? Porque nós levamos a sério os comentários dos clientes. Eles motivam muito do que fazemos.

* Se quiser fazer sugestões sobre como podemos melhorar o Visual Studio, você poderá fazer isso usando a ferramenta [Fornecer uma sugestão](talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features).

* Se você tiver um travamento, uma falha ou outro problema de desempenho, você poderá compartilhar facilmente conosco as etapas de reprodução e os arquivos de suporte usando a ferramenta [Relatar um Problema](talk-to-us.md#i-want-to-report-a-problem-with-visual-studio).

## <a name="see-also"></a>Consulte também

* [Notas sobre a versão do Visual Studio 2019](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)
* [Microsoft Connect(); conferência de 2018](https://www.microsoft.com/connectevent)
* [Novidades no Visual Studio 2017](whats-new-visual-studio-2017.md)
