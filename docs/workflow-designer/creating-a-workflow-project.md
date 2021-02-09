---
title: Criar um projeto do Workflow Foundation
description: Saiba como criar bibliotecas e aplicativos com os modelos de projeto disponíveis no Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cf8c0fe0b716cecee19c00bb0b300d4ffdc99355
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894355"
---
# <a name="workflow-project-templates"></a>Modelos de projeto de fluxo de trabalho

Você pode criar fluxos de trabalho, Windows Communication Foundation (WCF) serviços de fluxo de trabalho, atividades personalizadas e designers de atividade personalizados usando modelos de projeto do Visual Studio. Este artigo descreve como criar bibliotecas e aplicativos com os modelos de projeto disponíveis no Visual Studio.

## <a name="create-a-workflow-project"></a>Criar um projeto de Fluxo de Trabalho

O Visual Studio fornece quatro modelos diferentes de projeto de fluxo de trabalho:

- Aplicativo de console de fluxo de trabalho

- Aplicativo de serviço de fluxo de trabalho WCF

- Biblioteca de atividades

- Biblioteca do designer de atividade

Para acessar esses modelos, primeiro instale o componente de **Windows Workflow Foundation** do Visual Studio. Para obter instruções detalhadas, consulte [instalar Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Depois de instalar o componente **Windows Workflow Foundation** , selecione **arquivo**  >  **novo**  >  **projeto**.

1. Pesquise e selecione um modelo de projeto de fluxo de trabalho, por exemplo, o modelo de **aplicativo do console de fluxo de trabalho** .

1. Continue para criar o projeto.

   > [!NOTE]
   > Se você quiser adicionar um novo projeto a uma solução existente, abra essa solução no Visual Studio, clique com o botão direito do mouse na solução em **Gerenciador de soluções** e selecione **Adicionar**  >  **novo projeto**.

## <a name="workflow-console-app"></a>Aplicativo de console de fluxo de trabalho

Se você escolher o modelo de **aplicativo do console de fluxo de trabalho** , o Visual Studio criará uma definição de fluxo de trabalho em XAML. O Designer de Fluxo de Trabalho é aberto e exibe a tela para o fluxo de trabalho que você criou. Para compor um fluxo de trabalho, arraste atividades ou outros itens de fluxo de trabalho da **caixa de ferramentas** para a superfície de design.

## <a name="wcf-workflow-service-app"></a>Aplicativo de serviço de fluxo de trabalho WCF

Se você escolher o modelo de **aplicativo de serviço de fluxo de trabalho do WCF** , o Visual Studio criará uma definição de serviço como XAML. O Designer de Fluxo de Trabalho é aberto no modo de exibição de design com uma <xref:System.Activities.Statements.Sequence> atividade que contém um conjunto de <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> atividades e.

## <a name="activity-library"></a>Biblioteca de atividades

Se você escolher o modelo de **biblioteca de atividades** , o Visual Studio criará uma definição de atividade em XAML. Designer de Fluxo de Trabalho abre e exibe a tela para sua atividade personalizada. Arraste uma atividade da **caixa de ferramentas** para a superfície de design para incluí-la em sua atividade personalizada.

> [!NOTE]
> Você só tem permissão para uma atividade filho no corpo da atividade personalizada. No entanto, essa atividade filho pode ser uma atividade composta, como uma <xref:System.Activities.Statements.Sequence> atividade ou <xref:System.Activities.Statements.Flowchart> atividade.

## <a name="activity-designer-library"></a>Biblioteca do designer de atividade

Se você escolher o modelo de **biblioteca do designer de atividade** , o Visual Studio criará uma definição de designer de atividade em XAML e um arquivo de implementação code-behind. O Designer de Fluxo de Trabalho é aberto e exibe a tela para o designer de atividade. Arraste controles de Windows Presentation Foundation (WPF) da **caixa de ferramentas** para a superfície de design para usá-los em seu designer de atividade personalizado.

Para obter um exemplo de como implementar um designer de atividade personalizado, consulte [como: criar um designer de atividade personalizado](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Designers de atividades personalizadas podem ser usados para atividades personalizadas e para atividades padrão do .NET.

## <a name="see-also"></a>Confira também

- [Usar o Designer de Fluxo de Trabalho](developing-applications-with-the-workflow-designer.md)
- [Fluxos de trabalho de design (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)
