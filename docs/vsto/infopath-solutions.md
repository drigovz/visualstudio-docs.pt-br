---
title: Soluções InfoPath
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d227e3c87810156e6e4262a79cfcc9b126d68417
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551748"
---
# <a name="infopath-solutions"></a>Soluções InfoPath
  O Visual Studio fornece modelos de projeto que você pode usar para criar suplementos do VSTO para Microsoft Office InfoPath 2013 e InfoPath 2010. O InfoPath não está disponível no Office 2016.

> [!NOTE]
> Você ainda poderá criar um suplemento do VSTO para o InfoPath mesmo se tiver instalado o Office 2016. Basta instalar o InfoPath 2013 ou o Office 2013 lado a lado com o Office 2016.

 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Os suplementos do VSTO para InfoPath são semelhantes aos suplementos do VSTO para outros aplicativos Microsoft Office. Esses tipos de soluções consistem em um assembly que é carregado pelo aplicativo. Os usuários finais podem ter acesso à funcionalidade desse assembly, não importa qual modelo de formulário ou formulário está aberto. Para obter mais informações sobre os suplementos do VSTO, consulte [introdução à programação de suplementos](../vsto/getting-started-programming-vsto-add-ins.md) do VSTO e [arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> O Visual Studio 2015 não inclui os projetos de modelo de formulário do InfoPath que foram fornecidos em versões anteriores do Visual Studio. Você também não pode usar o Visual Studio 2015 para abrir ou editar um projeto de modelo de formulário do InfoPath que foi criado em uma versão anterior do Visual Studio. No entanto, você pode abrir e editar um projeto de modelo de formulário do InfoPath usando Visual Studio Tools for Applications. Para obter mais informações, consulte [trabalhar com projetos do VSTO 2008 no InfoPath 2010.](http://go.microsoft.com/fwlink/?LinkID=218903)

## <a name="automate-infopath-by-using-an-add-in"></a>Automatizar o InfoPath usando um suplemento
 Para acessar o modelo de objeto do InfoPath por meio de um suplemento do VSTO do Office criado usando as ferramentas de desenvolvimento do Office `Application` no Visual Studio `ThisAddIn` , use o campo da classe em seu projeto. O `Application` campo retorna um <xref:Microsoft.Office.Interop.InfoPath.Application> objeto que representa a instância atual do InfoPath. Para obter mais informações, consulte [programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md).

 Quando você chama o modelo de objeto do InfoPath de um suplemento do VSTO, usa tipos que são fornecidos no assembly de interoperabilidade primário para o InfoPath. O assembly de interoperabilidade primário atua como uma ponte entre o código gerenciado no suplemento do VSTO e o modelo de objeto COM no InfoPath. Todos os tipos no assembly de interoperabilidade primário do InfoPath <xref:Microsoft.Office.Interop.InfoPath> são definidos no namespace. Para obter mais informações sobre o assembly de interoperabilidade primário do InfoPath, consulte [sobre o Microsoft Office assembly de interoperabilidade primário do InfoPath](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72). Para obter mais informações sobre assemblies de interoperabilidade primária em geral, consulte [ &#40;visão&#41; geral do desenvolvimento de soluções do Office VSTO](../vsto/office-solutions-development-overview-vsto.md) e assemblies de interoperabilidade [primária do Office](../vsto/office-primary-interop-assemblies.md).

## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>Personalizar a interface do usuário do InfoPath usando um suplemento
 Ao criar um suplemento do VSTO para o InfoPath, você tem várias opções de personalização de interface do usuário diferentes. A tabela a seguir lista algumas dessas opções.

|Tarefa|Para obter mais informações|
|----------|--------------------------|
|Crie um painel de tarefas personalizado.|[Painéis de tarefas personalizados](../vsto/custom-task-panes.md)|
|Adicione guias personalizadas à faixa de faixas no InfoPath.|[Personalizar uma faixa de faixas para o InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|

 Para obter mais informações sobre como personalizar a interface do usuário do InfoPath e outros aplicativos Microsoft Office, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Consulte também
- [Sobre o Microsoft Office assembly de interoperabilidade primário do InfoPath](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72)
- [Introdução à programação de suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Visão geral &#40;do desenvolvimento de soluções do Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Como: Criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md)
- [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)
- [Assemblies de interoperabilidade primária do Office](../vsto/office-primary-interop-assemblies.md)
- [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)
- [InfoPath 2010 no desenvolvimento do Office](http://go.microsoft.com/fwlink/?LinkId=199012)
