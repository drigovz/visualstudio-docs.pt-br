---
title: Criar um projeto do Workflow Foundation
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf4013f1302ff4952fa34c689801978b9116e549
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57222448"
---
# <a name="workflow-project-templates"></a>Modelos de projeto de fluxo de trabalho

Você pode criar fluxos de trabalho, serviços de fluxo de trabalho Windows Communication Foundation (WCF), as atividades personalizados e designers personalizados de atividade usando modelos de projeto do Visual Studio. Este artigo descreve como criar bibliotecas e aplicativos com modelos de projeto disponíveis no Visual Studio.

## <a name="create-a-workflow-project"></a>Criar um projeto de Fluxo de Trabalho

Visual Studio fornece quatro diferentes modelos de projeto de fluxo de trabalho:

- Aplicativo de console do fluxo de trabalho

- Aplicativo de serviço de fluxo de trabalho do WCF

- Biblioteca de atividades

- Biblioteca do designer de atividade

Para acessar esses modelos, primeiro instale o **Windows Workflow Foundation** componente do Visual Studio. Para obter instruções detalhadas, consulte [instalar o Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Depois de instalar o **Windows Workflow Foundation** componente, abra o **novo projeto** caixa de diálogo, selecionando **arquivo** > **novo**  >  **Projeto**.

1. No painel esquerdo, selecione a **Visual c#** > **fluxo de trabalho** categoria (ou **Visual Basic** > **fluxo de trabalho**se você preferir o Visual Basic).

1. No painel central, selecione um modelo de projeto, como **aplicativo de Console do fluxo de trabalho**.

1. No **nome** , digite um nome descritivo para seu projeto para torná-lo mais fácil identificar.

1. No **local** , digite o diretório no qual você deseja salvar o projeto, ou selecione **procurar** para navegar até ele.

1. No **solução** , digite o nome para a nova solução. Selecione **Okey** para criar o aplicativo.

   > [!NOTE]
   > Se você quiser adicionar um novo projeto a uma solução existente, abrir a solução no Visual Studio, clique com botão direito na solução **Gerenciador de soluções**e selecione **Add** > **novo Projeto** para abrir o **novo projeto** caixa de diálogo.

## <a name="workflow-console-app"></a>Aplicativo de console do fluxo de trabalho

Se você escolher o **aplicativo de Console do fluxo de trabalho** modelo, o Visual Studio cria uma definição de fluxo de trabalho em XAML. O Designer de fluxo de trabalho é aberta e exibe a tela para o fluxo de trabalho que você criou. Para compor um fluxo de trabalho, arraste atividades ou outros itens de fluxo de trabalho da **caixa de ferramentas** à superfície de design.

## <a name="wcf-workflow-service-app"></a>Aplicativo de serviço de fluxo de trabalho do WCF

Se você escolher o **aplicativo de serviço de fluxo de trabalho WCF** modelo, o Visual Studio cria uma definição de serviço como XAML. O Designer de fluxo de trabalho é aberto para o modo de design com uma <xref:System.Activities.Statements.Sequence> que contém um conjunto de atividades <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> atividades.

## <a name="activity-library"></a>Biblioteca de atividades

Se você escolher o **biblioteca de atividades** modelo, o Visual Studio cria uma definição de atividade em XAML. Designer de fluxo de trabalho é aberta e exibe a tela para a atividade personalizada. Arraste uma atividade de **caixa de ferramentas** para a superfície de design para incluí-lo em sua atividade personalizada.

> [!NOTE]
> Você pode apenas uma atividade filho no corpo da atividade personalizada. No entanto, o que a atividade filho pode ser uma atividade composta, como uma <xref:System.Activities.Statements.Sequence> atividade ou <xref:System.Activities.Statements.Flowchart> atividade.

## <a name="activity-designer-library"></a>Biblioteca do designer de atividade

Se você escolher o **biblioteca do Designer de atividade** modelo, o Visual Studio cria uma definição de designer de atividade em XAML e um arquivo de implementação de code-behind. O Designer de fluxo de trabalho é aberta e exibe a tela para o designer de atividade. Controles de arraste Windows Presentation Foundation (WPF) de **caixa de ferramentas** para a superfície de design para usá-los em seu designer personalizado de atividade.

Para obter um exemplo de como implementar um designer personalizado de atividade, consulte [como: Criar um designer personalizado de atividade](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Designers personalizados de atividade podem ser usados para atividades personalizadas em atividades do .NET Framework padrão.

## <a name="see-also"></a>Consulte também

- [Use o Designer de fluxo de trabalho](developing-applications-with-the-workflow-designer.md)
- [Criar fluxos de trabalho (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)