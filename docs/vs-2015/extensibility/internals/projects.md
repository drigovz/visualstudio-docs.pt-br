---
title: Projetos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: 44
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a251af12ccf4be5f0f48f789ac59fedaed3299b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183942"
---
# <a name="projects"></a>Projetos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

No Visual Studio, os projetos são os contêineres que os desenvolvedores usam para organizar arquivos de código-fonte e outros recursos que aparecem no **Gerenciador de soluções**. Normalmente, os projetos são arquivos (por exemplo, um arquivo. csproj para um projeto C#) que armazenam referências a arquivos de código-fonte e recursos como arquivos de bitmap. Os projetos permitem organizar, compilar, depurar e implantar código-fonte, referências a serviços Web e bancos de dados e outros recursos. O VSPackages pode estender o sistema de projeto do Visual Studio de três maneiras principais: *tipos de projeto*, *subtipos de projeto*e *ferramentas personalizadas*.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Tipos de Projeto](../../extensibility/internals/project-types.md)  
 Os *tipos de projeto* adicionam suporte para novos tipos de projetos, como linguagens de programação. Por exemplo, cada idioma ao qual o Visual Studio dá suporte tem seu próprio tipo de projeto e o exemplo de integração do IronPython inclui um tipo de projeto para a linguagem IronPython. Você deve criar um tipo de projeto para idiomas diferentes de C# ou Visual Basic para personalizar como os itens são compilados, depurados, implantados e exibidos em **Gerenciador de soluções**. Para obter mais informações, consulte [Project Types](../../extensibility/internals/project-types.md).  
  
 [Subtipos de projeto](../../extensibility/internals/project-subtypes.md)  
 Os *subtipos de projeto* são baseados em tipos de projeto e podem ser usados para personalizar a maneira como os projetos são criados, depurados e implantados. O Visual Studio usa subtipos de projeto com projetos de dispositivo inteligente; Eles personalizam a implantação copiando um programa criado recentemente de um computador de desenvolvimento para o dispositivo de destino. Os tipos de projeto do C# e do Visual Basic podem ser usados como base para subtipos de projeto; Tipos de projeto C++ não podem. Seus próprios tipos de projeto também podem ser usados como base para subtipos de projeto. Para obter mais informações, consulte [subtipos de projeto](../../extensibility/internals/project-subtypes.md).  
  
 [Projetos Web](../../extensibility/internals/web-projects.md)  
 Explica o projeto Web, que, por sua vez, cria aplicativos Web.  
  
 [Nova geração de projeto: nos bastidores, parte um](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) e [nova geração de projeto: nos bastidores, parte dois](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Explica o que realmente ocorre quando você cria um novo projeto.  
  
 [Exemplos de VSSDK](../../misc/vssdk-samples.md)  
 Descreve os exemplos no VSSDK que lidam com projetos e soluções.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Por dentro do SDK do Visual Studio](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Explique diferentes aspectos da extensibilidade do Visual Studio.
