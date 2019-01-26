---
title: 'Como: Anexar exibições para dados de documentos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e9aa7b4a36f1d3a073bb13188954a1159012797
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55010032"
---
# <a name="how-to-attach-views-to-document-data"></a>Como: Anexar exibições para dados de documento
Se você tiver uma nova exibição de documento, você poderá anexá-lo a um objeto de dados de documento existente.  
  
## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Para determinar se você pode anexar um modo de exibição para um objeto de dados de documento existente  
  
1. Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2. Em sua implementação de `IVsEditorFactory::CreateEditorInstance`, chame `QueryInterface` sobre o objeto de dados de documento existente quando o IDE chama seu `CreateEditorInstance` implementação.  
  
    Chamando `QueryInterface` permite que você examine o objeto de dados de documento existente, que é especificado no `punkDocDataExisting` parâmetro.  
  
    As interfaces exatas, você deve consultar, no entanto, varia de acordo com o editor que esteja abrindo o documento, conforme descrito na etapa 4.  
  
3. Se você não encontrar as interfaces apropriadas no objeto de dados de documento existente, em seguida, retorne um código de erro para o seu editor, que indica que o objeto de dados do documento é incompatível com seu editor.  
  
    Na implementação do IDE do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, uma caixa de mensagem avisará que o documento está aberto em outro editor e pergunta se você deseja fechá-lo.  
  
4. Se você fechar este documento, o Visual Studio chama sua fábrica de editor para uma segunda vez. Nessa chamada, o `DocDataExisting` parâmetro é igual a NULL. Sua implementação de fábrica do editor, em seguida, poderá abrir o objeto de dados de documento em seu próprio editor.  
  
   > [!NOTE]
   >  Para determinar se você pode trabalhar com um objeto de dados de documento existente, você também pode usar privado Conhecimento da implementação da interface ao converter um ponteiro para o real [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] classe da sua implementação privada. Por exemplo, todos os editores padrão implementam `IVsPersistFileFormat`, que herda de <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. Assim, você pode chamar `QueryInterface` para <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, e se a ID de classe no objeto de dados existente do documento corresponde à sua implementação de ID de classe e, em seguida, você pode trabalhar com o objeto de dados do documento.  
  
## <a name="robust-programming"></a>Programação robusta  
 Quando o Visual Studio chama sua implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método, ele transmitirá de volta um ponteiro para o objeto de dados de documento existente no `punkDocDataExisting` parâmetro, se houver. Examinar o objeto de dados de documento retornado no `punkDocDataExisting` para determinar se o objeto de dados de documento é apropriado para seu editor, conforme descrito na observação na etapa 4 do procedimento neste tópico. Se é apropriado e, em seguida, sua fábrica de editor deve fornecer um segundo modo de exibição para os dados conforme descrito na [dar suporte a vários modos de exibição de documento](../extensibility/supporting-multiple-document-views.md). Caso contrário, em seguida, ele deve exibir uma mensagem de erro apropriado.  
  
## <a name="see-also"></a>Consulte também  
 [Suporte a vários modos de exibição de documento](../extensibility/supporting-multiple-document-views.md)   
 [Dados de documentos e exibição de documentos em editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md)