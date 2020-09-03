---
title: Visão geral dos modelos do Office Project
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], about project templates
- Excel Workbook project template
- Word Template project template
- Excel [Office development in Visual Studio], project templates
- Project [Office development in Visual Studio], project templates
- project templates [Office development in Visual Studio]
- project templates, Word
- InfoPath [Office development in Visual Studio], project templates
- Excel Template project template
- project templates, 2007 Microsoft Office system
- project templates, Excel
- PowerPoint [Office development in Visual Studio], project templates
- Word [Office development in Visual Studio], Word project templates
- Office projects [Office development in Visual Studio], templates
- Excel projects in Visual Studio
- Word Document project template
- Visio [Office development in Visual Studio], project templates
- Word projects in Visual Studio
- Outlook [Office development in Visual Studio], project templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d83b04795386cfec80a8a309a9a84da04f6df105
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68926597"
---
# <a name="office-project-templates-overview"></a>Visão geral dos modelos do Office Project
  O Microsoft Office Developer Tools no Visual Studio inclui modelos de projeto para criação dos seguintes tipos de solução do Office:

- [Personalizações no nível de documento](#DocLevel)

- [Suplementos do VSTO](#AppLevel)

  Para obter uma comparação detalhada desses tipos de soluções do Office, consulte [visão geral do desenvolvimento de soluções do office &#40;&#41;do VSTO ](../vsto/office-solutions-development-overview-vsto.md).

  Os modelos de projeto do Office estão disponíveis na caixa de diálogo **novo projeto** , sob o nó do **Office** do **Visual C#** e **Visual Basic** nós de linguagem. Cada modelo gera um projeto com configuração adequada para o aplicativo de destino, incluindo referências de assembly e configurações de depuração.

  Cada projeto fornece arquivos e código para que você comece em um tipo de solução específico. O código gerado para cada projeto inclui manipuladores de eventos de inicialização e desligamento. Você pode adicionar código a esses manipuladores de eventos para inicializar sua solução quando ela for carregada e limpá-la quando ela for descarregada. Para obter mais informações, consulte [projetos do Office no ambiente do Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md) e [eventos em projetos do Office](../vsto/events-in-office-projects.md).

> [!NOTE]
> As ferramentas de desenvolvimento do Office estão incluídas em determinadas edições do Visual Studio. Para obter mais informações, consulte [configurar um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

## <a name="document-level-customizations"></a><a name="DocLevel"></a> Personalizações em nível de documento
 O nó **Office** na caixa de diálogo **novo projeto** fornece os seguintes modelos de projeto para ajudá-lo a começar a criar personalizações em nível de documento para o Word e o Excel:

- **Documento do VSTO do Word 2013 e 2016**

- **Modelo do VSTO do Word 2013 e 2016**

- **Pasta de trabalho do VSTO do Excel 2013 e 2016**

- **Modelo do VSTO do Excel 2013 e 2016**

- **Documento do Word 2010 VSTO**

- **Modelo do VSTO do Word 2010**

- **Pasta de trabalho do VSTO do Excel 2010**

- **Modelo do VSTO do Excel 2010**

  Os modelos de projeto da Pasta de Trabalho do Excel e do Documento do Word fornecem código para que você comece a criar uma solução que se baseie em uma pasta de trabalho ou em um documento específico. Nesses tipos de solução, seu código é executado apenas quando o documento associado é aberto no Word ou Excel.

  Os modelos de projeto do Modelo do Excel e Modelo do Word se comportam de forma idêntica aos modelos de projeto da Pasta de Trabalho do Excel e do Documento do Word. No entanto, os modelos de projeto do Modelo do Word e Modelo do Excel tornam mais fácil para os usuários criar novas cópias locais de documento ou pasta de trabalho do modelo personalizado em sua solução. Os recursos em sua solução estão disponíveis no novo documento que o usuário cria do modelo.

> [!NOTE]
> Modelos do Word que referenciam extensões de código gerenciado não podem ser usados como suplementos globais do VSTO. O assembly não será chamado se o modelo for carregado a partir do diretório de inicialização do Word. Para obter mais informações, consulte [limitações de modelos globais e suplementos do Excel (arquivos. xla)](#Limitations).

 Para obter informações sobre como começar esses tipos de projeto, consulte os seguintes tópicos:

- [Programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md)

- [Soluções do Word](../vsto/word-solutions.md)

- [Soluções do Excel](../vsto/excel-solutions.md)

- [Walkthrough: criar sua primeira personalização em nível de documento para o Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)

- [Walkthrough: criar sua primeira personalização em nível de documento para o Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)

## <a name="vsto-add-ins"></a><a name="AppLevel"></a> Suplementos do VSTO
 O nó **Office/SharePoint** na caixa de diálogo **novo projeto** fornece os seguintes modelos de projeto para começar a criar suplementos do VSTO.

- **Suplemento do VSTO do Excel 2013 e 2016**

- **Suplemento do VSTO do InfoPath 2013**

- **Suplemento do VSTO do Outlook 2013 e 2016**

- **Suplemento do PowerPoint 2013 e 2016**

- **Suplemento do Project 2013 e 2016**

- **Suplemento do Visio 2013 e 2016**

- **Suplemento do Word 2013 e 2016**

- **Suplemento do Excel 2010**

- **Suplemento do InfoPath 2010**

- **Suplemento do Outlook 2010**

- **Suplemento do PowerPoint 2010**

- **Suplemento do Project 2010**

- **Suplemento do Visio 2010**

- **Suplemento do Word 2010**

  Quando você cria um projeto que se baseia em um desses modelos de projeto, o código na sua solução é executado quando o aplicativo associado é aberto. Diferentemente dos projetos no nível de documento, seu código não é associado a um único documento.

  Para obter mais informações sobre como começar esses tipos de projeto, consulte os seguintes tópicos:

- [Introdução à programação de suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md)

- [Programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md)

- [Walkthrough: criar seu primeiro suplemento do VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Walkthrough: criar seu primeiro suplemento do VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Walkthrough: criar seu primeiro suplemento do VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Walkthrough: criar seu primeiro suplemento do VSTO para o projeto](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Walkthrough: criar seu primeiro suplemento do VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

## <a name="document-vs-template-solutions"></a>Documentar versus soluções de modelo
 Quando você cria uma solução em torno de uma pasta de trabalho do Excel e de um documento do Word, é preciso decidir a melhor maneira de disponibilizar esse documento a seus usuários.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Em algumas situações, talvez seja conveniente fornecer uma cópia de um documento para cada usuário. Nesse caso, crie sua solução usando um projeto de documento do Excel ou Word.

 Em outras situações, talvez seja conveniente tornar um modelo disponível em um servidor, de modo que cada usuário possa abrir o modelo e salvar uma cópia local como um documento. Nesse caso, crie sua solução usando um projeto de modelo do Excel ou Word.

## <a name="comparison"></a>Comparação
 A tabela a seguir descreve as diferenças entre documentos e modelos.

|Documentos|Modelos|
|---------------|---------------|
|Os usuários podem abrir e modificar um documento, a menos que ele seja definido para ser somente leitura. Todas as alterações salvas são mantidas no original.|Os usuários podem abrir um modelo para criar uma cópia local como um novo documento. Eles não podem modificar o original, a menos que recebam permissões especiais.|
|Quando aberto, o documento gera o evento <xref:Microsoft.Office.Tools.Word.Document.Open>.|Quando aberto, o modelo gera o evento <xref:Microsoft.Office.Tools.Word.Document.New>.|

## <a name="limitations-of-global-templates-and-excel-add-ins-xla-files"></a><a name="Limitations"></a> Limitações de modelos globais e suplementos do Excel (arquivos. xla)
 Documentos, pastas de trabalho e modelos podem não funcionar corretamente como modelos globais ou suplementos do VSTO do Excel (arquivos. xla).

## <a name="word-templates"></a>Modelos do Word
 Se um modelo do Microsoft Office Word tiver extensões de código gerenciado, o assembly do projeto não será chamado se o modelo for anexado como um modelo global ou carregado do diretório de inicialização do Word. Além disso, o documento não reconhece o formato de um modelo que faz parte de uma solução do Office.

## <a name="excel-add-ins-xla-files"></a>Suplementos do Excel (arquivos. xla)
 Não há nenhum projeto do Office para criar um suplemento do VSTO do Excel (arquivo *. xla* ). É possível salvar uma pasta de trabalho como um arquivo .xla, mas não é uma operação com suporte e não é recomendada. Se você salvar uma pasta de trabalho que tem extensões de código gerenciado como um arquivo **Microsoft Office suplemento do Excel ( \* . xla)** , poderá selecioná-la na caixa de diálogo **suplementos** para aplicar a outra pasta de trabalho. Em alguns casos, seu código será executado na pasta de trabalho de destino depois que o suplemento do VSTO for aplicado, mas não há suporte para o uso da solução do Office.

## <a name="see-also"></a>Confira também
- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)
- [Desenvolver soluções do Office](../vsto/developing-office-solutions.md)
- [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Introdução à programação de personalizações em nível de documento para o Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Introdução à programação de personalizações em nível de documento para o Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [Introdução à programação de suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
