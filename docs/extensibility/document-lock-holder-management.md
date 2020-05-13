---
title: Gestão do suporte do bloqueio de documentos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9dd520f8ad5cab1f0cfee890c4bcc388c204bb1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712132"
---
# <a name="document-lock-holder-management"></a>Gerenciamento do suporte de bloqueio de documentos

A tabela de documentos em execução (RDT) mantém uma contagem de documentos abertos e quaisquer bloqueios de edição que eles tenham. Você pode colocar um bloqueio de edição em um documento no RDT quando ele é editado programicamente em segundo plano sem que o usuário veja um documento aberto em uma janela de documento. Essa funcionalidade é frequentemente usada por designers que modificam vários arquivos através de uma interface gráfica do usuário.

## <a name="document-lock-holder-scenarios"></a>Cenários de suporte de bloqueio de documento

### <a name="file-a-has-a-dependence-on-file-b"></a>Arquivo "a" tem uma dependência do arquivo "b"

Considere uma situação em que você implemente um editor padrão "A" para o tipo de arquivo "a", e cada arquivo do tipo "a" tem uma referência (ou dependência de) um arquivo do tipo "b". Existe um editor padrão "B" para arquivos do tipo "b". Quando o editor "A" abre o arquivo "a" ele recupera a referência ao arquivo correspondente "b". O arquivo "b" não é exibido, mas o editor "A" pode modificá-lo. O editor "A" obtém uma referência aos dados <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> do documento do arquivo "b" do método e também mantém um bloqueio de edição no arquivo "b". Depois que o editor "A" terminar de modificar o arquivo "b" você pode <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> diminuir a contagem de bloqueio de edição no arquivo "b" chamando o método. Você pode omitir este passo <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> se você `dwRDTLockType` tivesse chamado o método com o parâmetro definido para [_VSRDTFLAGS. RDT_NoLock.](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_NoLock>)

### <a name="file-b-is-opened-by-a-different-editor"></a>Arquivo "b" é aberto por um editor diferente

Caso o arquivo "b" já seja aberto pelo editor "B" quando o editor "A" tentar abri-lo, existem dois cenários separados para lidar:

- Se o arquivo "b" estiver aberto em um editor compatível, você deve ter o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> editor "A" registrar uma trava de edição de documento no arquivo "b" usando o método. Depois que seu editor "A" terminar de modificar o arquivo "b", desregistre o bloqueio de edição de documento usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> método.

- Se o arquivo "b" estiver aberto de forma incompatível, você pode deixar a tentativa de abertura do arquivo "b" pelo editor "A" falhar, ou pode deixar a exibição associada ao editor "A" abrir parcialmente e exibir uma mensagem de erro apropriada. A mensagem de erro deve instruir o usuário a fechar o arquivo "b" no editor incompatível e, em seguida, reabrir o arquivo "a" usando o editor "A". Você também pode [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> implementar o método para solicitar ao usuário que feche o arquivo "b" que está aberto no editor incompatível. Se o usuário fechar o arquivo "b", a abertura do arquivo "a" no editor "A" continua normalmente.

## <a name="additional-document-edit-lock-considerations"></a>Considerações adicionais de bloqueio de edição de documentos

Você tem um comportamento diferente se o editor "A" for o único editor que tem um bloqueio de edição de documento no arquivo "b" do que você teria se o editor "B" também tiver um bloqueio de edição de documento no arquivo "b". In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], **Class Designer** é um exemplo de um designer visual que não mantém um bloqueio de edição no arquivo de código associado. Ou seja, se o usuário tiver um diagrama de classe aberto na exibição de design e o arquivo de código associado aberto simultaneamente, e se o usuário modificar o arquivo de código, mas não salvar as alterações, as alterações também serão perdidas para o arquivo de diagrama de classe (.cd). Se o **Class Designer** tiver o único bloqueio de edição de documento no arquivo de código, o usuário não será solicitado a salvar as alterações ao fechar o arquivo de código. O IDE pede ao usuário para salvar as alterações somente depois que o usuário fecha o **Class Designer**. As alterações salvas são refletidas em ambos os arquivos. Se o **Designer de classe** e o editor de arquivos de código mantiverem bloqueios de edição de documentos no arquivo de código, então o usuário será solicitado a salvar ao fechar o arquivo de código ou o formulário. Nesse ponto, as alterações salvas são refletidas tanto no formulário quanto no arquivo de código. Para obter mais informações sobre diagramas de classe, consulte [Trabalhe com diagramas de classe (Class Designer)](../ide/class-designer/designing-and-viewing-classes-and-types.md).

Observe que se você precisar colocar um bloqueio de edição em um <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> documento para um não-editor, você deve implementar a interface.

Muitas vezes um designer de ia que modifica arquivos de código faz alterações em mais de um arquivo. Nesses casos, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> o método lida com a salvação de um ou mais documentos por meio do **:Você deseja salvar alterações na** caixa de diálogo a seguir?

## <a name="see-also"></a>Confira também

- [Tabela de documentos em execução](../extensibility/internals/running-document-table.md)
- [Persistência e a tabela de documentos em execução](../extensibility/internals/persistence-and-the-running-document-table.md)
