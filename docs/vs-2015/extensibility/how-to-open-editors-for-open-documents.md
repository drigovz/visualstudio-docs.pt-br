---
title: 'Como: Abrir editores para documentos abertos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae6e565e026ca49825a7b00a82e4e5c62a2f6c3c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092325"
---
# <a name="how-to-open-editors-for-open-documents"></a>Como: Editores abertos para documentos abertos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Antes de um projeto é aberto em uma janela de documento, o projeto primeiro deve determinar se o arquivo já está aberto na janela do documento para outro editor. O arquivo pode ser qualquer um dos software em um editor específico do projeto ou um dos editores padrão registrado com [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="opening-a-project-specific-editor"></a>Abrir um Editor específico do projeto  
 Use o procedimento a seguir para abrir um editor específico do projeto para um arquivo que já está aberto.  
  
#### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Abra um editor específico do projeto para um arquivo aberto  
  
1. Chame o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>.  
  
    Essa chamada retorna ponteiros para a hierarquia do documento, item de hierarquia e quadro de janela, se apropriado.  
  
2. Se o documento for aberto, o projeto deve verificar para ver se existe apenas um objeto de dados de documento, ou se um objeto de exibição de documento também está presente.  
  
   - Se existe um objeto de exibição de documento, e essa exibição é para uma hierarquia diferente ou um item de hierarquia, o projeto usa o ponteiro do quadro de janela do modo de exibição para repavimentar janela existente.  
  
   - Se existe um objeto de exibição de documento e este modo de exibição é para a mesma hierarquia e o item de hierarquia, o projeto pode abrir uma segunda exibição se ela pode anexar ao objeto de dados subjacente do documento. Caso contrário, o projeto deve usar o ponteiro do quadro de janela do modo de exibição para repavimentar janela existente.  
  
   - Se o objeto de dados de documento existe, apenas o projeto deve determinar se ele pode usar o objeto de dados de documento para sua exibição. Se o objeto de dados de documento for compatível, concluído as etapas discutidas [abrir um Editor específico do projeto](../extensibility/how-to-open-project-specific-editors.md).  
  
     Se o objeto de dados de documento não for compatível, um erro deve ser exibido para o usuário que indica que o arquivo está atualmente em uso. Esse erro só deve ser exibido em casos transitórios, como quando um arquivo está sendo compilado ao mesmo tempo o usuário está tentando abrir o arquivo usando um editor diferente do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principal do texto. O editor de texto principal pode compartilhar o objeto de dados de documento com o compilador.  
  
3. Se o documento não estiver aberto, porque não há nenhum objeto de dados de documento ou o objeto de exibição de documento, conclua as etapas em [abrir um Editor específico do projeto](../extensibility/how-to-open-project-specific-editors.md).  
  
## <a name="opening-a-standard-editor"></a>Abrir um Editor padrão  
 Use o procedimento a seguir para abrir um editor padrão para um arquivo que já está aberto.  
  
#### <a name="to-open-a-standard-editor-for-an-open-file"></a>Para abrir um editor padrão para um arquivo aberto  
  
1. Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
     Esse método primeiro verifica se o documento não ainda estiver aberto, chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>. Se o documento já estiver aberto, sua janela de editor é ressurgiu.  
  
2. Se o documento não estiver aberto, em seguida, conclua as etapas em [como: Abrir editores padrão](../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Consulte também  
 [Abrir e salvar itens de projeto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Como: Editores abertos específicos do projeto](../extensibility/how-to-open-project-specific-editors.md)   
 [Como: Abrir editores padrão](../extensibility/how-to-open-standard-editors.md)
