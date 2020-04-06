---
title: Visual Studio SDK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56f772d7d27f11318cdeb0bf365373d5f7c1294b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698071"
---
# <a name="visual-studio-sdk"></a>SDK do Visual Studio
O Visual Studio SDK ajuda você a estender os recursos do Visual Studio ou integrar novos recursos ao Visual Studio. Você pode distribuir suas extensões para outros usuários, bem como para o Visual Studio Marketplace. A seguir estão algumas das maneiras pelas quais você pode estender o Visual Studio:

- Adicionar comandos, botões, menus e outros elementos de II ao IDE

- Adicionar janelas de ferramentas para novas funcionalidades

- Amplie o IntelliSense para um determinado idioma ou forneça o IntelliSense para novas linguagens de programação

- Use lâmpadas para fornecer dicas e sugestões que ajudem os desenvolvedores a escrever um código melhor

- Habilite o suporte para um novo idioma

- Adicione um tipo de projeto personalizado

- Alcance milhões de desenvolvedores através do Visual Studio Marketplace

  Se você nunca escreveu uma extensão do Visual Studio antes, você deve encontrar mais informações sobre esses recursos e em [Começar a desenvolver extensões do Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="install-the-visual-studio-sdk"></a>Instalar o SDK do Visual Studio
 O Visual Studio SDK é um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Novidades no Visual Studio 2017 SDK 2017
 O Visual Studio SDK tem alguns novos recursos, como o formato VSIX v3, bem como alterações de quebra, o que pode exigir que você atualize sua extensão. Para obter mais informações, veja [as novidades do Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).

## <a name="visual-studio-user-experience-guidelines"></a>Diretrizes de experiência do usuário do Visual Studio
 Obtenha ótimas dicas para projetar a ui para sua extensão nas [diretrizes de experiência do usuário do Visual Studio.](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)

 Você também pode aprender como fazer sua extensão parecer ótima em dispositivos de DPI altos com o artigo [Problemas de DPI de endereço.](../extensibility/addressing-dpi-issues2.md)

 Aproveite o [serviço e catálogo](../extensibility/image-service-and-catalog.md) de imagem para um ótimo gerenciamento de imagens e suporte para alto DPI e tema.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Encontre e instale extensões existentes do Visual Studio
 Você pode encontrar extensões do Visual Studio no diálogo **Extensões e Atualizações** no menu **Ferramentas.** Para obter mais informações, consulte [Encontrar e Usar extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Você também pode encontrar extensões no [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

## <a name="visual-studio-sdk-reference"></a>Referência visual Studio SDK
 Você pode encontrar a referência da API Visual Studio SDK no [Visual Studio SDK Reference](../extensibility/visual-studio-sdk-reference.md).

## <a name="visual-studio-sdk-samples"></a>Amostras de Visual Studio SDK
 Você pode encontrar exemplos de código aberto de extensões VS SDK no GitHub no [Visual Studio Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Este repo do GitHub contém amostras que ilustram vários recursos extensíveis no Visual Studio.

## <a name="other-visual-studio-sdk-resources"></a>Outros recursos do Visual Studio SDK
 Se você tiver dúvidas sobre o VSSDK ou quiser compartilhar suas experiências desenvolvendo extensões, você pode usar o [Fórum de Extensibilidade visual studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) ou o [ExtendVS Gitter Chatroom](https://gitter.im/Microsoft/extendvs).

 Você pode encontrar mais informações no [blog VSX Arcana](https://blogs.msdn.microsoft.com/vsx/) e em vários blogs escritos por MVPs da Microsoft:

- [Extensões favoritas do Visual Studio](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Extensibilidade do Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)

- [Ampliando o Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>Confira também

- [Crie uma extensão com um comando de menu](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Como: Migrar projetos de extensibilidade para o Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [FAQ: Conversão de complementos em extensões VSPackage](/visualstudio/extensibility/faq-converting-add-ins-to-vspackage-extensions?view=vs-2015)
- [Gerenciar vários segmentos em código gerenciado](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Estender menus e comandos](../extensibility/extending-menus-and-commands.md)
- [Adicionar comandos às barras de ferramentas](../extensibility/adding-commands-to-toolbars.md)
- [Estender e personalizar janelas de ferramentas](../extensibility/extending-and-customizing-tool-windows.md)
- [Extensões de serviços de editor e linguagem](../extensibility/editor-and-language-service-extensions.md)
- [Ampliar projetos](../extensibility/extending-projects.md)
- [Estender as configurações e opções do usuário](../extensibility/extending-user-settings-and-options.md)
- [Crie modelos personalizados de projetos e itens](../extensibility/creating-custom-project-and-item-templates.md)
- [Estender propriedades e a janela da propriedade](../extensibility/extending-properties-and-the-property-window.md)
- [Estender outras partes do Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Uso e prestação de serviços](../extensibility/using-and-providing-services.md)
- [Gerenciar VSPackages](../extensibility/managing-vspackages.md)
- [Visual Studio shell isolado](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Extensões do Ship Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Por dentro do SDK do Visual Studio](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Suporte para o SDK do Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)
- [Referência visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
