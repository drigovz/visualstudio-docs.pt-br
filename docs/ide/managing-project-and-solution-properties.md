---
title: Gerenciar propriedades do projeto e da solução
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01fcdc09c9d3ee4f5a38a95ef4304bfdf537d527
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591301"
---
# <a name="manage-project-and-solution-properties"></a>Gerenciar propriedades do projeto e da solução

Projetos têm propriedades que controlam muitos aspectos da compilação, da depuração, do teste e da implantação. Algumas propriedades são comuns entre todos os tipos de projeto, e algumas são exclusivas de linguagens ou plataformas específicas. Para acessar as propriedades do projeto, clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e escolha **Propriedades** ou digite **propriedades** na caixa de pesquisa na barra de menus e escolha **Janela de Propriedades** nos resultados.

![Menu de contexto do projeto](../ide/media/vs2015_proj_prop_menu.gif)

Os projetos do .NET também podem ter um nó de propriedades na árvore do projeto em si.

![Nó de propriedades na árvore do Gerenciador de Soluções](../ide/media/vs2015_props_se.png)

> [!NOTE]
> Este tópico aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Gerenciando propriedades da solução e do projeto (Visual Studio para Mac)](/visualstudio/mac/managing-solutions-and-project-properties).

## <a name="project-properties"></a>Propriedades do projeto

As propriedades do projeto são organizadas em grupos e cada grupo tem sua própria página de propriedades. As páginas podem ser diferentes para idiomas e tipos de projeto distintos.

### <a name="c-visual-basic-and-f-projects"></a>Projetos em C#, Visual Basic e F#

Em projetos C#, Visual Basic e F #, as propriedades são expostas no **Designer de projeto**. A ilustração a seguir mostra a página de propriedades de **compilação** para um projeto WPF em C#:

![Designer de Projeto do Visual Studio](../ide/media/vs2015_proppage_build.png)

Para obter informações sobre cada uma das páginas de propriedades no **Designer de projeto**, consulte referência de [Propriedades do projeto](../ide/reference/project-properties-reference.md).

> [!TIP]
> As soluções têm algumas propriedades e, portanto, itens de projeto; essas propriedades são acessadas no [janela Propriedades](../ide/reference/properties-window.md), não no **Designer de projeto**.

### <a name="c-and-javascript-projects"></a>Projetos em C++ e JavaScript

Projetos em C++ e JavaScript têm uma interface do usuário diferente para gerenciar propriedades do projeto. Esta ilustração mostra uma página de propriedades de projeto em C++ (páginas em JavaScript são semelhantes):

![Propriedades de projeto do Visual C&#43;&#43;](../ide/media/vs2015_projprops_cpp.png)

Para obter informações sobre as propriedades do projeto C++, confira [Trabalhar com propriedades do projeto (C++)](/cpp/build/working-with-project-properties). Para obter mais informações sobre as propriedades de JavaScript, consulte [páginas de propriedades, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Propriedades da solução

Para acessar propriedades na solução, clique com o botão direito do mouse no nó da solução no **Gerenciador de Soluções** e escolha **Propriedades**. Na caixa de diálogo, você pode definir configurações de projeto para compilações de **depuração** ou **versão** , escolher quais projetos devem ser o projeto de inicialização quando **F5** for pressionado e definir opções de análise de código.

## <a name="see-also"></a>Confira também

- [Soluções e projetos no Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
- [Gerenciando propriedades da solução e do projeto (Visual Studio para Mac)](/visualstudio/mac/managing-solutions-and-project-properties)
