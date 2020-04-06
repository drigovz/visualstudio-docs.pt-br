---
title: Começando a desenvolver extensões visuais do estúdio | Microsoft Docs
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 744475e61458f7b91ce08fba4d17046df36f5558
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699736"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Começar a desenvolver extensões do Visual Studio

Se você nunca escreveu uma extensão do Visual Studio antes, provavelmente tem algumas perguntas. Listamos alguns dos mais comuns aqui. Se você não ver as informações que está procurando, use os botões de feedback **(esta página foi útil?**

> [!NOTE]
> Este artigo se aplica ao Visual Studio no Windows. Para visual studio para Mac, consulte [Extending Visual Studio for Mac](/visualstudio/mac/extending-visual-studio-mac). Para obter o Visual Studio Code, consulte [visual Studio Code Extension API](https://code.visualstudio.com/api).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Que software eu preciso para desenvolver extensões do Visual Studio?

Você precisa instalar o Visual Studio SDK, além do Visual Studio, para desenvolver extensões do Visual Studio. Você pode instalar o Visual Studio SDK como parte da configuração regular, ou pode instalá-lo mais tarde. Para obter mais informações sobre a instalação do Visual Studio SDK, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Que tipo de coisas posso fazer com extensões do Visual Studio?

O céu é o limite quando se trata de imaginar diferentes extensões do Visual Studio. Claro, a maioria das extensões tem algo a ver com escrever código, mas isso não tem que ser o caso. Aqui estão alguns exemplos dos tipos de extensões que você pode construir:

- Suporte para linguagens que não estão incluídas no Visual Studio, com coloração de sintaxe, IntelliSense e suporte a compilador e depuração

- Ferramentas de produtividade que ampliam a experiência principal do IDE com modelos adicionais, refatoração de código, novos diálogos ou janelas de ferramentas

- Designers específicos de domínio para cenários como design de dados ou suporte à nuvem

Para exemplos de extensões, confira o [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Muitas extensões são de código aberto, e o Marketplace inclui links para seu repo GitHub.

## <a name="which-visual-studio-features-can-i-extend"></a>Quais recursos do Visual Studio posso estender?

Em teoria, você pode estender quase qualquer parte do Visual Studio: menus, barras de ferramentas, comandos, janelas, soluções, projetos, editores e assim por diante.

Na prática, descobrimos que os recursos que a maioria das pessoas deseja estender são comandos, menus e barras de ferramentas, janelas, IntelliSense e projetos. Aqui estão links para as seções relevantes:

- [Estendendo menus e comandos](../extensibility/extending-menus-and-commands.md): adicione seus próprios itens aos menus e barras de ferramentas do Visual Studio. Você pode usá-los para lançar novas funcionalidades do Visual Studio ou seus próprios aplicativos de ajuda externa. Você também pode fornecer atalhos personalizados para seus itens do menu.

- [Ampliação e personalização da ferramenta Windows](../extensibility/extending-and-customizing-tool-windows.md): amplie as janelas de ferramentas existentes ou crie suas próprias janelas de ferramentas. Por exemplo, você pode adicionar novas propriedades às **propriedades,** ou criar uma nova janela de ferramenta para adicionar recursos adicionais.

- [Extensões de serviço de idiomas](../extensibility/editor-and-language-service-extensions.md)e editor: adicione suas próprias personalizações ao IntelliSense fornecido para linguagens do Visual Studio ou crie suporte para novas linguagens de programação. Você pode criar novas conclusões de declaração, sugestões e novas dicas de ferramentas do QuickInfo. Com lâmpadas, você pode adicionar sugestões de refatoração e correções de código para suportar novas linguagens de programação.

- [Estender projetos](../extensibility/extending-projects.md)

- [Estender opções e configurações de usuário](../extensibility/extending-user-settings-and-options.md)

- [Estender propriedades e a janela de propriedades](../extensibility/extending-properties-and-the-property-window.md)

- [Estender outras partes do Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Shell isolado do Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a>Quais modelos de projeto são fornecidos pelo VSSDK?
 Os dois principais tipos de extensões são VSPackages e extensões MEF. Em geral, as extensões VSPackage são usadas para extensões que usam ou estendem comandos, janelas de ferramentas e projetos. As extensões MEF são usadas para estender ou personalizar o editor do Visual Studio.

 Para extensões Visual C# e Visual Basic, o VSSDK fornece um modelo de projeto VSIX vazio que você pode usar juntamente com os novos modelos de itens que criam comandos de menu, janelas de ferramentas e extensões de editor. Você também pode usar este modelo para empacotar modelos de projeto, trechos de código e outros artefatos para distribuição a outros usuários.

 Para C++, o assistente VSPackage fornece o código para adicionar comandos de menu, janelas de ferramentas e editores personalizados.

 O modelo Shell isolado é usado para embalar uma extensão em uma versão do visual studio shell que você pode marcar e distribuir como sua própria. Os tópicos a seguir mostram como começar com cada tipo de extensão:

- Comandos do [menu: Criando uma extensão com um comando menu](../extensibility/creating-an-extension-with-a-menu-command.md)

- Janelas de [ferramentas: Criando uma extensão com uma janela de ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md)

- Extensões do [editor: Criando uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- Pacotes BÁSICOS VS: [Criando uma extensão com um VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

- Modelo de projeto [VSIX: Começando com o modelo do projeto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Como faço minha extensão parecer com o Visual Studio?
 Obtenha ótimas dicas para projetar a ui para sua extensão no [Visual Studio User Experience Guidelines](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Onde posso encontrar exemplos de código VSSDK?
 Cada um dos links listados na seção anterior tem passo a passo que mostram como implementar recursos específicos. Você também pode encontrar amostras de VSSDK de código aberto no GitHub no [Visual Studio Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="how-can-i-distribute-my-extension"></a>Como posso distribuir minha extensão?
 Você pode instalar sua extensão em outro computador ou enviá-la para seus amigos como um arquivo .vsix, que você instala clicando duas vezes nele. Você pode saber mais sobre os pacotes VSIX no [Shipping Visual Studio Extensions](../extensibility/shipping-visual-studio-extensions.md).

 Você também pode publicar sua extensão no Visual Studio Marketplace, o que a torna visível para um grande número de clientes do Visual Studio. Para um exemplo de embalagem de uma extensão para o Marketplace, consulte [Passo a Passo: Publicar uma extensão visual studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Para obter mais informações sobre o que você precisa fazer para publicar no Marketplace, consulte [Produtos e Extensões para O Visual Studio](/azure/devops/extend/overview?view=vsts).

## <a name="see-also"></a>Confira também

- [Estendendo o Visual Studio para Mac](/visualstudio/mac/extending-visual-studio-mac)
- [Estendendo o código visual do estúdio](https://code.visualstudio.com/api)
