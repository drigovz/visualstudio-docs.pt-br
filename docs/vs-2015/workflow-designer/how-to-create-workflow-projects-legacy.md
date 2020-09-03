---
title: 'Como: criar projetos de fluxo de trabalho (herdados) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf68c1a28f662bfa4e271d3c402ef1c8946b6f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668673"
---
# <a name="how-to-create-workflow-projects-legacy"></a>Como: Criar projetos de fluxo de trabalho (o legados)
Siga estas etapas para criar um projeto de [!INCLUDE[wf](../includes/wf-md.md)] que tem como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]. Este procedimento usa [!INCLUDE[wfd1](../includes/wfd1-md.md)] herdado fornecido por [!INCLUDE[vs2010](../includes/vs2010-md.md)].

### <a name="to-create-a-workflow-project"></a>Para criar um projeto de fluxo de trabalho

1. Inicie o [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)].

2. No menu **Arquivo** , aponte para **Novo**e selecione **Projeto**.

     A caixa de diálogo **Novo Projeto** será aberta.

3. Selecione a opção **.NET Framework 3,0** ou a opção **.NET Framework 3,5** na lista suspensa na parte superior da janela **novo projeto** para acessar o designer herdado.

    > [!NOTE]
    > A opção padrão no [!INCLUDE[vs2010](../includes/vs2010-md.md)] é **.NET Framework 4**. Essa opção é usada criar aplicativos de [!INCLUDE[wf](../includes/wf-md.md)] que direcionam [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] e usa o designer herdado.

4. No painel **tipos de projeto** , selecione projetos do Visual C# ou Visual Basic projetos e, em seguida, selecione **fluxo de trabalho**.

5. No painel **modelos** , selecione um dos modelos de projeto instalados:

    - Aplicativo de console sequencial de fluxo de trabalho

    - Sequencial biblioteca de fluxo de trabalho

    - Biblioteca de atividade de fluxo de trabalho

    - Aplicativo de console do fluxo de trabalho do computador de estado

    - Biblioteca de fluxo de trabalho do computador de estado

    - Fluxo de trabalho vazio Projeto

6. Na caixa **nome** , insira um nome descritivo para o seu projeto para facilitar a identificação.

7. Na caixa **local** , insira o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até o diretório.

     Se você quiser um diretório de solução criado para o projeto, marque a caixa de seleção **criar diretório para a solução** e insira um nome na caixa **nome da solução** .

8. Clique em **OK**.

## <a name="see-also"></a>Consulte Também
 [Criando projetos herdados de fluxo de trabalho](../workflow-designer/creating-legacy-workflow-projects.md)