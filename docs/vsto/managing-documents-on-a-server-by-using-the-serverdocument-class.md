---
title: Gerenciar documentos em um servidor usando a classe ServerDocument
description: Saiba como você pode usar a classe ServerDocument no Ferramentas do Visual Studio for Office Runtime para gerenciar vários aspectos de personalizações em nível de documento.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 17a25ca382cfbbc762731afacaa628de616cfe1c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879469"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>Gerenciar documentos em um servidor usando a classe ServerDocument
  Você pode usar a `ServerDocument` classe no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] para gerenciar vários aspectos de personalizações em nível de documento, mesmo que Microsoft Office Word e Microsoft Office Excel não estejam instalados. É possível executar as seguintes tarefas:

- Acessar e modificar dados no cache de dados de um documento ou pasta de trabalho. Para obter mais informações, consulte [trabalhar com dados armazenados em cache no documento](#CachedData).

- Gerencie o assembly de personalização associado a um documento. Para obter mais informações, consulte [gerenciar a personalização do documento](#CustomizationInfo).

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="understand-the-serverdocument-class"></a>Entender a classe ServerDocument
 A `ServerDocument` classe foi projetada para ser usada em computadores que não têm o Office instalado. Portanto, você normalmente usa essa classe em aplicativos que não se integram ao Office, como projetos de console ou projetos de Windows Forms, em vez de projetos do Office. Use a <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe no assembly *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* .

 A `ServerDocument` classe pode ser usada para operar em personalizações em nível de documento que foram criadas usando o [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] .

 Para obter mais informações sobre o tempo de execução das ferramentas do Visual Studio 2010 para Office e as extensões do Office para o .NET Framework, consulte [visão geral do ferramentas do Visual Studio para Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

> [!NOTE]
> Se você tiver um aplicativo herdado que usa a `ServerDocument` classe no `Visual Studio Tools for Office` sistema (versão 3,0 tempo de execução), o `Visual Studio Tools for Office` sistema (versão 3,0 tempo de execução) deverá ser instalado em computadores que executam o aplicativo. O `Visual Studio 2010 Tools for Office runtime` não pode executar esses aplicativos.

## <a name="work-with-cached-data-in-the-document"></a><a name="CachedData"></a> Trabalhar com dados armazenados em cache no documento
 A `ServerDocument` classe fornece membros que você pode usar para trabalhar com o cache de dados em documentos personalizados. Para obter mais informações sobre dados armazenados em cache, consulte armazenar dados em [cache](../vsto/caching-data.md) e [acessar dados em documentos no servidor](../vsto/accessing-data-in-documents-on-the-server.md).

 A tabela a seguir lista os membros que você pode usar para trabalhar com dados armazenados em cache.

|Tarefa|Membro a ser usado|
|----------|-------------------|
|Para determinar se um documento tem um cache de dados.|O método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>.|
|Para acessar os dados armazenados em cache em um documento.<br /><br /> Para obter mais informações, consulte [acessar dados em documentos no servidor](../vsto/accessing-data-in-documents-on-the-server.md).|A propriedade de <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> .|

## <a name="manage-the-document-customization"></a><a name="CustomizationInfo"></a> Gerenciar a personalização do documento
 Você pode usar membros da `ServerDocument` classe para gerenciar o assembly de personalização associado a um documento. Por exemplo, você pode remover programaticamente a personalização de um documento para que o documento não faça mais parte de uma personalização.

 A tabela a seguir lista os membros que você pode usar para gerenciar o assembly de personalização.

|Tarefa|Membro a ser usado|
|----------|-------------------|
|Para determinar se um documento faz parte de uma personalização em nível de documento.|O método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>.|
|Para anexar de forma programática uma personalização a um documento em tempo de execução.<br /><br /> Para obter mais informações, consulte [como: anexar extensões de código gerenciado a documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Um dos <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> métodos.|
|Para remover programaticamente uma personalização de um documento em tempo de execução.<br /><br /> Para obter mais informações, consulte [como: remover extensões de código gerenciado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|O método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>.|
|Para obter a URL do manifesto de implantação que está associado ao documento.|A propriedade de <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A> .|

## <a name="see-also"></a>Confira também
- [Como: anexar extensões de código gerenciado a documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
- [Como remover extensões de código gerenciado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Visão geral do Ferramentas do Visual Studio para Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Dados de cache](../vsto/caching-data.md)
