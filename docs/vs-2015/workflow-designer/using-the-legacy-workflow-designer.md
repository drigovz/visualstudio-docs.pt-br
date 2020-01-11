---
title: Usando o Designer de Fluxo de Trabalho herdado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72c92b4431c21c27bc1fe2ff86b24c850cc34694
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846088"
---
# <a name="using-the-legacy-workflow-designer"></a>Usando Designer de Fluxo de Trabalho herdado
[!INCLUDE[wfd2](../includes/wfd2-md.md)] herdado fornecido por [!INCLUDE[vs2010](../includes/vs2010-md.md)] pode ser usado para direcionar [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Ele é acessado selecionando a opção **.NET Framework 3,0** ou a opção **.NET Framework 3,5** na lista suspensa na parte superior da janela **novo projeto** . A opção padrão em [!INCLUDE[vs2010](../includes/vs2010-md.md)] é **.NET Framework 4** , que é usada para criar [!INCLUDE[wf](../includes/wf-md.md)] aplicativos que se destinam ao [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].

 ph x="1" /&gt; fornece uma maneira de criar aplicativos graficamente de [!INCLUDE[wf](../includes/wf-md.md)] usando a interface do usuário e de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . aplicativos de[!INCLUDE[wf](../includes/wf-md.md)] são compostos das etapas do processo de fluxo de trabalho chamadas atividades. Para criar um fluxo de trabalho, redija as atividades na superfície de design arrastando seus respectivos designers de atividade da **caixa de ferramentas** para a superfície de design.

 A tabela a seguir lista os principais recursos de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para Windows Workflow Foundation.

|Recurso|Descrição|
|-------------|-----------------|
|Arrastar e soltar de atividades|Arraste atividades da **caixa de ferramentas** para a superfície de design para criar um fluxo de trabalho.|
|Pesquisador de Propriedades|A janela **Propriedades** padrão no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] é usada para configurar as propriedades de uma atividade.|
|{1&gt;Zoom&lt;1}|O ícone de **nível de zoom** de binóculos está localizado abaixo da barra de rolagem vertical no lado direito da superfície de design. Clique nos binóculos e selecione uma porcentagem de zoom para fazer com que o gráfico do fluxo de trabalho aumente ou reduza. Você também pode usar o ícone de **panorâmica** opções de cursor de lupa para ampliar e reduzir.|
|Panorâmica|O ícone de **panorâmica** , um círculo que contém quatro setas cruzadas apontando para quatro direções, está localizado abaixo da barra de rolagem vertical no lado direito da superfície de design logo abaixo do ícone de zoom de binóculos. Se você clicar no ícone de bandeja, oferece de um menu pop-up as seguintes opções de cursor:<br /><br /> -O **zoom no cursor de** lupa permite ampliar clicando na superfície de design.<br />-O **cursor de lupa ampliação** permite que você reduza clicando na superfície de design.<br />-O cursor à mão da **ferramenta de navegação** permite que você "Pegue" e mude a exibição de um fluxo de trabalho na superfície de design.<br />-O cursor de seta **padrão** permite que você alterne de outros cursores de volta para o cursor de seta padrão.|
|Rolagem automático|Se você tiver um grande fluxo de trabalho, convém colocar uma atividade além de exibição da área visível de superfície de design. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permite arrastar uma atividade para a borda da superfície de design mais próxima de onde você deseja colocar a atividade. A superfície de design de exibição os rola automaticamente naquela direção.|
|Marcas inteligentes|As atividades que não são configuradas completamente ou não são configuradas não válida são marcadas com um ícone de ponto de exclamação. Você pode clicar no ícone e ver uma lista suspensa das necessidades de configuração que existem na atividade. Em seguida, você pode usar a janela **Propriedades** para configurar a atividade adequadamente. Quando todas as propriedades são válidos para atividades, o ícone de ponto de exclamação desaparece.|

## <a name="in-this-section"></a>Nesta seção
 [Janelas de fluxo de trabalho do Visual Studio (herdado)](../workflow-designer/visual-studio-workflow-windows-legacy.md)

 [Criando projetos herdados de fluxo de trabalho](../workflow-designer/creating-legacy-workflow-projects.md)

 [Exibições de fluxo de trabalho sequencial (herdado)](../workflow-designer/sequential-workflow-views-legacy.md)

 [Atividades de fluxo de trabalho herdadas](../workflow-designer/legacy-workflow-activities.md)

 [Usando temas em fluxos de trabalho (herdado)](../workflow-designer/using-themes-in-workflows-legacy.md)

 [Usando o Designer de Fluxo de Trabalho da máquina de estado herdado](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)

 [Usando o designer de atividade herdado](../workflow-designer/using-the-legacy-activity-designer.md)

 [Designer herdado para a ajuda da interface do usuário do Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)

## <a name="see-also"></a>Veja também
 [Desenvolvendo fluxos de trabalho](https://msdn2.microsoft.com/library/bb628448.aspx)
