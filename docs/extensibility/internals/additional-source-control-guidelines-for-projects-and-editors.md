---
title: Diretrizes adicionais de controle de fonte para projetos e editores | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 181f6c10ff7ce95cd3a37151f117353d1bb47d41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710116"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Diretrizes adicionais de controle de fontes para projetos e editores
Há uma série de diretrizes que projetos e editores devem seguir para apoiar o controle de fontes.

## <a name="guidelines"></a>Diretrizes
 Seu projeto ou editor também deve fazer o seguinte para dar suporte ao controle de origem:

|Área|Project|Editor|Detalhes|
|----------|-------------|------------|-------------|
|Cópias privadas de arquivos|X||O ambiente suporta cópias privadas de arquivos. Ou seja, cada pessoa alistada no projeto tem sua própria cópia privada dos arquivos desse projeto.|
|Persistência ANSI/Unicode|X|X|Se você escrever o código de persistência, persista arquivos no formulário ANSI porque a maioria dos programas de controle de origem não suportam o Unicode no momento.|
|Enumerar arquivos|X||O projeto deve conter uma lista específica de todos os arquivos dentro dele <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> deve ser capaz de enumerar a lista de arquivos usando o ou (VSH_PROPID_First_Child/Next_Sibling). O projeto também deve expor <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> nomes de itens através de sua implementação e procurar nomes de suporte (incluindo arquivos especiais) através de sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> implementação.|
|Formato de texto|X|X|Quando possível, os arquivos devem estar em formato de texto para suportar a fusão de diferentes versões. Arquivos que não estão em formato de texto não podem ser mesclados com outras versões do arquivo mais tarde. O formato de texto preferido é XML.|
|Baseado em referência|X||Projetos baseados em referência são prontamente suportados no controle de origem. No entanto, os projetos baseados em diretórios também são suportados pelo controle de origem, desde que o projeto possa produzir uma lista de seus arquivos sob demanda, independentemente de esses arquivos existirem em disco. Ao abrir um projeto a partir do controle de origem, o arquivo do projeto é derrubado primeiro antes de qualquer um de seus arquivos.|
|Persista objetos e propriedades em ordem previsível|X|X|Persista seus arquivos em uma ordem previsível, como ordem alfabética, para facilitar a fusão.|
|Recarregar|X|X|Quando um arquivo é alterado no disco, o editor deve ser capaz de recarregá-lo. Quando você participa do controle de origem, o ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> recarregará os dados para você, chamando sua implementação. O caso de recarga mais difícil é quando um checkout ocorre quando<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> você chamou IVsQueryEditQuerySave:: e está processando informações. No entanto, seu código de recarga deve ser capaz de ser executado nesta situação.<br /><br /> O ambiente recarrega automaticamente arquivos do projeto. No entanto, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> um projeto deve implementar se tiver hierarquias aninhadas para suportar a recarga de arquivos de projeto aninhados.|

## <a name="see-also"></a>Confira também
- [Controle de origem de suporte](../../extensibility/internals/supporting-source-control.md)
