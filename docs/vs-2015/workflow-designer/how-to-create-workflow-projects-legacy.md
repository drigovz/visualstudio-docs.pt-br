---
title: 'Como: Criar projetos de fluxo de trabalho (herdado) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f9c67f16e81bd0176ec25aa490c2119267b94159
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922231"
---
# <a name="how-to-create-workflow-projects-legacy"></a>Como: Criar projetos de fluxo de trabalho (herdado)
Siga estas etapas para criar um projeto de [!INCLUDE[wf](../includes/wf-md.md)] que tem como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]. Este procedimento usa [!INCLUDE[wfd1](../includes/wfd1-md.md)] herdado fornecido por [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
### <a name="to-create-a-workflow-project"></a>Para criar um projeto de fluxo de trabalho  
  
1.  Inicie o [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)].  
  
2.  No menu **Arquivo**, aponte para **Novo** e selecione **Projeto**.  
  
     A caixa de diálogo **Novo Projeto** é aberta.  
  
3.  Selecione o **.NET Framework 3.0** opção ou o **.NET Framework 3.5** opção na lista suspensa na parte superior da lista da **novo projeto** janela para acessar o designer herdado.  
  
    > [!NOTE]
    >  A opção padrão na [!INCLUDE[vs2010](../includes/vs2010-md.md)] está **.NET Framework 4**. Essa opção é usada criar aplicativos de [!INCLUDE[wf](../includes/wf-md.md)] que direcionam [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] e usa o designer herdado.  
  
4.  No **tipos de projeto** painel, selecione projetos do Visual C# ou projetos do Visual Basic e, em seguida, selecione **fluxo de trabalho**.  
  
5.  No **modelos** painel, selecione um dos modelos de projeto instalado:  
  
    -   Aplicativo de console sequencial de fluxo de trabalho  
  
    -   Sequencial biblioteca de fluxo de trabalho  
  
    -   Biblioteca de atividade de fluxo de trabalho  
  
    -   Aplicativo de console do fluxo de trabalho do computador de estado  
  
    -   Biblioteca de fluxo de trabalho do computador de estado  
  
    -   Fluxo de trabalho vazio Projeto  
  
6.  No **nome** , digite um nome descritivo para seu projeto para torná-lo mais fácil identificar.  
  
7.  No **local** , digite o diretório no qual você deseja salvar seu projeto, ou clique em **procurar** para navegar até o diretório.  
  
     Se você quiser um diretório de solução criado para o projeto, selecione a **criar diretório para solução** caixa de seleção e insira um nome na **nome da solução** caixa.  
  
8.  Clique em **OK**.  
  
## <a name="see-also"></a>Consulte também  
 [Criando projetos herdados de fluxo de trabalho](../workflow-designer/creating-legacy-workflow-projects.md)