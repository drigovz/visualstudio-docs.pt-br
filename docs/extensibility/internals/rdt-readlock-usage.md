---
title: RDT_ReadLock Usage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c11cee4c1f8c150fc8bcf42b3dbc1a193d3441a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341350"
---
# <a name="rdtreadlock-usage"></a>Uso de RDT_ReadLock

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) é um sinalizador que fornece a lógica para bloquear um documento no executando o documento de tabela (RDT), que é a lista de todos os documentos estão abertos no IDE do Visual Studio. Este sinalizador determina quando os documentos estão abertos, e se um documento está visível na interface do usuário ou mantido de forma invisível na memória.

Geralmente, você usa [_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) quando uma das seguintes opções for verdadeira:

- Você deseja abrir um documento de forma invisível e somente leitura, mas ele ainda não tiver sido estabelecida que <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> deve possuí-lo.

- Você deseja que o usuário para ser solicitado a salvar um documento que foi aberto invisivelmente antes do usuário exibido-lo na interface do usuário e, em seguida, tentou fechá-lo.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Como gerenciar documentos visíveis e invisíveis

Quando um usuário abre um documento na interface do usuário, uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> proprietário para o documento deve ser estabelecido e um [_VSRDTFLAGS. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) sinalizador deve ser definido. Se nenhum <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> proprietário pode ser estabelecido e, em seguida, o documento não será salvo quando o usuário clica **Salvar tudo** ou fecha o IDE. Isso significa que se um documento é aberto modo invisível onde ele foi modificado na memória, e o usuário é solicitado a salvar o documento no desligamento ou salvo se **Salvar tudo** for escolhido, então um `RDT_ReadLock` não pode ser usado. Em vez disso, você deve usar um `RDT_EditLock` e registrar um <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> quando um [__VSREGDOCLOCKHOLDER. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) sinalizador.

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock e modificação do documento

O sinalizador anterior mencionado indica que produzirá a abertura invisível do documento de seu `RDT_EditLock` quando o documento é aberto pelo usuário em um visíveis **DocumentWindow**. Quando isso ocorre, o usuário é apresentado com uma **salvar** solicitar quando o visíveis **DocumentWindow** está fechado. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` as implementações que usam o <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> serviço inicialmente funciona quando somente um `RDT_ReadLock` é executada (ou seja, quando o documento for aberto de forma invisível para analisar as informações). Posteriormente, se o documento deve ser modificado, em seguida, o bloqueio é atualizado para uma fraca **RDT_EditLock**. Se o usuário abre o documento em um visíveis **DocumentWindow**, o `CodeModel`do fraco `RDT_EditLock` é liberado.

Se o usuário, em seguida, fecha o **DocumentWindow** e escolhe **não** quando solicitado a salvar o documento aberto, em seguida, a `CodeModel` implementação descarta todas as informações do documento e reabra o documento do disco de forma invisível na próxima vez em que mais informações são necessárias para o documento. A sutileza desse comportamento é uma instância em que o usuário abre o **DocumentWindow** do documento aberto invisível, modifica, fecha e, em seguida, escolhe **não** quando for solicitado a salvar o documento. Nesse caso, se o documento possui um `RDT_ReadLock`, em seguida, o documento não será fechado, na verdade, e o documento modificado permanecerá aberto de forma invisível na memória, mesmo que o usuário optou por não salvar o documento.

Se a abertura invisível do documento usa uma fraca `RDT_EditLock`, em seguida, ele produz seu bloqueio quando o usuário abre o documento visivelmente e outros bloqueios não são mantidos. Quando o usuário fechar o **DocumentWindow** e escolhe **não** quando solicitado a salvar o documento, em seguida, o documento deve ser fechado da memória. Isso significa que o cliente invisível deve escutar eventos RDT acompanhar esta ocorrência. Na próxima vez em que o documento é necessário, o documento deverá ser reaberto.