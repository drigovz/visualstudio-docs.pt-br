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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b7a9299321d2aa80eebb564bf9b926f07ab0108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706207"
---
# <a name="projects"></a>Projetos
No Visual Studio, os projetos são os contêineres que os desenvolvedores usam para organizar arquivos de código-fonte e outros recursos que aparecem no **Solution Explorer**. Normalmente, os projetos são arquivos (por exemplo, um arquivo .csproj para um projeto C#) que armazenam referências a arquivos de código-fonte e recursos como arquivos bitmap. Os projetos permitem que você organize, crie, depura e implante código-fonte, referências a serviços e bancos de dados da Web e outros recursos. O VSPackages pode estender o sistema de projetos do Visual Studio de três maneiras principais: *tipos de projetos,* *subtipos de projeto*e ferramentas *personalizadas.*

## <a name="in-this-section"></a>Nesta seção
- [Tipos de projeto](../../extensibility/internals/project-types.md)

 *Os tipos* de projetos adicionam suporte a novos tipos de projetos, como linguagens de programação. Por exemplo, cada idioma que o Visual Studio suporta tem seu próprio tipo de projeto, e a amostra de integração IronPython inclui um tipo de projeto para a linguagem IronPython. Você deve criar um tipo de projeto para outros idiomas que não sejam C# ou Visual Basic para personalizar como os itens são construídos, depurados, implantados e exibidos no **Solution Explorer**. Para obter mais informações, consulte [Tipos de Projeto](../../extensibility/internals/project-types.md).

- [Subtipos de projeto](../../extensibility/internals/project-subtypes.md)

 *Os subtipos do projeto* são baseados em tipos de projetos e podem ser usados para personalizar a forma como os projetos são construídos, depurados e implantados. Visual Studio usa subtipos de projetos com projetos de Dispositivos Inteligentes; eles personalizam a implantação copiando um programa recém-construído de um computador de desenvolvimento para o dispositivo de destino. Os tipos de projeto C# e Visual Basic podem ser usados como base para subtipos de projetos; Os tipos de projeto C++ não podem. Seus próprios tipos de projeto também podem ser usados como base para subtipos de projetos. Para obter mais informações, consulte [Subtipos do Projeto](../../extensibility/internals/project-subtypes.md).

- [Projetos Web](../../extensibility/internals/web-projects.md)

 Explica o projeto Web, que por sua vez cria aplicativos web.

- [Nova geração de projetos: Sob o capô, parte um](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) e [nova geração de projeto: Sob o Capô, Parte Dois](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Explica o que realmente ocorre quando você cria um novo projeto.

- [Amostras de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Contém as amostras no VSSDK que lidam com projetos e soluções.

## <a name="related-sections"></a>Seções relacionadas
- [Por dentro do SDK do Visual Studio](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Explique diferentes aspectos da extensibilidade do Visual Studio.
