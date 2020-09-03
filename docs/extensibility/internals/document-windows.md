---
title: Janelas de documentos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 711033a4ad2e782ecbe509595266426d186bed8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708510"
---
# <a name="document-windows"></a>Janelas de documentos
No Visual Studio, uma *janela de documento* é uma janela filho com quadros que está associada a uma janela MDI (interface de vários documentos). As janelas de documentos normalmente são usadas para a exibição e modificação do código-fonte ou do texto, mas também podem hospedar outros tipos funcionais. Janelas de documentos:

- Pode ser organizado em grupos de guias horizontais ou verticais separados no MDI pai para que vários arquivos possam ser exibidos ao mesmo tempo.

- Pode ser encaixado em qualquer ordem no MDI pai.

- Pode ser flutuante livremente.

- São vinculados em ordem de tabulação a outras janelas MDI.

  Os comandos para agrupamento, encaixe e flutuação podem ser encontrados no menu de atalho para uma guia de janela de documento.

  Para obter mais informações sobre o comportamento da janela no Visual Studio, consulte [Personalizar layouts de janela](../../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="document-window-implementation"></a>Implementação da janela do documento
 As janelas de documentos são criadas com a implementação de um editor. A <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface cria janelas de documentos como parte da instanciação de um editor. Para obter mais informações, consulte [interfaces herdadas no editor](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015).

> [!NOTE]
> Para fornecer pontos de navegação para trás e para frente em uma janela, implemente a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interface. O editor de texto usa marcadores de texto para identificar pontos de navegação no documento.

## <a name="the-running-document-table"></a>A tabela de documentos em execução
 O IDE usa a tabela de documentos em execução (RDT) para acompanhar o status de cada janela do documento. O RDT é o mecanismo pelo qual as janelas de documentos são notificadas sobre eventos, como quando uma solução é fechada ou quando um arquivo é editado. Para obter mais informações, consulte [executando a tabela de documentos](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Confira também
- [Carregamento de documento atrasado](../../extensibility/internals/delayed-document-loading.md)
