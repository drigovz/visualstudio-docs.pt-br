---
title: Como especificar um ícone do aplicativo (Visual Basic, C#)
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7e78bd32bf9c21829adeb04a22cd30abb47a3379
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596132"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Como especificar um ícone do aplicativo (Visual Basic, C#)

A propriedade `Icon` de um projeto especifica o arquivo do ícone (*.ico*) que será exibido para o aplicativo compilado no **Explorador de Arquivos** e na barra de tarefas do Windows.

A propriedade `Icon` pode ser acessada no painel **Aplicativo** do **Designer de Projeto**, ele contém uma lista de ícones que foram adicionados a um projeto como recursos ou arquivos de conteúdo.

> [!NOTE]
> Depois de definir a propriedade do ícone para um aplicativo, talvez você também veja a propriedade `Icon` de cada **Janela** ou **Formulário** no aplicativo. Para obter informações sobre os ícones para aplicativos independentes do WPF (Windows Presentation Foundation), consulte a propriedade <xref:System.Windows.Window.Icon%2A>.

## <a name="to-specify-an-application-icon"></a>Para especificar um ícone do aplicativo

1. No **Gerenciador de Soluções**, escolha um nó do projeto (não o nó **Solução**).

1. Na barra de menus, escolha**Propriedades do** **projeto** > .

1. Quando o **Designer de Projeto** for exibido, escolha a guia **Aplicativo**.

1. **(Básico Visual)** &mdash;Na lista **Ícone,** escolha um arquivo ícone *(.ico).*

    **C#**&mdash;Perto da lista **de ícones,** escolha o ** \<botão Procurar...>** e navegue até o local do arquivo de ícone que deseja.

## <a name="see-also"></a>Confira também

- [Página de inscrição, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Página de inscrição, Project Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)
