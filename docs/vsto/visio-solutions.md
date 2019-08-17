---
title: Soluções do Visio
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 69d795fe9e4243bbce51e1e137bb6704492bae32
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551276"
---
# <a name="visio-solutions"></a>Soluções do Visio
  O Visual Studio fornece modelos de projeto que você pode usar para criar suplementos do VSTO para Microsoft Office Visio. Você pode usar os suplementos do VSTO para automatizar o Visio, estender os recursos do Visio ou personalizar a interface do usuário do Visio.

 Para obter mais informações sobre os suplementos do VSTO, consulte [introdução à programação de suplementos](../vsto/getting-started-programming-vsto-add-ins.md) do VSTO e [arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md). Se você for novo na programação com o Microsoft Office, consulte [introdução &#40;ao desenvolvimento do Office no&#41;Visual Studio](../vsto/getting-started-office-development-in-visual-studio.md).

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

  Para acessar o modelo de objeto do Visio a partir de um suplemento do VSTO `Application` , use o `ThisAddIn` campo da classe em seu projeto. O `Application` campo retorna um `Microsoft.Office.Interop.Visio.Application` objeto que representa a instância atual do Visio. Para obter mais informações, consulte [programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md).

  Quando você chama o modelo de objeto do Visio, usa tipos que são fornecidos no PIA (assembly de interoperabilidade primária) para o Visio. O PIA atua como uma ponte entre o código gerenciado no suplemento do VSTO e o modelo de objeto COM no Visio. Todos os tipos no pia do Visio são definidos no `Microsoft.Office.Interop.Visio` namespace. Para obter mais informações sobre assemblies de interoperabilidade primária, consulte [ &#40;visão&#41; geral do desenvolvimento de soluções do Office VSTO](../vsto/office-solutions-development-overview-vsto.md) e assemblies de interoperabilidade [primária do Office](../vsto/office-primary-interop-assemblies.md)

## <a name="visio-object-model-overview"></a>Visão geral do modelo de objeto do Visio
 Você pode encontrar uma visão geral do modelo de objeto do Visio na [visão geral do modelo de objeto](../vsto/visio-object-model-overview.md)do Visio, que inclui links para a referência do modelo de objeto do Visio e os SDKs.

## <a name="customize-the-user-interface-of-visio"></a>Personalizar a interface do usuário do Visio
 A interface do usuário do Visio tem as seguintes opções de personalização.

|Tarefa|Para obter mais informações|
|----------|--------------------------|
|Personalize a faixa de faixas.|[Visão geral da faixa de opções](../vsto/ribbon-overview.md)|

 Para obter informações sobre como personalizar a interface do usuário do Visio, consulte a documentação de referência do VBA para a classe [Visio. UIObject](/office/vba/api/Visio.UIObject) .

## <a name="see-also"></a>Consulte também
- [Introdução à programação de suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Visão geral &#40;do desenvolvimento de soluções do Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Como: Criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md)
- [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)
- [Assemblies de interoperabilidade primária do Office](../vsto/office-primary-interop-assemblies.md)
- [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)
- [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)
- [Visio 2010 no desenvolvimento do Office](http://go.microsoft.com/fwlink/?LinkId=199017)
