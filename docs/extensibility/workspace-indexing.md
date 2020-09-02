---
title: Indexação de espaço de trabalho no Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 9bf7df777d27003fa5763debc772a8804ec28ef5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952682"
---
# <a name="workspace-indexing"></a>Indexação de espaço de trabalho

Em uma solução, os sistemas de projeto são responsáveis por fornecer a funcionalidade de Build, Debug, **goto** Symbol Search e muito mais. Os sistemas de projeto podem fazer esse trabalho porque entendem a relação e os recursos de arquivos dentro de um projeto. Um espaço de trabalho de [pasta aberta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) precisa da mesma percepção para fornecer recursos avançados de IDE também. A coleção e o armazenamento persistente desses dados são um processo chamado indexação de espaço de trabalho. Esses dados indexados podem ser consultados por meio de um conjunto de APIs assíncronas. Os extensores podem participar do processo de indexação, fornecendo <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner> s que sabem como lidar com determinados tipos de arquivos.

## <a name="types-of-indexed-data"></a>Tipos de dados indexados

Há três tipos de dados que são indexados. Observe que o tipo esperado dos scanners de arquivo difere do tipo desserializado do índice.

|Dados|Tipo de scanner de arquivo|Tipo de resultado da consulta de índice|Tipos relacionados|
|--|--|--|--|
|Referências|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Símbolos|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> deve ser usado em vez de `IIndexWorkspaceService` para consultas|
|Valores de dados|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Consultando dados indexados

Há dois tipos assíncronos disponíveis para acessar dados persistentes. A primeira é por meio de <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData> . Ele fornece acesso básico a um único arquivo `FileReferenceResult` e `FileDataResult` dados e armazena os resultados em cache. O segundo é o <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> que não usa o Caching, mas permite mais recursos de consulta.

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Indexing;

private static IIndexWorkspaceData GetCachedIndexedData(IWorkspace workspace)
{
    // Gets access to indexed data wrapped in a cache.
    return workspace?.GetIndexWorkspaceDataService()?.CreateIndexWorkspaceData();
}

private static IIndexWorkspaceService GetDirectIndexedData(IWorkspace workspace)
{
    // Gets direct access to indexed data.
    // Can also be casted to IIndexWorkspaceService2.
    return workspace?.GetIndexWorkspaceService();
}
```

## <a name="participating-in-indexing"></a>Participando da indexação

A indexação do espaço de trabalho aproximadamente segue a seguinte sequência:

1. Descoberta e persistência de entidades do sistema de arquivos no espaço de trabalho (somente na verificação de abertura inicial).
1. Por arquivo, o provedor de correspondência com a prioridade mais alta é solicitado a verificar `FileReferenceInfo` s.
1. Por arquivo, o provedor de correspondência com a prioridade mais alta é solicitado a verificar `SymbolDefinition` s.
1. Por arquivo, todos os provedores são solicitados por `FileDataValue` s.

As extensões podem exportar um scanner implementando `IWorkspaceProviderFactory<IFileScanner>` e exportando o tipo com <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute> . O `SupportedTypes` argumento de atributo deve ser um ou mais valores de <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants> . Para obter um scanner de exemplo, consulte o [exemplo](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs)do SDK do vs.

> [!WARNING]
> Não exportar um scanner de arquivo que ofereça suporte ao `FileScannerTypeConstants.FileScannerContentType` tipo. Ele é usado apenas para fins internos da Microsoft.

Em situações avançadas, uma extensão pode dar suporte dinamicamente a um conjunto arbitrário de tipos de arquivos. Em vez da exportação de MEF `IWorkspaceProviderFactory<IFileScanner>` , uma extensão pode ser exportada `IWorkspaceProviderFactory<IFileScannerProvider>` . Quando a indexação for iniciada, esse tipo de fábrica será importado, instanciado e você terá seu <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> método invocado. `IFileScanner` as instâncias com suporte a qualquer valor de `FileScannerTpeConstants` serão respeitadas, não apenas símbolos.

## <a name="next-steps"></a>Próximas etapas

* [Espaços de trabalho e serviços de idioma](workspace-language-services.md) -saiba como integrar serviços de idiomas em um espaço de trabalho de pasta aberta.
* [Build do espaço de trabalho](workspace-build.md) – abrir pasta dá suporte a sistemas de compilação, como MSBuild e makefiles.