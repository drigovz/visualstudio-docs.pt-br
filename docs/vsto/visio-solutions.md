---
title: Soluções do Visio
description: Saiba como você pode usar os suplementos do VSTO para automatizar o Visio, estender os recursos do Visio ou personalizar a interface do usuário do Visio.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9d888a27a8443b6500093a70416414bec453e77e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838038"
---
# <a name="visio-solutions"></a>Soluções do Visio
  O Visual Studio fornece modelos de projeto que você pode usar para criar suplementos do VSTO para Microsoft Office Visio. Você pode usar os suplementos do VSTO para automatizar o Visio, estender os recursos do Visio ou personalizar a interface do usuário do Visio.

 Para obter mais informações sobre os suplementos do VSTO, consulte [introdução à programação de suplementos](../vsto/getting-started-programming-vsto-add-ins.md) do VSTO e [arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md). Se você for novo na programação com o Microsoft Office, consulte Introdução [&#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 **Aplica-se a:** As informações neste tópico se aplicam a projetos de suplemento do VSTO para o Visio 2010. Para obter mais informações, confira [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md) (Funcionalidades disponibilizadas pelo aplicativo do Office e pelo tipo de projeto).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-visio-by-using-the-visio-object-model"></a>Automatizar o Visio usando o modelo de objeto do Visio
 O modelo de objeto do Visio expõe muitas classes que você pode usar para automatizar o Visio a fim de criar diagramas para gráficos organizacionais, fluxogramas, cronogramas de projeto, diagramas de rede, espaços do Office e muito mais. A API permite que você escreva código para realizar tarefas comuns:

- Construa e posicione formas e texto em diagramas.

- Gerencie o comportamento da forma com base na lógica de negócios e na entrada do usuário.

- Visualização do diagrama de controle, como movimento panorâmico e zoom.

- Personalize a interface do usuário do aplicativo.

- Importar dados externos para o Visio, vinculá-los a formas e exibi-los graficamente em uma página.

  Você pode exibir os procedimentos passo a passo e exemplos de código para usar o modelo de objeto do Visio para trabalhar com documentos e formas no [trabalho com documentos do Visio](../vsto/working-with-visio-documents.md) e [trabalhar com formas do Visio](../vsto/working-with-visio-shapes.md).

  Para acessar o modelo de objeto do Visio a partir de um suplemento do VSTO, use o `Application` campo da `ThisAddIn` classe em seu projeto. O `Application` campo retorna um `Microsoft.Office.Interop.Visio.Application` objeto que representa a instância atual do Visio. Para obter mais informações, consulte [programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md).

  Quando você chama o modelo de objeto do Visio, usa tipos que são fornecidos no PIA (assembly de interoperabilidade primária) para o Visio. O PIA atua como uma ponte entre o código gerenciado no suplemento do VSTO e o modelo de objeto COM no Visio. Todos os tipos no PIA do Visio são definidos no `Microsoft.Office.Interop.Visio` namespace. Para obter mais informações sobre assemblies de interoperabilidade primária, consulte [visão geral do desenvolvimento de soluções do office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) e [assemblies de interoperabilidade primária do Office](../vsto/office-primary-interop-assemblies.md).

## <a name="visio-object-model-overview"></a>Visão geral do modelo de objeto do Visio
 Você pode encontrar uma visão geral do modelo de objeto do Visio na [visão geral do modelo de objeto](../vsto/visio-object-model-overview.md)do Visio, que inclui links para a referência do modelo de objeto do Visio e os SDKs.

## <a name="customize-the-user-interface-of-visio"></a>Personalizar a interface do usuário do Visio
 A interface do usuário do Visio tem as seguintes opções de personalização.

|Tarefa|Para obter mais informações|
|----------|--------------------------|
|Personalize a faixa de faixas.|[Visão geral da faixa de opções](../vsto/ribbon-overview.md)|

 Para obter informações sobre como personalizar a interface do usuário do Visio, consulte a documentação de referência do VBA para a classe [Visio. UIObject](/office/vba/api/Visio.UIObject) .

## <a name="see-also"></a>Confira também
- [Introdução à programação de suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Visão geral do desenvolvimento de soluções do Office &#40;&#41;VSTO ](../vsto/office-solutions-development-overview-vsto.md)
- [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md)
- [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)
- [Assemblies de interoperabilidade primária do Office](../vsto/office-primary-interop-assemblies.md)
- [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)
- [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)
- [Visio 2010 no desenvolvimento do Office](/previous-versions/office/developer/office-2010/ff604964(v=office.14))
