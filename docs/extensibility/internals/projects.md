---
title: Projetos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f8fbd19eca1a6aab770718628bbd36a49902074
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327362"
---
# <a name="projects"></a>Projetos
No Visual Studio, os projetos são contêineres que os desenvolvedores usam para organizar os arquivos de código-fonte e outros recursos que aparecem no **Gerenciador de soluções**. Normalmente, os projetos são arquivos (por exemplo, um arquivo. csproj para um projeto de c#) que armazenam referências a recursos como arquivos de bitmap e arquivos de código-fonte. Projetos permitem organizar, compilar, depurar e implantar o código-fonte, as referências a serviços Web e bancos de dados e outros recursos. Os VSPackages pode estender o sistema de projeto do Visual Studio de três maneiras principais: *tipos de projeto*, *subtipos de projeto*, e *ferramentas personalizadas*.

## <a name="in-this-section"></a>Nesta seção
- [Tipos de projeto](../../extensibility/internals/project-types.md)

 *Tipos de projeto* adicionar suporte para novos tipos de projetos, como linguagens de programação. Por exemplo, cada idioma com suporte para Visual Studio tem seu próprio tipo de projeto e o exemplo de integração do IronPython inclui um tipo de projeto para o idioma de IronPython. Você deve criar um tipo de projeto em idiomas diferentes do c# ou Visual Basic para personalizar como itens são criados, depurados, implantados e exibidos no **Gerenciador de soluções**. Para obter mais informações, consulte [tipos de projeto](../../extensibility/internals/project-types.md).

- [Subtipos de projeto](../../extensibility/internals/project-subtypes.md)

 *Subtipos de projeto* são baseados nos tipos de projeto e pode ser usado para personalizar a maneira como os projetos são criados, depurados e implantados. O Visual Studio usa subtipos do projeto com projetos de dispositivo inteligente; eles personalizar a implantação por meio da cópia de um programa criado recentemente de um computador de desenvolvimento para o dispositivo de destino. O c# e tipos de projeto do Visual Basic podem ser usados como base para os subtipos de projeto. Tipos de projeto C++ não é possível. Seus próprios tipos de projeto também podem ser usados como base para os subtipos de projeto. Para obter mais informações, consulte [subtipos do projeto](../../extensibility/internals/project-subtypes.md).

- [Projetos Web](../../extensibility/internals/web-projects.md)

 Explica o projeto da Web, que por sua vez, criar aplicativos Web.

- [Geração de novo projeto: Nos bastidores, parte um](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) e [nova geração de projeto: bastidores, parte dois](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Explica o que realmente ocorre quando você cria um novo projeto.

- [Exemplos de VSSDK](https://aka.ms/vs2015sdksamples) contém exemplos de VSSDK que lidam com projetos e soluções.

## <a name="related-sections"></a>Seções relacionadas
- [Dentro do SDK do Visual Studio](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Explica os diferentes aspectos de extensibilidade do Visual Studio.