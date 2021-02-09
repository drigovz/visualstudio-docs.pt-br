---
title: Como especificar um ícone do aplicativo (Visual Basic, C#)
description: Saiba como usar a Propriedade Icon para especificar o ícone que o explorador de arquivos e a barra de tarefas do Windows exibem para o aplicativo compilado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 77be1eefb4ea4da139bb536e9d838afecddd7202
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869291"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Como especificar um ícone do aplicativo (Visual Basic, C#)

A propriedade `Icon` de um projeto especifica o arquivo do ícone (*.ico*) que será exibido para o aplicativo compilado no **Explorador de Arquivos** e na barra de tarefas do Windows.

A propriedade `Icon` pode ser acessada no painel **Aplicativo** do **Designer de Projeto**, ele contém uma lista de ícones que foram adicionados a um projeto como recursos ou arquivos de conteúdo.

> [!NOTE]
> Depois de definir a propriedade do ícone para um aplicativo, talvez você também veja a propriedade `Icon` de cada **Janela** ou **Formulário** no aplicativo. Para obter informações sobre os ícones para aplicativos independentes do WPF (Windows Presentation Foundation), consulte a propriedade <xref:System.Windows.Window.Icon%2A>.

## <a name="to-specify-an-application-icon"></a>Para especificar um ícone do aplicativo

1. No **Gerenciador de Soluções**, escolha um nó do projeto (não o nó **Solução**).

1. Na barra de menus, escolha   >  **Propriedades** do projeto.

1. Quando o **Designer de Projeto** for exibido, escolha a guia **Aplicativo**.

1. **(Visual Basic)** &mdash; Na lista de **ícones** , escolha um arquivo de ícone (*. ico*).

    **C#** &mdash; Próximo à lista de **ícones** , escolha o **\<Browse...>** botão e, em seguida, navegue até o local do arquivo de ícone desejado.

## <a name="see-also"></a>Confira também

- [Página de aplicativo, designer de projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Página de aplicativo, designer de projeto (C#)](../ide/reference/application-page-project-designer-csharp.md)
