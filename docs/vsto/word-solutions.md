---
title: Soluções do Word
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Word
- Office projects [Office development in Visual Studio], Word
- application-level add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio]
- projects [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], about Word solutions
- Office solutions [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], application-level add-ins
- documents [Office development in Visual Studio], Word
- Office development in Visual Studio, Word solutions
- add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Word
- Office documents [Office development in Visual Studio, Word
- document-level customizations [Office development in Visual Studio], Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3cef71cc5f6c4e25d04e6045be7059d81c06b484
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254934"
---
# <a name="word-solutions"></a>Soluções do Word
  O Visual Studio fornece modelos de projeto que você pode usar para criar personalizações em nível de documento e suplementos do VSTO para o Microsoft Office Word. Você pode usar essas soluções para automatizar o Word, estender os recursos do Word e personalizar a interface do usuário do Word. Para obter mais informações sobre as diferenças entre as personalizações em nível de documento e os suplementos do VSTO, consulte [visão &#40;geral&#41;do desenvolvimento de soluções do Office VSTO](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Este tópico fornece as seguintes informações:

- [Automatizar o Word](#automating).

- [Desenvolva personalizações em nível de documento para o Word](#doclevel).

- [Desenvolva suplementos do VSTO para o Word](#applevel).

- [Personalize a interface do usuário do Word](#UI).

## <a name="automating"></a>Automatizar o Word
 O modelo de objeto do Word expõe muitos tipos que você pode usar para automatizar o Word. Por exemplo, você pode criar programaticamente tabelas, formatar documentos e definir o texto em intervalos e parágrafos. Para obter mais informações, consulte [visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md).

 Ao desenvolver soluções do Word no Visual Studio, você também pode usar *itens de host* e controles de *host* em suas soluções. Esses são objetos que estendem determinados objetos comumente usados no modelo de objeto do Word, <xref:Microsoft.Office.Interop.Word.Document> como <xref:Microsoft.Office.Interop.Word.ContentControl> os objetos e. Os objetos estendidos se comportam como os objetos do Word em que se baseiam, mas adicionam eventos adicionais e recursos de associação de dados aos objetos. Para obter mais informações, consulte [automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md).

## <a name="doclevel"></a>Desenvolver personalizações em nível de documento para o Word
 Uma personalização no nível do documento para o Microsoft Office Word consiste em um assembly associado a um documento específico. O assembly normalmente estende o documento Personalizando a interface do usuário e automatizando o Word. Ao contrário de um suplemento do VSTO, que está associado ao próprio Word, a funcionalidade que você implementa em uma personalização está disponível somente quando o documento associado é aberto no Word.

 Para criar um projeto de personalização no nível do documento do Word, use o documento do Word ou modelos de projeto de modelo do Word na caixa de diálogo **novo projeto** do Visual Studio. Para obter mais informações, confira [Como: Crie projetos do Office no Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

 Para obter mais informações sobre como as personalizações no nível de documento funcionam, [arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md).

### <a name="word-customization-programming-model"></a>Modelo de programação de personalização do Word
 Quando você cria um projeto de nível de documento para o Word, o Visual Studio gera uma `ThisDocument`classe, chamada, que é a base da sua solução. Essa classe representa o documento associado à sua solução e fornece um ponto de partida para escrever seu código.

 Para obter mais informações sobre `ThisDocument` a classe e outros recursos que você pode usar em um projeto de nível de documento, consulte [programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md).

## <a name="applevel"></a>Desenvolver suplementos do VSTO para o Word
 Um suplemento do VSTO para o Microsoft Office Word consiste em um assembly que é carregado pelo Word. O assembly normalmente estende o Word Personalizando a interface do usuário e automatizando o Word. Ao contrário de uma personalização em nível de documento, que é associada a um documento específico, a funcionalidade que você implementa em um suplemento do VSTO não é restrita a nenhum documento único.

 Para criar um projeto de suplemento do VSTO para o Word, use os modelos de projeto do suplemento do Word na caixa de diálogo **novo projeto** do Visual Studio. Para obter mais informações, confira [Como: Crie projetos do Office no Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

 Para obter informações gerais sobre como funcionam os suplementos do VSTO, consulte [arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md).

### <a name="word-add-in-programming-model"></a>Modelo de programação de suplemento do Word
 Quando você cria um projeto de suplemento do Word VSTO, o Visual Studio gera uma classe, `ThisAddIn`chamada, que é a base da sua solução. Essa classe fornece um ponto de partida para escrever seu código e também expõe o modelo de objeto do Word para seu suplemento do VSTO.

 Para obter mais informações sobre `ThisAddIn` a classe e outros recursos que você pode usar em um suplemento do VSTO, consulte [programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md).

## <a name="UI"></a>Personalizar a interface do usuário do Word
 Há várias maneiras diferentes de personalizar a interface do usuário do Word. Algumas opções estão disponíveis para todos os tipos de projeto e outras opções estão disponíveis somente para suplementos do VSTO ou personalizações em nível de documento.

### <a name="options-for-all-project-types"></a>Opções para todos os tipos de projeto
 A tabela a seguir lista as opções de personalização disponíveis para as personalizações no nível do documento e os suplementos do VSTO.

|Tarefa|Para obter mais informações|
|----------|--------------------------|
|Personalize a faixa de faixas.|[Visão geral da faixa de faixas](../vsto/ribbon-overview.md)|
|Adicione controles de Windows Forms ou controles de palavra estendidos ao documento personalizado (para uma personalização em nível de documento) ou a qualquer documento aberto (para um suplemento do VSTO).|[Como: Adicionar controles de Windows Forms a documentos do Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Como: Adicionar controles de conteúdo a documentos do Word](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [Como: Adicionar controles de indicador a documentos do Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|

### <a name="options-for-document-level-customizations"></a>Opções para personalizações em nível de documento
 A tabela a seguir lista as opções de personalização disponíveis apenas para personalizações em nível de documento.

|Tarefa|Para obter mais informações|
|----------|--------------------------|
|Adicione um painel Ações ao documento.|[Visão geral do painel Ações](../vsto/actions-pane-overview.md)<br /><br /> [Como: Adicionar um painel de ações a documentos do Word ou a pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Adicione controles de XMLNode e XMLNodes estendidos à superfície do documento.|[Como: Adicionar controles XMLNode a documentos do Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [Como: Adicionar controles de XMLNodes a documentos do Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|

### <a name="options-for-vsto-add-ins"></a>Opções para suplementos do VSTO
 A tabela a seguir lista as opções de personalização disponíveis apenas para os suplementos do VSTO.

|Tarefa|Para obter mais informações|
|----------|--------------------------|
|Crie um painel de tarefas personalizado.|[Painéis de tarefas personalizados](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)|Fornece uma visão geral dos tipos principais fornecidos pelo modelo de objeto do Word.|
|[Automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)|Fornece informações sobre objetos estendidos (fornecidos pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]) que você pode usar em soluções do Word.|
|[Visão geral dos controles de Windows Forms em documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md)|Descreve como você pode adicionar controles de Windows Forms a documentos do Word.|
|[Passo a passo: Crie sua primeira personalização em nível de documento para o Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Demonstra como criar uma personalização básica no nível do documento para o Word.|
|[Passo a passo: Criar seu primeiro suplemento do VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Demonstra como criar um suplemento do VSTO básico para o Word.|
|[Passo a passo: Adicionar controles a um documento em tempo de execução em um suplemento do VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|Demonstra como adicionar um botão de Windows Forms e um <xref:Microsoft.Office.Tools.Word.RichTextContentControl> a um documento em tempo de execução usando um suplemento do VSTO.|
|[Word 2010 no desenvolvimento do Office](http://go.microsoft.com/fwlink/?LinkId=199020)|Fornece links para artigos e documentação de referência sobre como desenvolver soluções de palavras (não específicas do desenvolvimento do Office usando o Visual Studio).|
