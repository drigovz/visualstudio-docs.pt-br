---
title: Dados armazenados em cache em personalizações em nível de documento
description: Saiba como o Visual Studio separa os dados da exibição em personalizações em nível de documento, permitindo que os dados sejam inseridos como um cache de dados.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f1c383b5367b2966b9fd082b2d47570264b4d191
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955769"
---
# <a name="cached-data-in-document-level-customizations"></a>Dados armazenados em cache em personalizações em nível de documento
  Um objetivo principal das personalizações no nível do documento é separar dados da exibição em documentos do Office. Os dados referem-se às informações armazenadas no documento, incluindo números e texto. A exibição refere-se à interface do usuário e ao modelo de objeto do Microsoft Office Word e Microsoft Office Excel.

 O Visual Studio separa os dados da exibição em personalizações em nível de documento, permitindo que os dados sejam inseridos como uma *ilha de dados*, também chamada de *cache de dados*. Você pode ler ou modificar os dados diretamente sem iniciar o Word ou o Excel. Isso é útil quando você precisa modificar dados em documentos em um servidor que não tem Microsoft Office instalado. O Word e o Excel são destinados ao uso em ambientes de cliente; Eles não foram projetados para serem executados em um servidor.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Para obter mais informações sobre personalizações em nível de documento, consulte [visão geral do desenvolvimento de soluções do Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) e [arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md).

## <a name="understand-the-cached-data-programming-model"></a>Entender o modelo de programação de dados em cache
 A ilha de dados pode conter qualquer objeto em sua solução que atenda a determinados requisitos. Esses objetos incluem <xref:System.Data.DataSet> objetos, <xref:System.Data.DataTable> objetos e qualquer outro objeto que possa ser serializado pela <xref:System.Xml.Serialization.XmlSerializer> classe. Para obter mais informações, consulte [armazenar dados em cache](../vsto/caching-data.md).

 Para fornecer a exibição dos dados armazenados em cache, você pode associar controles de Windows Forms e de *host* no documento a objetos na ilha de dados. A vinculação de dados entre a ilha de dados e os controles associados a dados mantém as duas sincronizadas. Você também pode adicionar código de validação aos dados que são independentes dos controles. Para obter mais informações, consulte [associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 Os controles de host são versões estendidas de objetos nativos nos modelos de objetos do Excel e do Word. Ao contrário dos objetos nativos, os controles de host podem ser associados diretamente a objetos de dados gerenciados. Para obter mais informações, consulte Visão geral de [itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md) e [controles de Windows Forms em documentos do Office visão geral](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="access-cached-data-on-the-server"></a>Acessar dados armazenados em cache no servidor
 Para acessar dados armazenados em cache em um documento, você pode usar a <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe. Essa classe faz parte do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] e pode ser usada em um servidor sem executar o Excel ou o Word. Quando o usuário abre o documento depois de modificar os dados armazenados em cache, todos os controles associados aos dados são automaticamente sincronizados com as alterações e o usuário recebe os dados atualizados. Para obter mais informações, consulte [acessar dados em documentos no servidor](../vsto/accessing-data-in-documents-on-the-server.md).

 O Excel e o Word não são necessários para gravar nos dados no servidor, apenas para exibi-lo no cliente. O Excel e o Word não precisam nem ser instalados no servidor. Isso fornece uma escalabilidade aprimorada e a capacidade de executar processamento rápido em lote de documentos que contêm ilhas de dados.

## <a name="data-caching-for-offline-use"></a>Cache de dados para uso offline
 O armazenamento de dados na ilha de dados permite cenários offline. Quando um usuário abre um documento pela primeira vez ou solicita o documento do servidor, a ilha de dados é preenchida com os dados mais recentes. A ilha de dados é armazenada em cache no documento e fica disponível offline. O usuário (e seu código) pode manipular os dados, embora nenhuma conexão dinâmica esteja disponível. Quando o usuário se reconecta, as alterações nos dados podem ser propagadas de volta para uma fonte de dados do servidor.

## <a name="cached-data-and-custom-xml-parts-compared"></a>Dados armazenados em cache e partes XML personalizadas comparadas
 As partes XML personalizadas foram introduzidas no sistema de Microsoft Office de 2007 como uma maneira de armazenar partes arbitrárias de XML em um documento. Embora partes XML personalizadas sejam úteis em muitos dos mesmos cenários que o cache de dados, há algumas diferenças entre a ilha de dados e as partes XML personalizadas. Para obter mais informações sobre partes XML personalizadas, consulte [visão geral de partes XML personalizadas](../vsto/custom-xml-parts-overview.md).

 A tabela a seguir lista algumas das diferenças e semelhanças.

|Pergunta/característica|Cache de dados|Partes XML personalizadas|
|-|----------------|----------------------|
|Quais aplicativos do Office podem usá-los?|Personalizações em nível de documento para os seguintes aplicativos:<br /><br /> -Excel<br />-Palavra|Soluções de nível de documento e de aplicativo para os seguintes aplicativos:<br /><br /> -Excel<br />-PowerPoint<br />-Palavra|
|Quais tipos de dados você pode armazenar?|Qualquer objeto público em seu assembly de personalização que atenda a determinados requisitos. Para obter mais informações, consulte [armazenar dados em cache](../vsto/caching-data.md).|Quaisquer dados XML.|
|Você pode acessar os dados sem iniciar Microsoft Office aplicativos?|Sim, usando a <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe fornecida pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|Sim, usando classes no <xref:System.IO.Packaging> namespace ou usando o SDK de formato XML aberto.|

## <a name="see-also"></a>Confira também
- [Dados em soluções do Office](../vsto/data-in-office-solutions.md)
- [Arquitetura de soluções do Office no Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
