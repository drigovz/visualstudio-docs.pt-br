---
title: Gerenciando propriedades de solução e projeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d727efc0-1096-4ede-84b6-31a65da22ac0
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f3e9ff4acbfd6df1980a3882311b3d3c4611e064
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758115"
---
# <a name="managing-project-and-solution-properties"></a>Gerenciando propriedades de solução e projeto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projetos têm propriedades que controlam muitos aspectos da compilação, da depuração, do teste e da implantação. Algumas propriedades são comuns entre todos os tipos de projeto, e algumas são exclusivas de linguagens ou plataformas específicas. Acesse propriedades do projeto clicando com o botão direito do mouse no nó do projeto no Gerenciador de Soluções e escolhendo Propriedades ou digitando as propriedades na caixa de pesquisa **QuickLaunch** na barra de menus.  
  
 ![Menu de contexto do projeto](../ide/media/vs2015-proj-prop-menu.gif "vs2015_proj_prop_menu")  
  
 Projetos do .NET também têm um nó de propriedades na árvore do projeto em si.  
  
 ![Nó de propriedades na árvore do Gerenciador de Soluções](../ide/media/vs2015-props-se.png "VS2015_Props_SE")  
  
> [!TIP]
>  As soluções têm algumas propriedades, bem como os itens de projeto; essas propriedades são acessadas na [Janela Propriedades](../ide/reference/properties-window.md), não no **Designer de Projeto**.  
  
## <a name="project-properties"></a>Propriedades do projeto  
 Propriedades do Projeto são organizadas em grupos, cada grupo tem sua própria página de propriedades, e as páginas podem ser diferentes para diferentes linguagens e tipos de projeto.  
  
### <a name="c-and-visual-basic-projects"></a>Projetos em C# e Visual Basic  
 Em projetos C# e Visual Basic, as propriedades são expostas no **Designer de Projeto**. A ilustração a seguir mostra a página de propriedades Build para um projeto WPF em C#:  
  
 ![Designer de Projeto do Visual Studio](../ide/media/vs2015-proppage-build.png "VS2015_PropPage_Build")  
  
 Para obter informações sobre cada uma das páginas de propriedades no Designer de Projeto, consulte [Referência de Propriedades de Projeto](../ide/reference/project-properties-reference.md).  
  
### <a name="c-and-javascript-projects"></a>Projetos em C++ e JavaScript  
 Projetos em C++ e JavaScript têm uma interface do usuário diferente para gerenciar propriedades do projeto. Esta ilustração mostra uma página de propriedades de projeto em C++ (páginas em JavaScript são semelhantes):  
  
 ![Propriedades do projeto em Visual C&#43;&#43;](../ide/media/vs2015-projprops-cpp.png "VS2015_ProjProps_cpp")  
  
 Para obter informações sobre propriedades de projeto C++, consulte [Trabalhando com propriedades do projeto](http://msdn.microsoft.com/library/9b0d6f8b-7d4e-4e61-aa75-7d14944816cd). Para obter mais informações sobre as propriedades de JavaScript, consulte [Páginas de propriedades, JavaScript](../ide/reference/property-pages-javascript.md).  
  
## <a name="solution-properties"></a>Propriedades da solução  
 Para acessar propriedades na solução, clique com o botão direito do mouse no nó da solução no **Gerenciador de Soluções** e escolha **Propriedades**. Na caixa de diálogo, você pode definir configurações de projeto para compilações de Depuração ou Versão, escolher quais projetos devem ser o projeto de inicialização quando F5 é pressionado e definir opções de análise de código.  
  
## <a name="see-also"></a>Consulte também  
 [Soluções e projetos no Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
