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
ms.openlocfilehash: 15c02312d5c257f13b9c0394790bc8a2611d7972
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949793"
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

1. Depois de instalar o **Windows Workflow Foundation** componente, selecione **arquivo** > **novo** > **doprojeto**.

1. Pesquise e selecione um modelo de projeto de fluxo de trabalho, por exemplo, o **aplicativo de Console do fluxo de trabalho** modelo.

1. Prossiga com criar o projeto.

   > [!NOTE]
   > Se você quiser adicionar um novo projeto a uma solução existente, abrir a solução no Visual Studio, clique com botão direito na solução **Gerenciador de soluções**e selecione **Add** > **novo Projeto**.

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