---
title: Suporte a múltiplas visualizações de documentos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a952414fa7156d80675564e519e556ccedd524a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699547"
---
# <a name="supporting-multiple-document-views"></a>Dando suporte a várias exibições de documento
Você pode fornecer mais de uma visualização de um documento criando dados de documentos separados e objetos de exibição de documentos para o seu editor. Alguns casos em que uma exibição de documento adicional seria útil são:

- Suporte a novas janelas: Você quer que seu editor forneça duas ou mais visualizações do mesmo tipo, para que um usuário que já tenha uma janela aberta no editor possa abrir uma nova janela selecionando o comando **Nova janela** no menu **Janela.**

- Suporte a exibição de formulário e código: Você deseja que seu editor forneça visualizações de diferentes tipos. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], por exemplo, fornece uma exibição de formulário e uma exibição de código.

  Para obter mais informações sobre isso, consulte o procedimento CreateEditorInstance no arquivo EditorFactory.cs no projeto de editor personalizado criado pelo Visual Studio Package Template. Para obter mais informações sobre este projeto, consulte [Passo a Passo: Criando um Editor Personalizado](../extensibility/walkthrough-creating-a-custom-editor.md).

## <a name="synchronizing-views"></a>Sincronizando visualizações
 Quando você implementa várias visualizações, o objeto de dados do documento é responsável por manter todas as visualizações sincronizadas com os dados. Você pode usar as interfaces <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> de manipulação de eventos para sincronizar várias visualizações com os dados.

 Se você não <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> usar o objeto para sincronizar várias visualizações, então você deve implementar seu próprio sistema de eventos para lidar com alterações feitas no objeto de dados do documento. Você pode usar diferentes níveis de granularidade para manter várias visualizações atualizadas. Com uma configuração de máxima granularidade, como você digita em uma visualização as outras visualizações são atualizadas imediatamente. Com granularidade mínima, outras visualizações não são atualizadas até que sejam ativadas.

## <a name="determining-whether-document-data-is-already-open"></a>Determinando se os dados do documento já estão abertos
 A tabela de documentos em execução (RDT) no ambiente de desenvolvimento integrado (IDE) ajuda a rastrear se os dados de um documento já estão abertos, como mostrado no diagrama a seguir.

 ![Gráfico DocDataView](../extensibility/media/docdataview.gif "Docdataview") Múltiplas visualizações

 Por padrão, cada exibição (objeto de exibição<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>do documento) está contida em seu próprio quadro de janela ( ). Como já observado, no entanto, os dados do documento podem ser exibidos em várias visualizações. Para habilitar isso, o Visual Studio verifica o RDT para determinar se o documento em questão já está aberto em um editor. Quando o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> para criar o editor, um `punkDocDataExisting` valor não NULA retornado no parâmetro indica que o documento já está aberto em outro editor. Para obter mais informações sobre como o RDT funciona, consulte [Executando a tabela de documentos](../extensibility/internals/running-document-table.md).

 Em <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> sua implementação, examine o `punkDocDataExisting` objeto de dados do documento retornado para determinar se os dados do documento são apropriados para o seu editor. (Por exemplo, apenas dados HTML devem ser exibidos por um editor HTML.) Se for apropriado, então sua fábrica de editores deve fornecer uma segunda visão para os dados. Se `punkDocDataExisting` o parâmetro `NULL`não estiver, é possível que o objeto de dados do documento esteja aberto em outro editor, ou, mais provavelmente, que os dados do documento já estão abertos em uma visão diferente com o mesmo editor. Se os dados do documento forem abertos em um editor diferente que sua fábrica de editores não suporta, então o Visual Studio não abrirá sua fábrica de editores. Para obter mais informações, [consulte Como: Anexar visualizações a dados de documentos](../extensibility/how-to-attach-views-to-document-data.md).
