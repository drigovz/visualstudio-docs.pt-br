---
title: 'Como: Especificar um ícone do aplicativo (Visual Basic, C#)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a1e2502d2844b32f6f5e1c22c7fcddf7d6287c8d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55039339"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Como: Especificar um ícone do aplicativo (Visual Basic, C#)

A propriedade `Icon` de um projeto especifica o arquivo do ícone (*.ico*) que será exibido para o aplicativo compilado no **Explorador de Arquivos** e na barra de tarefas do Windows.

A propriedade `Icon` pode ser acessada no painel **Aplicativo** do **Designer de Projeto**, ele contém uma lista de ícones que foram adicionados a um projeto como recursos ou arquivos de conteúdo.

> [!NOTE]
> Depois de definir a propriedade do ícone para um aplicativo, talvez você também veja a propriedade `Icon` de cada **Janela** ou **Formulário** no aplicativo. Para obter informações sobre os ícones para aplicativos independentes do WPF (Windows Presentation Foundation), consulte a propriedade <xref:System.Windows.Window.Icon%2A>.

## <a name="to-specify-an-application-icon"></a>Para especificar um ícone do aplicativo

1. No **Gerenciador de Soluções**, escolha um nó do projeto (não o nó **Solução**).

1. Na barra de menus, escolha **Projeto** > **Propriedades**.

1. Quando o **Designer de Projeto** for exibido, escolha a guia **Aplicativo**.

1. **(Visual Basic)** &mdash;Na lista **Ícone**, escolha um arquivo de ícone (*.ico*).

    **C#**&mdash; Próximo à lista **Ícone**, escolha o botão **\<Procurar...>** e navegue até o local do ícone de arquivo desejado.

## <a name="see-also"></a>Consulte também

- [Página Aplicativo, Designer de Projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Página Aplicativo, Designer de Projeto (C#)](../ide/reference/application-page-project-designer-csharp.md)