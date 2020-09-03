---
title: 'Como: criar um projeto de fluxo de trabalho vazio (Herdado) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- projects, empty workflow
- empty workflow projects
- workflows, empty workflow projects
ms.assetid: f81b9cf2-9adb-47a2-936b-cb1851614e19
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d24baf48f74a7e18ee7bb4922ad989fd8e03a38a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662743"
---
# <a name="how-to-create-an-empty-workflow-project-legacy"></a>Como: Crie um fluxo de trabalho vazio Project (o legados)
Siga estas etapas para criar um fluxo de trabalho vazio Projeto usando [!INCLUDE[wfd1](../includes/wfd1-md.md)] herdado fornecido por [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Use [!INCLUDE[wfd2](../includes/wfd2-md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-an-empty-workflow-project"></a>Para criar um projeto vazio de fluxo de trabalho

1. Inicie o Visual Studio.

2. No menu **Arquivo** , aponte para **Novo**e selecione **Projeto**.

     A caixa de diálogo **Novo Projeto** será aberta.

3. Selecione a opção **.NET Framework 3,0** ou a opção **.NET Framework 3,5** na lista suspensa na parte superior da janela **novo projeto** para acessar o designer herdado.

    > [!NOTE]
    > A opção padrão no [!INCLUDE[vs2010](../includes/vs2010-md.md)] é **.NET Framework 4**. Essa opção é usada criar aplicativos de [!INCLUDE[wf](../includes/wf-md.md)] que direcionam [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] e usa o designer herdado.

4. No painel **tipos de projeto** , selecione Visual C# ou Visual Basic (em **outras linguagens**) e, em seguida, selecione **fluxo de trabalho**.

5. No painel **modelos** , selecione **projeto de fluxo de trabalho vazio**.

6. Na caixa **nome** , insira um nome descritivo para o seu projeto para facilitar a identificação.

7. Na caixa **local** , insira o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até ele.

     Se você quiser um diretório de solução criado para o projeto, marque a caixa de seleção **criar diretório para a solução** e insira um nome na caixa **nome da solução** .

8. Clique em **OK**.

## <a name="see-also"></a>Consulte Também
 [Criando projetos herdados de fluxo de trabalho](../workflow-designer/creating-legacy-workflow-projects.md)