---
title: 'Como: Anexar visualizações aos dados do documento | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d8bd586a9d67996389f3cb6a2b0f13f0afec3bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711084"
---
# <a name="how-to-attach-views-to-document-data"></a>Como: Anexar visualizações aos dados do documento
Se você tiver uma nova exibição de documento, poderá anexá-la a um objeto de dados de documento existente.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Para determinar se você pode anexar uma exibição a um objeto de dados de documento existente

1. Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.

2. Na sua `IVsEditorFactory::CreateEditorInstance`implementação `QueryInterface` do , chamada sobre o objeto `CreateEditorInstance` de dados de documento existente quando o IDE chamar sua implementação.

    A `QueryInterface` chamada permite examinar o objeto de dados do `punkDocDataExisting` documento existente, que está especificado no parâmetro.

    As interfaces exatas que você deve consultar, no entanto, depende do editor que está abrindo o documento, conforme descrito na etapa 4.

3. Se você não encontrar as interfaces apropriadas no objeto de dados do documento existente, então retorne um código de erro ao seu editor indicando que o objeto de dados do documento é incompatível com o seu editor.

    Na implementação do IDE, uma caixa de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>mensagem notifica que o documento está aberto em outro editor e pergunta se você deseja fechá-lo.

4. Se você fechar este documento, então o Visual Studio liga para sua fábrica de editores pela segunda vez. Nesta chamada, `DocDataExisting` o parâmetro é igual a NULL. A implementação da fábrica do editor pode, então, abrir o objeto de dados do documento em seu próprio editor.

   > [!NOTE]
   > Para determinar se você pode trabalhar com um objeto de dados de documento existente, você [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] também pode usar o conhecimento privado da implementação da interface, lançando um ponteiro para a classe real de sua implementação privada. Por exemplo, todos os `IVsPersistFileFormat`editores padrão <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>implementam , que herda de . Assim, você `QueryInterface` pode <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>solicitar , e se o ID de classe no objeto de dados de documento existente corresponder ao ID de classe da sua implementação, então você pode trabalhar com o objeto de dados do documento.

## <a name="robust-programming"></a>Programação robusta
 Quando o Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> chama sua implementação do método, ele repassa `punkDocDataExisting` um ponteiro para o objeto de dados de documento existente no parâmetro, se existir. Examine o objeto de `punkDocDataExisting` dados do documento retornado para determinar se o objeto de dados do documento é apropriado para o seu editor, conforme descrito na nota na etapa 4 do procedimento neste tópico. Se for apropriado, então sua fábrica de editores deve fornecer uma segunda visualização para os dados conforme descrito em [Exibir várias visualizações de documentos](../extensibility/supporting-multiple-document-views.md). Se não, então ele deve exibir uma mensagem de erro apropriada.

## <a name="see-also"></a>Confira também
- [Suporte a várias exibições de documentos](../extensibility/supporting-multiple-document-views.md)
- [Dados de documentos e visualização de documentos em editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md)
