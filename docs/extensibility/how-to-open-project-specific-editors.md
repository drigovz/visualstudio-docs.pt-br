---
title: 'Como: Abrir editores específicos de projetos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3cb6e360a38d64de4976f83b0167d47dc03fbc87
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710836"
---
# <a name="how-to-open-project-specific-editors"></a>Como: Abrir editores específicos de projetos
Se um arquivo de item que está sendo aberto por um projeto estiver intrinsecamente vinculado ao editor específico para esse projeto, o projeto deve abrir o arquivo usando um editor específico do projeto. O arquivo não pode ser delegado ao mecanismo do IDE para selecionar um editor. Por exemplo, em vez de usar um editor de bitmap padrão, você pode usar essa opção de editor específico de projeto para especificar um editor de bitmap específico que reconhece informações no arquivo que são exclusivas do seu projeto.

 O IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> chama o método quando determina que um arquivo deve ser aberto por um projeto específico. Para obter mais informações, consulte [Exibir arquivos usando o comando Abrir arquivo](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Use as seguintes `OpenItem` diretrizes para implementar o método para que seu projeto abra um arquivo usando um editor específico do projeto.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Para implementar o método OpenItem com um editor específico de projeto

1. Ligue <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> para`RDT_EditLock`o método ( ) para determinar se o arquivo (objeto de dados do documento) já está aberto.

    > [!NOTE]
    > Para obter mais informações sobre dados de documentos e objetos de exibição de documentos, consulte [dados do documento e exibição de documentos em editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md).

2. Se o arquivo já estiver aberto, reapareça o arquivo ligando para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> método e especificando um valor de IDO_ActivateIfOpen para o `grfIDO` parâmetro.

     Se o arquivo estiver aberto e o documento for de um projeto diferente do projeto de chamada, um aviso será exibido ao usuário de que o editor que está sendo aberto é de outro projeto. A janela do arquivo é então em si.

3. Se o buffer de texto (objeto de dados do documento) já estiver aberto e você quiser anexar outra exibição a ele, você será responsável por conectar essa exibição. A abordagem recomendada para instanciar uma exibição (objeto de exibição de documento) do projeto é a seguinte:

    1. Ligue `QueryService` para <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> o serviço para <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> obter um ponteiro para a interface.

    2. Chame <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> o método para criar uma instância da classe de exibição de documentos.

4. Ligue <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> para o método, especificando o objeto de exibição do documento.

     Este método siteia o objeto de exibição de documento em uma janela de documento.

5. Realize as chamadas apropriadas para os <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> métodos ou para os <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> métodos.

     Neste ponto, a visão deve ser totalmente inicializada e pronta para ser aberta.

6. Chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> o método para mostrar e abrir a vista.

## <a name="see-also"></a>Confira também
- [Abrir e salvar itens do projeto](../extensibility/internals/opening-and-saving-project-items.md)
- [Como: Abrir editores padrão](../extensibility/how-to-open-standard-editors.md)
- [Como: Abrir editores para documentos abertos](../extensibility/how-to-open-editors-for-open-documents.md)
