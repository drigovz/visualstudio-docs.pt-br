---
title: Ferramentas de localização
ms.date: 02/15/2019
ms.topic: reference
helpviewer_keywords:
- globalization [Visual Studio]
- Visual Basic code, international applications
- C#, international applications
- localization [Visual Studio]
- world-ready applications
- international applications [Visual Studio]
ms.assetid: 4d9815ae-3e80-4b4d-933d-f8309aee18d5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eebdccf44580442b87e3d31e33ddcd7052838306
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810895"
---
# <a name="develop-globalized-and-localized-apps"></a>Desenvolver aplicativos localizados e globalizados

O Visual Studio facilita o desenvolvimento para um público-alvo internacional, aproveitando os serviços internos do [.NET](/dotnet/standard/globalization-localization/).

Por exemplo, o sistema do projeto dos aplicativos Windows Forms pode gerar arquivos de recurso para a cultura de interface do usuário de fallback e para cada cultura de interface do usuário adicional. Ao compilar um projeto no Visual Studio, os arquivos de recursos são compilados do formato XML do Visual Studio (.resx) para um formato binário intermediário (.resources), que são então inseridos em assemblies satélites. Para obter mais informações, consulte [Arquivos de recurso no Visual Studio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps#VSResFiles) e [Criar assemblies satélite para aplicativos da área de trabalho](/dotnet/framework/resources/creating-satellite-assemblies-for-desktop-apps).

## <a name="bidirectional-languages"></a>Linguagens bidirecionais

É possível usar o Visual Studio para criar aplicativos que exibem o texto corretamente em idiomas escritos da direita para a esquerda, incluindo árabe e hebraico. Para alguns recursos, é possível apenas definir as propriedades. Em outros casos, é necessário implementar recursos no código.

> [!NOTE]
> Para inserir e exibir idiomas bidirecionais, você precisa trabalhar com uma versão do Windows que está configurada com o idioma apropriado. Essa pode ser uma versão em inglês do Windows com o pacote de idioma apropriado instalado, ou a versão localizada do Windows.

### <a name="apps-that-support-bidirectional-languages"></a>Aplicativos que dão suporte a idiomas bidirecionais

- Aplicativos do Windows

   É possível criar aplicativos totalmente bidirecionais que incluem suporte para texto bidirecional, sentido de leitura da direita para a esquerda e espelhamento (reversão do layout de janelas, menus, caixas de diálogo e assim por diante). Com exceção do espelhamento, esses recursos estão disponíveis por padrão ou como configurações de propriedades. Há suporte inerente para o espelhamento em alguns recursos, como caixas de mensagem. No entanto, em outros casos, é necessário implementar o espelhamento no código. Para obter mais informações, consulte [suporte bidirecional para aplicativos Windows Forms](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications).

- Aplicativos Web

   Os serviços Web dão suporte ao recebimento e ao envio de textos UTF-8 e Unicode, tornando-os adequados para aplicativos que envolvem idiomas bidirecionais. Os aplicativos cliente Web dependem de navegadores para sua interface do usuário e, portanto, o grau de suporte bidirecional em um aplicativo Web depende do nível de suporte do navegador do usuário a essas funcionalidades bidirecionais. No Visual Studio, é possível criar aplicativos com suporte para texto em árabe ou hebraico, sentido de leitura da direita para a esquerda, codificação de arquivos e configurações da cultura local. Para obter mais informações, consulte [suporte bidirecional para aplicativos web ASP.net](/previous-versions/6eedwbtt(v=vs.140)).

> [!NOTE]
> Os aplicativos de console não incluem o suporte de texto para idiomas bidirecionais. Esta é uma consequência de como o Windows funciona com aplicativos de console.

## <a name="see-also"></a>Confira também

- [Suporte para idiomas bidirecionais no Visual Studio](use-bidirectional-languages.md)
- [Globalizar e localizar aplicativos .NET](/dotnet/standard/globalization-localization/)
- [Recursos em aplicativos .NET](/dotnet/framework/resources/)