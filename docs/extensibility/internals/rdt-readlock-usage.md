---
title: Uso de RDT_ReadLock | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb897fab61e1e14b52863b5853748c685200d5ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705923"
---
# <a name="rdt_readlock-usage"></a>Uso de RDT_ReadLock

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) é uma bandeira que fornece lógica para o bloqueio de um documento na Tabela de Documentos em Execução (RDT), que é a lista de todos os documentos que estão atualmente abertos no Visual Studio IDE. Este sinalizador determina quando os documentos são abertos e se um documento é visível na interface do usuário ou mantido invisivelmente na memória.

Geralmente, você usa [_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) quando um dos seguintes é verdadeiro:

- Você quer abrir um documento de forma invisível e somente leitura, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> mas ainda não está estabelecido qual deve possuí-lo.

- Você quer que o usuário seja solicitado a salvar um documento que foi invisivelmente aberto antes que o usuário o exibisse na ui e, em seguida, tentasse fechá-lo.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Como gerenciar documentos visíveis e invisíveis

Quando um usuário abre um documento <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> na ui, um proprietário para o documento deve ser estabelecido e um [_VSRDTFLAGS. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) bandeira deve ser definida. Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> nenhum proprietário puder ser estabelecido, o documento não será salvo quando o usuário clicar em **Salvar tudo** ou fechar o IDE. Isso significa que se um documento estiver aberto invisivelmente onde ele é modificado na memória, e o usuário `RDT_ReadLock` for solicitado a salvar o documento no desligamento ou salvo se salvar **tudo** for escolhido, então um não poderá ser usado. Em vez disso, `RDT_EditLock` você <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> deve usar um e registrar um quando um [__VSREGDOCLOCKHOLDER. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) bandeira.

## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock e modificação de documentos

A bandeira anterior mencionada indica que a abertura `RDT_EditLock` invisível do documento produzirá sua quando o documento for aberto pelo usuário em uma **Janela de Documentos**visível . Quando isso ocorre, o usuário é apresentado com um **aviso salvar** quando o **DocumentWindow** visível é fechado. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel`implementações que <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> utilizam o serviço `RDT_ReadLock` funcionam inicialmente quando apenas um é tomado (ou seja, quando o documento é aberto invisivelmente para analisar informações). Posteriormente, se o documento deve ser modificado, então o bloqueio é atualizado para um **RDT_EditLock**fraco . Se o usuário abrir o documento em `CodeModel`uma Janela `RDT_EditLock` **de Documento**visível, o fraco será liberado.

Se o usuário fechar a **DocumentWindow** e escolher **Não** quando solicitado para `CodeModel` salvar o documento aberto, então a implementação elimina todas as informações do documento e reabre o documento do disco invisivelmente na próxima vez que mais informações forem necessárias para o documento. A sutileza desse comportamento é um exemplo em que o usuário abre o **DocumentWindow** do documento aberto invisível, modifica-o, fecha-o e, em seguida, escolhe **Não** quando solicitado a salvar o documento. Neste caso, se o `RDT_ReadLock`documento tiver um , então o documento não será realmente fechado e o documento modificado permanecerá aberto invisivelmente na memória, mesmo que o usuário tenha optado por não salvar o documento.

Se a abertura invisível do `RDT_EditLock`documento usar um fraco, então ele cede seu bloqueio quando o usuário abre o documento visivelmente e nenhum outro bloqueio é mantido. Quando o usuário fecha a **DocumentWindow** e escolhe **Não** quando solicitado para salvar o documento, então o documento deve ser fechado da memória. Isso significa que o cliente invisível deve ouvir os eventos RDT para acompanhar essa ocorrência. Da próxima vez que o documento for exigido, o documento deve ser reaberto.
