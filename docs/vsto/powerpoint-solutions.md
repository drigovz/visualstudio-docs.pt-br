---
title: Soluções do PowerPoint
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c41b2942b53c97222abf7308b6706a7cdc734df1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985668"
---
# <a name="powerpoint-solutions"></a>Soluções do PowerPoint
  O Visual Studio fornece modelos de projeto que você pode usar para criar suplementos do VSTO para Microsoft Office PowerPoint. Você pode usar os suplementos do VSTO para automatizar o PowerPoint, estender recursos do PowerPoint ou personalizar a interface do usuário do PowerPoint.

 Para obter mais informações sobre os suplementos do VSTO, consulte [introdução à programação de suplementos](getting-started-programming-vsto-add-ins.md) do VSTO e [arquitetura de suplementos do VSTO](architecture-of-vsto-add-ins.md). Se você for novo na programação com o Microsoft Office, consulte Introdução [&#40;desenvolvimento do Office no Visual Studio&#41;](getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_pptallapp](includes/appliesto-pptallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Automatizar o PowerPoint usando o modelo de objeto do PowerPoint
 O modelo de objeto do PowerPoint expõe muitos tipos que você pode usar para automatizar o PowerPoint. Esses tipos permitem que você escreva código para realizar tarefas comuns:

- Crie e formate apresentações de forma programática.

- Adicionar ou remover slides de apresentações.

- Adicionar ou alterar formas em um slide.

  Para acessar o modelo de objeto do PowerPoint a partir de um suplemento do VSTO, use o `Application` campo da `ThisAddIn` classe em seu projeto. O `Application` campo retorna um objeto de [aplicativo](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) que representa a instância atual do PowerPoint. Para obter mais informações, consulte [programar suplementos do VSTO](programming-vsto-add-ins.md).

  Quando você chama o modelo de objeto do PowerPoint, usa os tipos que são fornecidos no assembly de interoperabilidade primário para o PowerPoint. O assembly de interoperabilidade primário atua como uma ponte entre o código gerenciado no suplemento do VSTO e o modelo de objeto COM no PowerPoint. Todos os tipos no assembly de interoperabilidade primário do PowerPoint são definidos no namespace [Microsoft. Office. Interop. PowerPoint](/previous-versions/office/developer/office-2010/ff763170(v=office.14)) . Para obter mais informações sobre assemblies de interoperabilidade primária, consulte [visão geral do desenvolvimento de soluções do office &#40;VSTO&#41;](office-solutions-development-overview-vsto.md) e [assemblies de interoperabilidade primária do Office](office-primary-interop-assemblies.md).

## <a name="use-the-powerpoint-object-model-documentation"></a><a name="WordOMDocumentation"></a> Usar a documentação do modelo de objeto do PowerPoint
 Para obter informações completas sobre o modelo de objeto do PowerPoint, consulte a referência do assembly de interoperabilidade primária do PowerPoint (PIA) e a referência do modelo de objeto do VBA.

### <a name="primary-interop-assembly-reference"></a>Referência de assembly de interoperabilidade primária
 A documentação de referência do PIA do PowerPoint descreve os tipos no assembly de interoperabilidade primária para o PowerPoint. Esta documentação está disponível no seguinte local: [referência de assembly de interoperabilidade primária do PowerPoint 2010](office-primary-interop-assemblies.md).

 Para obter mais informações sobre o design do PIA do PowerPoint, como as diferenças entre classes e interfaces no PIA e como os eventos no PIA são implementados, consulte [visão geral de classes e interfaces nos assemblies de interoperabilidade primária do Office](/previous-versions/office/developer/office-2010/ff759900(v=office.14)).

### <a name="vba-object-model-reference"></a>Referência de modelo de objeto VBA
 A referência do modelo de objeto do VBA documenta o modelo de objeto do PowerPoint como ele é exposto ao código Visual Basic for Applications (VBA). Para obter mais informações, consulte [referência de modelo de objeto do PowerPoint 2010](/office/vba/api/overview/PowerPoint/object-model).

 Todos os objetos e membros na referência do modelo de objeto do VBA correspondem a tipos e membros no PIA (assembly de interoperabilidade primária) do PowerPoint. Por exemplo, o objeto de apresentação na referência de modelo de objeto do VBA corresponde ao tipo de [apresentação](/previous-versions/office/developer/office-2010/ff761925(v=office.14)) no pia do PowerPoint. Embora a referência de modelo de objeto do VBA Forneça exemplos de código para a maioria das propriedades, métodos e eventos, você deve converter o código VBA nesta referência para Visual Basic ou Visual C# se quiser usá-los em um projeto de suplemento do VSTO do PowerPoint que você cria usando o Visual Studio.

## <a name="customize-the-user-interface-of-powerpoint"></a>Personalizar a interface do usuário do PowerPoint
 Você pode modificar a interface do usuário do PowerPoint das seguintes maneiras.

|Tarefa|Para obter mais informações|
|----------|--------------------------|
|Crie um painel de tarefas personalizado.|[Painéis de tarefas personalizados](custom-task-panes.md)|
|Adicione guias personalizadas à faixa de faixas.|[Visão geral da faixa de faixas](ribbon-overview.md)|
|Adicione grupos personalizados a uma guia interna na faixa de bits.|[Como: personalizar uma guia interna](how-to-customize-a-built-in-tab.md)|

 Para obter mais informações sobre como personalizar a interface do usuário do PowerPoint e de outros aplicativos Microsoft Office, consulte [personalização da interface do usuário do Office](office-ui-customization.md).

## <a name="see-also"></a>Confira também
- [Walkthrough: criar seu primeiro suplemento do VSTO para PowerPoint](walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Introdução à programação de suplementos do VSTO](getting-started-programming-vsto-add-ins.md)
- [Visão geral do desenvolvimento de soluções do Office &#40;&#41;VSTO ](office-solutions-development-overview-vsto.md)
- [Arquitetura de suplementos do VSTO](architecture-of-vsto-add-ins.md)
- [Como: criar projetos do Office no Visual Studio](how-to-create-office-projects-in-visual-studio.md)
- [Programar suplementos do VSTO](programming-vsto-add-ins.md)
- [Escrever código em soluções do Office](writing-code-in-office-solutions.md)
- [Assemblies de interoperabilidade primária do Office](office-primary-interop-assemblies.md)
- [Personalização da interface do usuário do Office](office-ui-customization.md)
- [PowerPoint 2010 no desenvolvimento do Office](/previous-versions/office/developer/office-2010/ff604967(v=office.14))
