---
title: Exibindo arquivos usando o comando abrir com | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4051793077e613981e1dd5b44f1736878f5853e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708588"
---
# <a name="display-files-by-using-the-open-with-command"></a>Exibir arquivos usando o comando abrir com
Um projeto pode pedir ao IDE para exibir a caixa de diálogo **abrir com** . Essa solicitação solicita que o usuário abra um arquivo que tenha uma seleção de editores padrão. As etapas a seguir descrevem esse processo:

1. O projeto chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , especificando um valor de `OSE_UseOpenWithDialog` para o `OSEOpenDocEditor` parâmetro.

2. Com base na extensão de nome de arquivo do documento, o IDE determina quais editores listados no registro podem abrir o documento especificado e exibe essas informações na caixa de diálogo **abrir com** .

    > [!NOTE]
    > Os projetos que têm um editor intrínseco que deve ser incluído na caixa de diálogo **abrir com** devem registrar uma fábrica de editor para cada editor. Os editores intrínsecos funcionam apenas junto com um tipo específico de projeto, que é imposto na implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método. O IDE tem uma fábrica de editor interna para o editor de texto principal e o editor binário. O IDE também cria uma instância de uma fábrica de editor em nome de cada associação de arquivo registrada do Windows. Um exemplo desse tipo de arquivo é o Microsoft Word.

3. Assim que o usuário seleciona um item na caixa de diálogo **abrir com** , o IDE abre o documento chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método. Para obter mais informações, consulte [como: abrir editores padrão](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Confira também
- [Abrir e salvar itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Exibir arquivos usando o comando abrir arquivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Como: abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)
