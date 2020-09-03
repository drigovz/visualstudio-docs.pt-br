---
title: 'Como: criar uma biblioteca de atividades de fluxo de trabalho (Herdado) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activity library projects
- workflow activity libraries
- projects, workflow activity libraries
ms.assetid: fb5aa940-2ae8-4b52-b52c-51c20861a7b4
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5bc4566c1ea520ac1050227ac8e4c0aee22e617
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72604958"
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>Como: Crie uma biblioteca de atividade de fluxo de trabalho (o legados)
Siga estas etapas para criar um projeto de biblioteca de atividade de fluxo de trabalho usando [!INCLUDE[wfd1](../includes/wfd1-md.md)] herdado fornecido por [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Use [!INCLUDE[wfd2](../includes/wfd2-md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-workflow-activity-library-project"></a>Para criar um projeto de biblioteca de atividade de fluxo de trabalho

1. Inicie o Visual Studio.

2. No menu **Arquivo** , aponte para **Novo**e selecione **Projeto**.

     A caixa de diálogo **Novo Projeto** será aberta.

3. Selecione a opção **.NET Framework 3,0** ou a opção **.NET Framework 3,5** na lista suspensa na parte superior da janela **novo projeto** para acessar o designer herdado.

    > [!NOTE]
    > A opção padrão no [!INCLUDE[vs2010](../includes/vs2010-md.md)] é **.NET Framework 4**. Essa opção é usada criar aplicativos de [!INCLUDE[wf](../includes/wf-md.md)] que direcionam [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] e usa o designer herdado.

4. No painel **tipos de projeto** , selecione Visual C# ou Visual Basic (em **outras linguagens**) e, em seguida, selecione **fluxo de trabalho**.

5. No painel **modelos** , selecione **biblioteca de atividades de fluxo de trabalho**.

6. Na caixa **nome** , insira um nome descritivo para o seu projeto para facilitar a identificação.

7. Na caixa **local** , insira o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até ele.

     Se você quiser um diretório de solução criado para o projeto, marque a caixa de seleção **criar diretório para a solução** e insira um nome na caixa **nome da solução** .

8. Clique em **OK**.

## <a name="see-also"></a>Consulte Também
 [Criando projetos de fluxo de trabalho herdados](../workflow-designer/creating-legacy-workflow-projects.md) [usando as atividades herdadas do designer de atividades do](../workflow-designer/using-the-legacy-activity-designer.md) [Legacy Workflow Activities](../workflow-designer/legacy-workflow-activities.md) Workflow desenvolvendo atividades de [fluxo](https://msdn.microsoft.com/19876dfc-dfa5-4d52-b1f5-1d087474cc52) de trabalho [Windows Workflow Foundation atividades](https://msdn.microsoft.com/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)