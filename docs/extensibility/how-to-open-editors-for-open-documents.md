---
title: 'Como: Abrir Editores para Documentos Abertos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d0986573ac0d53427f6490370be2bfa1c4cbe7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710922"
---
# <a name="how-to-open-editors-for-open-documents"></a>Como: Abrir editores para documentos abertos
Antes de um projeto abrir uma janela de documento, o projeto primeiro deve determinar se o arquivo já está aberto na janela do documento para outro editor. O arquivo pode ser aberto em um editor específico de projeto ou [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]em um dos editores padrão registrados com .

## <a name="open-a-project-specific-editor"></a>Abra um editor específico para projetos
 Use o procedimento a seguir para abrir um editor específico do projeto para um arquivo que já está aberto.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Para abrir um editor específico de projeto para um arquivo aberto

1. Chame o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> .

    Esta chamada retorna ponteiros para a hierarquia do documento, item de hierarquia e quadro de janela, se apropriado.

2. Se o documento estiver aberto, o projeto deve verificar se apenas existe um objeto de dados de documento ou se um objeto de exibição de documento também está presente.

   - Se um objeto de exibição de documento existir e essa exibição for para um item de hierarquia ou hierarquia diferente, o projeto usará o ponteiro para o quadro de janela da exibição para ressurgir a janela existente.

   - Se um objeto de exibição de documento existir e essa exibição for para o mesmo item de hierarquia e hierarquia, o projeto poderá abrir uma segunda exibição se ele puder anexar ao objeto de dados do documento subjacente. Caso contrário, o projeto deve usar o ponteiro para o quadro da janela da vista para ressurgir a janela existente.

   - Se apenas o objeto de dados do documento existir, o projeto deve determinar se ele pode usar o objeto de dados do documento para sua exibição. Se o objeto de dados do documento for compatível, complete as etapas discutidas em [Abrir um editor específico do projeto](../extensibility/how-to-open-project-specific-editors.md).

     Se o objeto de dados do documento não for compatível, um erro deve ser exibido ao usuário que indique que o arquivo está em uso no momento. Esse erro só deve ser exibido em casos transitórios, como quando um arquivo está sendo compilado ao mesmo tempo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] em que o usuário está tentando abrir o arquivo usando um editor diferente do editor de texto principal. O editor de texto principal pode compartilhar objeto de dados de documento com o compilador.

3. Se o documento não estiver aberto porque não há objeto de dados de documento ou objeto de exibição de documento, complete as etapas em [Abrir um editor específico do projeto](../extensibility/how-to-open-project-specific-editors.md).

## <a name="open-a-standard-editor"></a>Abra um editor padrão
 Use o procedimento a seguir para abrir um editor padrão para um arquivo que já está aberto.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>Para abrir um editor padrão para um arquivo aberto

1. Chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.

     Este método primeiro verifica se o documento <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>ainda não está aberto por chamada . Se o documento já estiver aberto, a janela do editor será ressurgida.

2. Se o documento não estiver aberto, complete as etapas em [Como: Abrir editores padrão](../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Confira também
- [Abrir e salvar itens do projeto](../extensibility/internals/opening-and-saving-project-items.md)
- [Como: Abrir editores específicos de projetos](../extensibility/how-to-open-project-specific-editors.md)
- [Como: Abrir editores padrão](../extensibility/how-to-open-standard-editors.md)
