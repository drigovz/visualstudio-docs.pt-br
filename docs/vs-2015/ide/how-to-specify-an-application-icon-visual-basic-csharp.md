---
title: Como especificar um ícone do aplicativo (Visual Basic, C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 136fd00bea736af0f0c589c28eae597ff8fd558e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670699"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Como especificar um ícone do aplicativo (Visual Basic, C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A propriedade `Icon` de um projeto especifica o arquivo de ícone (.ico) que será exibido para o aplicativo compilado no Explorador de Arquivos e na barra de tarefas do Windows.

 A propriedade `Icon` pode ser acessada no painel **Aplicativo** do **Designer de Projeto**, ele contém uma lista de ícones que foram adicionados a um projeto como recursos ou arquivos de conteúdo.

> [!NOTE]
> Depois de definir a propriedade do ícone para um aplicativo, talvez você também veja a propriedade `Icon` de cada **Janela** ou **Formulário** no aplicativo. Para obter informações sobre os ícones para aplicativos independentes do WPF (Windows Presentation Foundation), consulte a propriedade <xref:System.Windows.Window.Icon%2A>.

### <a name="to-specify-an-application-icon"></a>Para especificar um ícone do aplicativo

1. No **Gerenciador de Soluções**, escolha um nó do projeto (não o nó **Solução**).

2. Na barra de menus, escolha **Projeto**, **Propriedades**.

3. Quando o **Designer de Projeto** for exibido, escolha a guia **Aplicativo**.

4. **(Visual Basic)**  Na lista **Ícone**, escolha um arquivo de ícone (.ico).

     **C#** Próximo à lista **Ícone**, escolha o botão **\<Procurar...>** e navegue até o local do ícone de arquivo desejado.

## <a name="see-also"></a>Consulte também
 [Página de aplicativo, designer de projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) [página de aplicativo,C#designer de projeto ()](../ide/reference/application-page-project-designer-csharp.md) [Gerenciando Propriedades de aplicativo](../ide/application-properties.md) [como: Adicionar ou remover recursos](https://msdn.microsoft.com/7b77bc06-3952-4799-b029-def3f8f7f88d)
