---
title: Visão geral das partes XML personalizadas
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom XML parts [Office development in Visual Studio], about
- Office Open XML Formats [Office development in Visual Studio]
- custom XML parts [Office development in Visual Studio]
- embedding XML data in documents [Office development in Visual Studio]
- XML parts [Office development in Visual Studio]
- XML file formats [Office development in Visual Studio]
- data [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- XML [Office development in Visual Studio], custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- documents [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b94deacad38f40d76b4c8485186bfd563808d912
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64784421"
---
# <a name="custom-xml-parts-overview"></a>Visão geral das partes XML personalizadas
  Você pode inserir dados XML em documentos para alguns Microsoft Office aplicativos. Quando você insere dados XML em um documento, os dados são nomeados como uma *parte XML personalizada*.

 Você pode criar e modificar partes XML personalizadas em um documento usando um suplemento do VSTO ou uma solução em nível de documento no Visual Studio. Você não precisa iniciar o aplicativo Microsoft Office para criar e modificar partes XML personalizadas.

 **Aplica-se a:** As informações neste tópico se aplicam a projetos de nível de documento e a projetos de suplemento do VSTO para Excel, PowerPoint e Word. Para obter mais informações, consulte [recursos disponíveis por aplicativo do Office e tipo de projeto](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> O Visual Studio também permite que você armazene em cache objetos de dados em personalizações em nível de documento. Esse recurso é diferente das partes XML personalizadas, embora haja algumas semelhanças. Para obter mais informações, consulte [dados armazenados em cache em personalizações em nível de documento](../vsto/cached-data-in-document-level-customizations.md).

## <a name="understand-custom-xml-parts"></a>Entender as partes XML personalizadas
 As partes XML personalizadas foram introduzidas no sistema de Microsoft Office de 2007, juntamente com os formatos XML abertos. Esses formatos incluem novos formatos de arquivo baseados em XML para Excel, PowerPoint e Word (como *. xlsx*, *. pptx*e *. docx*). Os documentos nesses formatos consistem em arquivos XML (também chamados de *partes XML*) que são organizados em pastas em um arquivo zip. A maioria das partes XML são partes internas que ajudam a definir a estrutura e o estado do documento. No entanto, os documentos também podem conter partes XML personalizadas, que podem ser usadas para armazenar dados XML arbitrários nos documentos.

 Os formatos de arquivo XML permitem que os aplicativos trabalhem com documentos de maneiras que não são possíveis com os formatos de arquivo binário mais antigos (como *. xls*, *. ppt*e *. doc*). Qualquer aplicativo que possa ler arquivos ZIP pode examinar e modificar o conteúdo dos documentos, mesmo que o Microsoft Office não esteja instalado.

 Para obter mais informações sobre a estrutura de XML aberto e partes XML personalizadas, consulte os seguintes artigos:

- [Apresentando os formatos de arquivo XML abertos do Office (2007)](/previous-versions/office/developer/office-2007/aa338205(v=office.12))

- [Como manipular documentos de formatos XML abertos](/previous-versions/office/developer/office-2007/aa982683(v=office.12))

- [Walkthrough: formato XML do Word 2007](/previous-versions/office/developer/office-2007/bb266220(v=office.12))

- [Compilar documentos do Word 2007 usando formatos XML abertos](/previous-versions/office/developer/office-2007/bb264572(v=office.12))

> [!NOTE]
> O Excel, o Word e o PowerPoint também permitem que você use partes XML personalizadas em documentos que são salvos nos formatos de arquivo binário. No entanto, se um documento for salvo em um formato binário, você não poderá adicionar ou modificar partes XML personalizadas sem iniciar o aplicativo Microsoft Office.

## <a name="create-and-modify-custom-xml-parts"></a>Criar e modificar partes XML personalizadas
 Você pode criar ou modificar partes XML personalizadas quando o documento estiver aberto no aplicativo do Office ou quando o documento for fechado, mesmo se o Microsoft Office não estiver instalado.

### <a name="modify-xml-parts-while-the-office-application-is-running"></a>Modificar partes XML enquanto o aplicativo do Office está em execução
 Você pode trabalhar com partes XML personalizadas usando uma personalização no nível do documento ou um suplemento do VSTO. Se você estiver usando uma personalização em nível de documento, normalmente trabalhará com partes XML personalizadas que estão no documento personalizado. Se você estiver usando um suplemento do VSTO, poderá criar ou modificar partes XML personalizadas em qualquer documento que esteja aberto no aplicativo.

 Para criar uma parte XML personalizada usando o Visual Studio, adicione uma nova <xref:Microsoft.Office.Core.CustomXMLPart> à <xref:Microsoft.Office.Core.CustomXMLParts> coleção no documento. Para obter mais informações, consulte estes tópicos:

- [Como: adicionar partes XML personalizadas a personalizações em nível de documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)

- [Como: adicionar partes XML personalizadas a documentos usando suplementos do VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)

### <a name="modify-xml-parts-without-starting-the-office-application"></a>Modificar partes XML sem iniciar o aplicativo do Office
 Você pode adicionar ou modificar uma parte XML personalizada sem iniciar o Excel, o PowerPoint ou o Word. Isso será útil se você quiser trabalhar com dados XML em um computador que não tenha aplicativos Microsoft Office instalados, como um servidor do.

 Para adicionar uma parte XML personalizada sem iniciar Microsoft Office, use classes no SDK de XML aberto. Essas classes são projetadas para fornecer acesso ao conteúdo Open XML que é específico para documentos do Office. Por exemplo, para adicionar uma parte XML personalizada a uma pasta de trabalho do Excel, você usa o <xref:DocumentFormat.OpenXml.Packaging.OpenXmlPartContainer.AddNewPart%2A> método de um <xref:DocumentFormat.OpenXml.Packaging.WorkbookPart> objeto. Para obter mais informações, consulte [Open XML SDK](/office/open-xml/open-xml-sdk).

## <a name="bind-custom-xml-parts-to-word-content-controls"></a>Associar partes XML personalizadas a controles de conteúdo do Word
 Você pode associar controles de conteúdo em uma solução do Word a elementos em uma parte XML personalizada. Quando um controle de conteúdo está associado a uma parte XML personalizada, os dados na parte XML personalizada são exibidos na interface do usuário (IU) do controle de conteúdo. Se um usuário editar texto no controle, o elemento XML correspondente será atualizado automaticamente. Da mesma forma, se os valores de elemento nas partes XML personalizadas forem alterados, os controles de conteúdo associados aos elementos XML exibirão os novos dados. Para obter mais informações, consulte [controles de conteúdo](../vsto/content-controls.md).

## <a name="see-also"></a>Confira também
- [Esquemas e dados XML em personalizações em nível de documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
- [Como: adicionar partes XML personalizadas a personalizações em nível de documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
- [Como: adicionar partes XML personalizadas a documentos usando suplementos do VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
- [Controles de conteúdo](../vsto/content-controls.md)
- [Walkthrough: associar controles de conteúdo a partes XML personalizadas](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)
