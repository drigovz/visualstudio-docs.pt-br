---
title: Como criar uma biblioteca de fluxo de trabalho de máquina de estado (herdada) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- projects, state machine workflow library
- state machine workflow libraries
- workflows, state machine workflow library
ms.assetid: 5bd68c6e-6a98-47d9-826d-9bb7a4fd72f8
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d3cff5d6aaa28915524b7699affdf41d3bebef4a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663374"
---
# <a name="how-to-create-a-state-machine-workflow-library-legacy"></a>Como: Crie uma biblioteca de fluxo de trabalho do computador de estado (o legados)
Siga estas etapas para criar um projeto de biblioteca de fluxo de trabalho do computador de estado usando [!INCLUDE[wfd1](../includes/wfd1-md.md)] herdado fornecido por [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Use [!INCLUDE[wfd2](../includes/wfd2-md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-state-machine-workflow-library-project"></a>Para criar um projeto de biblioteca de fluxo de trabalho do computador de estado

1. Inicie o Visual Studio.

2. No menu **Arquivo**, aponte para **Novo** e selecione **Projeto**.

     A caixa de diálogo **Novo Projeto** é aberta.

3. Selecione a opção **.NET Framework 3,0** ou a opção **.NET Framework 3,5** na lista suspensa na parte superior da janela **novo projeto** para acessar o designer herdado.

    > [!NOTE]
    > A opção padrão em [!INCLUDE[vs2010](../includes/vs2010-md.md)] é **.NET Framework 4**. Essa opção é usada criar aplicativos de [!INCLUDE[wf](../includes/wf-md.md)] que direcionam [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] e usa o designer herdado.

4. No painel **tipos de projeto** , selecione Visual C# ou Visual Basic (em **outras linguagens**) e, em seguida, selecione **fluxo de trabalho**.

5. No painel **modelos** , selecione **biblioteca de fluxos de trabalho da máquina de estado**.

6. Na caixa **nome** , insira um nome descritivo para o seu projeto para facilitar a identificação.

7. Na caixa **local** , insira o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até ele.

     Se você quiser um diretório de solução criado para o projeto, marque a caixa de seleção **criar diretório para a solução** e insira um nome na caixa **nome da solução** .

8. Clique em **OK**.

## <a name="see-also"></a>Consulte também
 Criando [fluxos de trabalho da máquina de estado](https://msdn.microsoft.com/library/344caacd-bf3b-4716-bd5a-eca74fc5a61d) dos [projetos herdados](../workflow-designer/creating-legacy-workflow-projects.md)