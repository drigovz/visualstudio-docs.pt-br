---
title: Modificar o Shell isolado usando o. Arquivo vsct | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c106a04e809e772ac3b8a77192fb2f101161e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194224"
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Modificar o Shell isolado usando o arquivo .Vsct
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O projeto de interface do usuário para um projeto de shell isolado do Visual Studio contém um arquivo. vsct que permite especificar quais grupos de aplicativos e comandos individuais estão disponíveis no aplicativo. Veja a seguir um trecho de um arquivo. vsct não modificado.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Por padrão, a maioria dos comandos e grupos de comandos está incluída. Para excluir um comando ou grupo de comandos, simplesmente remova a marca de comentário desse comando ou grupo.  
  
 Por exemplo, para remover o próximo painel e os comandos do painel anterior, remova os comentários das `No_PaneNextPaneCommand` `No_PanePrevPaneCommand` entradas e:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Para obter um exemplo mais detalhado dessas personalizações, consulte [Walkthrough: Criando um aplicativo de shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Arquivos referenciados  
 O arquivo default. vsct de um aplicativo faz referência aos arquivos a seguir. Esses arquivos estão localizados no subdiretório \VisualStudioIntegration\Common\Inc\ do diretório de instalação do SDK do Visual Studio.  
  
|Arquivo|Descrição|  
|----------|-----------------|  
|wbids. h|Identidades da interface do usuário para o pacote de navegação na Web.|  
|AppIDCmdUsed. vsct|Tabela de comandos para elementos primários da interface do usuário do Visual Studio.|  
|EmulatorCmdUsed. vsct|Tabela de comandos para elementos de interface do usuário de emulação do editor Emacs e Brief.|  
|Vsdebugguids. h|Define os GUIDs dos comandos, da página de opções e de outros recursos do depurador do Visual Studio.|  
|VsDbgCmdUsed. vsct|Tabela de comandos para o depurador.|  
  
 O arquivo AppIDCmdUsed. vsct inclui elementos da interface do usuário do Visual Studio com base nos símbolos definidos no arquivo Application. vsct.  
  
 Para obter mais informações, consulte [criando tabela de comandos XML (. Vsct)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) e a [referência de esquema XML vsct](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Shell isolado do Visual Studio](../extensibility/visual-studio-isolated-shell.md)
