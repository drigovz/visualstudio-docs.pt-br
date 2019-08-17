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
ms.openlocfilehash: 70968682a8221b88859fd561c9f678aced2911b9
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551475"
---
# <a name="powerpoint-solutions"></a>Soluções do PowerPoint
  O Visual Studio fornece modelos de projeto que você pode usar para criar suplementos do VSTO para Microsoft Office PowerPoint. Você pode usar os suplementos do VSTO para automatizar o PowerPoint, estender recursos do PowerPoint ou personalizar a interface do usuário do PowerPoint.

 Para obter mais informações sobre os suplementos do VSTO, consulte [introdução à programação de suplementos](../vsto/getting-started-programming-vsto-add-ins.md) do VSTO e [arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md). Se você for novo na programação com o Microsoft Office, consulte [introdução &#40;ao desenvolvimento do Office no&#41;Visual Studio](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") Para ver uma demonstração de vídeo relacionada [, consulte Como fazer: Criar um suplemento para o Microsoft PowerPoint? ](http://go.microsoft.com/fwlink/?LinkId=132767).

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Automatizar o PowerPoint usando o modelo de objeto do PowerPoint
 O modelo de objeto do PowerPoint expõe muitos tipos que você pode usar para automatizar o PowerPoint. Esses tipos permitem que você escreva código para realizar tarefas comuns:

- Crie e formate apresentações de forma programática.

- Adicionar ou remover slides de apresentações.

- Adicionar ou alterar formas em um slide.

  Para acessar o modelo de objeto do PowerPoint a partir de um suplemento do VSTO `Application` , use o `ThisAddIn` campo da classe em seu projeto. O `Application` campo retorna um objeto de [aplicativo](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) que representa a instância atual do PowerPoint. Para obter mais informações, consulte [programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md).

  Quando você chama o modelo de objeto do PowerPoint, usa os tipos que são fornecidos no assembly de interoperabilidade primário para o PowerPoint. O assembly de interoperabilidade primário atua como uma ponte entre o código gerenciado no suplemento do VSTO e o modelo de objeto COM no PowerPoint. Todos os tipos no assembly de interoperabilidade primário do PowerPoint são definidos no namespace [Microsoft. Office. Interop. PowerPoint](/previous-versions/office/developer/office-2010/ff763170(v=office.14)) . Para obter mais informações sobre assemblies de interoperabilidade primária, consulte [ &#40;visão&#41; geral do desenvolvimento de soluções do Office VSTO](../vsto/office-solutions-development-overview-vsto.md) e assemblies de interoperabilidade [primária do Office](../vsto/office-primary-interop-assemblies.md)

## <a name="WordOMDocumentation"></a>Usar a documentação do modelo de objeto do PowerPoint
 Para obter informações completas sobre o modelo de objeto do PowerPoint, consulte a referência do assembly de interoperabilidade primária do PowerPoint (PIA) e a referência do modelo de objeto do VBA.

### <a name="primary-interop-assembly-reference"></a>Referência de assembly de interoperabilidade primária
 A documentação de referência do PIA do PowerPoint descreve os tipos no assembly de interoperabilidade primária para o PowerPoint. Esta documentação está disponível no seguinte local: [Referência de assembly de interoperabilidade primária do PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588).

 Para obter mais informações sobre o design do PIA do PowerPoint, como as diferenças entre classes e interfaces no PIA e como os eventos no PIA são implementados, consulte [visão geral de classes e interfaces nos assemblies](http://go.microsoft.com/fwlink/?LinkId=199885)de interoperabilidade primária do Office.

### <a name="vba-object-model-reference"></a>Referência de modelo de objeto VBA
 A referência do modelo de objeto do VBA documenta o modelo de objeto do PowerPoint como ele é exposto ao código Visual Basic for Applications (VBA). Para obter mais informações, consulte [referência de modelo de objeto do PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199770).

 Todos os objetos e membros na referência do modelo de objeto do VBA correspondem a tipos e membros no PIA (assembly de interoperabilidade primária) do PowerPoint. Por exemplo, o objeto de apresentação na referência de modelo de objeto do VBA corresponde ao tipo de [apresentação](/previous-versions/office/developer/office-2010/ff761925(v=office.14)) no pia do PowerPoint. Embora a referência de modelo de objeto do VBA Forneça exemplos de código para a maioria das propriedades, métodos e eventos, você deve converter o código VBA nesta referência C# para Visual Basic ou Visual se quiser usá-los em um projeto de suplemento do VSTO do PowerPoint criado por usando o Visual Studio.

## <a name="customize-the-user-interface-of-powerpoint"></a>Personalizar a interface do usuário do PowerPoint
 Você pode modificar a interface do usuário do PowerPoint das seguintes maneiras.

|Tarefa|Para obter mais informações|
|----------|--------------------------|
|Crie um painel de tarefas personalizado.|[Painéis de tarefas personalizados](../vsto/custom-task-panes.md)|
|Adicione guias personalizadas à faixa de faixas.|[Visão geral da faixa de faixas](../vsto/ribbon-overview.md)|
|Adicione grupos personalizados a uma guia interna na faixa de bits.|[Como: Personalizar uma guia interna](../vsto/how-to-customize-a-built-in-tab.md)|

 Para obter mais informações sobre como personalizar a interface do usuário do PowerPoint e de outros aplicativos Microsoft Office, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Consulte também
- [Passo a passo: Criar seu primeiro suplemento do VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Introdução à programação de suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Visão geral &#40;do desenvolvimento de soluções do Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Como: Criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md)
- [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)
- [Assemblies de interoperabilidade primária do Office](../vsto/office-primary-interop-assemblies.md)
- [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)
- [PowerPoint 2010 no desenvolvimento do Office](http://go.microsoft.com/fwlink/?LinkId=199015)
