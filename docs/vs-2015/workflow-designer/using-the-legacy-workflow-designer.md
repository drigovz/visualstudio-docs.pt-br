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
ms.openlocfilehash: 2fa11cd0b29f3b8ee6008b8c0b3369b16812f0e5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302783"
---
# <a name="using-the-legacy-workflow-designer"></a>Usando Designer de Fluxo de Trabalho herdado
[!INCLUDE[wfd2](../includes/wfd2-md.md)] herdado fornecido por [!INCLUDE[vs2010](../includes/vs2010-md.md)] pode ser usado para direcionar [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 É acessada selecionando a opção de **o .NET Framework 3.0** ou a opção de **o .NET Framework 3.5** na lista suspensa para baixo na parte superior da janela de **Novo Projeto** . A opção padrão em [!INCLUDE[vs2010](../includes/vs2010-md.md)] é **o .NET Framework 4** que é usada para criar aplicativos de [!INCLUDE[wf](../includes/wf-md.md)] que direcionam [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].

 ph x="1" /&gt; fornece uma maneira de criar aplicativos graficamente de [!INCLUDE[wfd2](../includes/wfd2-md.md)] usando a interface do usuário e de [!INCLUDE[wf](../includes/wf-md.md)] . aplicativos de[!INCLUDE[wf](../includes/wf-md.md)] são compostos das etapas do processo de fluxo de trabalho chamadas atividades. Para criar um fluxo de trabalho, compor atividades na superfície de design arrastando seus respectivos designer de atividade de **Caixa de Ferramentas** na superfície de design.

 A tabela a seguir lista os principais recursos de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para Windows Workflow Foundation.

|Recurso|Descrição|
|-------------|-----------------|
|Arrastar e soltar de atividades|Arraste atividades de **Caixa de Ferramentas** na superfície de design para criar um fluxo de trabalho.|
|Pesquisador de Propriedades|A janela **Propriedades** padrão no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] é usada para configurar as propriedades de uma atividade.|
|Aplicar Zoom|O ícone de **Nível de Zoom** de binóculos está localizado abaixo de barra de rolagem vertical no lado direito da superfície de design. Clique nos binóculos e selecione uma porcentagem de zoom para fazer com que o gráfico do fluxo de trabalho aumente ou reduza. Você também pode usar o ícone de **panorâmica** opções de cursor de lupa para ampliar e reduzir.|
|Panorâmica|O ícone de **Panorâmica** , um círculo que contém quatro cruzou as setas apontando em quatro direções, está localizado abaixo de barra de rolagem vertical no lado direito da superfície de design logo abaixo do ícone de zoom de binóculos. Se você clicar no ícone de bandeja, oferece de um menu pop-up as seguintes opções de cursor:<br /><br /> -O **zoom no cursor de** lupa permite ampliar clicando na superfície de design.<br />-O **cursor de lupa ampliação** permite que você reduza clicando na superfície de design.<br />-O cursor à mão da **ferramenta de navegação** permite que você "Pegue" e mude a exibição de um fluxo de trabalho na superfície de design.<br />-O cursor de seta **padrão** permite que você alterne de outros cursores de volta para o cursor de seta padrão.|
|Rolagem automático|Se você tiver um grande fluxo de trabalho, convém colocar uma atividade além de exibição da área visível de superfície de design. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permite arrastar uma atividade para a borda da superfície de design mais próxima de onde você deseja colocar a atividade. A superfície de design de exibição os rola automaticamente naquela direção.|
|Marcas inteligentes|As atividades que não são configuradas completamente ou não são configuradas não válida são marcadas com um ícone de ponto de exclamação. Você pode clicar no ícone e ver uma lista suspensa das necessidades de configuração que existem na atividade. Você pode usar a janela de **Propriedades** para configurar corretamente a atividade. Quando todas as propriedades são válidos para atividades, o ícone de ponto de exclamação desaparece.|

## <a name="in-this-section"></a>Nesta seção
 [Janelas de fluxo de trabalho do Visual Studio (herdado)](../workflow-designer/visual-studio-workflow-windows-legacy.md)

 [Criando projetos herdados de fluxo de trabalho](../workflow-designer/creating-legacy-workflow-projects.md)

 [Exibições de fluxo de trabalho sequencial (herdado)](../workflow-designer/sequential-workflow-views-legacy.md)

 [Atividades de fluxo de trabalho herdadas](../workflow-designer/legacy-workflow-activities.md)

 [Usando temas em fluxos de trabalho (herdado)](../workflow-designer/using-themes-in-workflows-legacy.md)

 [Usando o Designer de Fluxo de Trabalho da máquina de estado herdado](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)

 [Usando o designer de atividade herdado](../workflow-designer/using-the-legacy-activity-designer.md)

 [Designer herdado para a ajuda da interface do usuário do Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)

## <a name="see-also"></a>Consulte também
 [Desenvolvendo fluxos de trabalho](https://go.microsoft.com/fwlink?LinkID=65010)