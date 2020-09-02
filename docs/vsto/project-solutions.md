---
title: Soluções de projeto
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 84dfe7cf86df2139b06a320d1c6441665a08a1b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985631"
---
# <a name="project-solutions"></a>Soluções de projeto
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] fornece modelos de projeto que você pode usar para criar suplementos do VSTO para Microsoft Office projeto. Você pode usar os suplementos do VSTO para automatizar o projeto, estender os recursos do projeto ou personalizar a interface do usuário do projeto.

 Para obter mais informações sobre os suplementos do VSTO, consulte [introdução à programação de suplementos](../vsto/getting-started-programming-vsto-add-ins.md) do VSTO e [arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md). Se você for novo na programação com o Microsoft Office, consulte Introdução [&#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-project-by-using-the-project-object-model"></a>Automatizar o projeto usando o modelo de objeto do projeto
 O modelo de objeto do projeto expõe muitos tipos que você pode usar para automatizar o projeto. Esses tipos permitem que você escreva código para realizar tarefas comuns, como criar e modificar programaticamente tarefas em um projeto.

 Para acessar o modelo de objeto do projeto a partir de um suplemento do VSTO, use o `Application` campo da `ThisAddIn` classe em seu projeto. O `Application` campo retorna um `Microsoft.Office.Interop.MsProject.Application` objeto que representa a instância atual do projeto. Para obter mais informações, consulte [programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md).

 Quando você chama o modelo de objeto do projeto, usa os tipos que são fornecidos no assembly de interoperabilidade primário para o projeto. O assembly de interoperabilidade primário atua como uma ponte entre o código gerenciado no suplemento do VSTO e o modelo de objeto COM no projeto. Todos os tipos no assembly de interoperabilidade primário do projeto são definidos no `Microsoft.Office.Interop.MSProject` namespace. Para obter mais informações sobre assemblies de interoperabilidade primária, consulte [visão geral do desenvolvimento de soluções do office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) e [assemblies de interoperabilidade primária do Office](../vsto/office-primary-interop-assemblies.md).

## <a name="use-the-project-object-model-documentation"></a>Usar a documentação do modelo de objeto do projeto
 Para obter informações completas sobre o modelo de objeto do projeto, você pode consultar a referência do modelo de objeto VBA do projeto. A referência do modelo de objeto do VBA documenta o modelo de objeto do projeto como ele é exposto ao código Visual Basic for Applications (VBA). Para obter mais informações, consulte [referência de modelo de objeto de projeto](/office/vba/api/project.object).

 Todos os objetos e membros na referência do modelo de objeto do VBA correspondem a tipos e membros no PIA (assembly de interoperabilidade primária) do projeto. Por exemplo, o objeto Calendar na referência de modelo de objeto do VBA corresponde ao `Microsoft.Office.Interop.MSProject.Calendar` tipo no pia do projeto. Embora a referência de modelo de objeto do VBA Forneça exemplos de código para a maioria das propriedades, métodos e eventos, você deve converter o código VBA nesta referência para Visual Basic ou Visual C# se quiser usá-los em um projeto de suplemento do VSTO do projeto que você cria usando o Visual Studio.

> [!NOTE]
> Neste momento, não há documentação de referência para o assembly de interoperabilidade primário do projeto.

### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Tipos de infraestrutura no assembly de interoperabilidade primário do projeto
 À medida que você escreve o código que usa o PIA do projeto, você pode observar muitos tipos que não estão descritos na referência do VBA. Esses tipos adicionais ajudam a converter objetos no modelo de objeto baseado em COM do projeto para código gerenciado, não devem ser usados diretamente em seu código.

 Para obter mais informações, consulte [visão geral de classes e interfaces nos assemblies de interoperabilidade primária do Office](/previous-versions/office/office-12/ms247299(v=office.12)).

## <a name="customize-the-user-interface-of-project"></a>Personalizar a interface do usuário do projeto
 Você pode personalizar a interface do usuário do projeto das seguintes maneiras.

|Tarefa|Para obter mais informações|
|----------|--------------------------|
|Adicionar guias personalizadas à faixa de faixas no projeto|[Visão geral da faixa de faixas](../vsto/ribbon-overview.md)|

 Para obter mais informações sobre como personalizar a interface do usuário do Project e de outros aplicativos Microsoft Office, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Confira também
- [Walkthrough: criar seu primeiro suplemento do VSTO para o projeto](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Introdução à programação de suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Visão geral do desenvolvimento de soluções do Office &#40;&#41;VSTO ](../vsto/office-solutions-development-overview-vsto.md)
- [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md)
- [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)
- [Assemblies de interoperabilidade primária do Office](../vsto/office-primary-interop-assemblies.md)
- [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)
- [Projeto 2010 e Project Server 2010 no desenvolvimento do Office](/previous-versions/office/developer/office-2010/ee758031(v=office.14))
