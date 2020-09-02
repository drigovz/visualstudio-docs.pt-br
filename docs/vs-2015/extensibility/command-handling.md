---
title: Manipulação de comandos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 563f38cd2dc3854918fe637fdc11afe1d1a49b64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184373"
---
# <a name="command-handling"></a>Manipulação de comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O editor pode definir novos comandos. Geralmente, os comandos são exibidos em um menu, em uma barra de ferramentas ou em um menu de contexto.  
  
 Para obter mais informações sobre como definir comandos e menus, consulte [comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Um serviço de linguagem pode controlar quais menus de contexto são mostrados no editor, interceptando a <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> enumeração. Como alternativa, você pode controlar o menu de contexto por marcador. Para obter mais informações, consulte [comandos importantes para filtros de serviço de linguagem](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Adicionando comandos ao menu de contexto do editor  
 Para adicionar um comando ao menu de contexto, você deve primeiro definir um conjunto de comandos de menu pertencentes a um grupo específico. O exemplo a seguir é extraído do arquivo. vsct gerado como parte do passo a passo explicativo [: adicionando recursos a um editor personalizado](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Menu guid="guidCustomEditorCmdSet" id="IDMX_RTF" priority="0x0000" type="Context">  
  
 \<Parent guid="guidCustomEditorCmdSet" id="0"/>  
  
 \<Strings>  
  
 \<ButtonText>Menu de contexto do CustomEditor\</ButtonText>  
  
 \<CommandName>CustomEditorContextMenu\</CommandName>  
  
 \</Strings>  
  
 \</Menu>  
  
 \</Menus>  
  
 O texto acima adiciona um comando de menu de contexto com o **menu de contexto Text CustomEditor**. O GUID do menu é o do conjunto de comandos criado com esse editor, e o tipo é "Context".  
  
 Você também pode usar comandos predefinidos que não precisam ser definidos no arquivo. vsct. Por exemplo, se você examinar o arquivo EditorPane.cs gerado pelo modelo de pacote do Visual Studio, verá que um conjunto de comandos predefinidos, como <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> definido por <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> , é tratado em manipuladores de comandos, como o método onSelectAll.  
  
## <a name="see-also"></a>Consulte Também  
 [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)
