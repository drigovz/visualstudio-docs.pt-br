---
title: Exibindo arquivos usando o open with command | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708588"
---
# <a name="display-files-by-using-the-open-with-command"></a>Exibir arquivos usando o comando Abrir com
Um projeto pode pedir ao IDE para exibir a **caixa de diálogo Abrir com** a caixa de diálogo. Essa solicitação solicita ao usuário que abra um arquivo que tenha uma seleção de editores padrão. As seguintes etapas descrevem este processo:

1. O projeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>chama , especificando um valor para `OSE_UseOpenWithDialog` o `OSEOpenDocEditor` parâmetro.

2. Com base na extensão do nome do arquivo do documento, o IDE determina quais editores listados no registro podem abrir o documento especificado e exibe essas informações na caixa **De caixa aberta com** a caixa de diálogo.

    > [!NOTE]
    > Projetos que tenham um editor intrínseco que deve ser incluído na caixa de diálogo **Aberto com** caixa de diálogo devem registrar uma fábrica de editores para cada editor. Os editores intrínsecos só funcionam em conjunto com um determinado <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> tipo de projeto, que é aplicado na implementação do método. O IDE tem uma fábrica de editores incorporada para o editor de texto principal e o editor binário. O IDE também cria uma instância de uma fábrica de editores em nome de cada associação de arquivos do Windows registrada. Um exemplo de tal arquivo é o Microsoft Word.

3. Assim que o usuário selecionar um item na caixa **Aberta com** a caixa <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> de diálogo, o IDE abre o documento pelo método de chamada. Para obter mais informações, consulte [Como: Abrir editores padrão](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Confira também
- [Abrir e salvar itens do projeto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Exibir arquivos usando o comando Abrir arquivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Como: Abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)
