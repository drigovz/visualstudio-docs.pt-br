---
title: Personalizando o Shell isolado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 724d4d0c4b392a362e702f33ea996df3a6fc0ad6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555962"
---
# <a name="customizing-the-isolated-shell"></a>Personalizar o Shell isolado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode personalizar seu aplicativo de shell isolado do Visual Studio alterando diferentes aspectos da interface do usuário do Visual Studio e restringindo os comandos e recursos incluídos no seu aplicativo especializado.  
  
## <a name="using-the-applicationpkgdef-file"></a>Usando o arquivo Application. pkgdef  
 A solução de modelo de shell isolado inclui um *SolutionName*. Arquivo Application. pkgdef que permite que você modifique os seguintes recursos:  
  
##### <a name="the-application-title"></a>O título do aplicativo  
 Você pode personalizar o título do aplicativo, que é o nome exibido na barra de título do aplicativo, alterando o valor da linha "AppName" no *SolutionName*. Arquivo Application. pkgdef. Para obter mais detalhes, consulte [Walkthrough: Criando um aplicativo de shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Se você não quiser que o título do aplicativo exiba o projeto que está carregado no momento, altere o valor da linha "ShowHierarchyRootInTitle" no *SolutionName*. Arquivo Application. pkgdef de DWORD: 00000001 para DWORD: 00000000.  
  
##### <a name="the-application-icon"></a>O ícone do aplicativo  
 Você pode personalizar o ícone do aplicativo, que é o ícone exibido pelo nome do aplicativo na barra de título do aplicativo. Copie um ícone diferente para o diretório de ícones. Em **Gerenciador de soluções**, adicione o ícone à pasta arquivos de recurso. Em seguida, abra o arquivo VSShellStub. rc e substitua o valor de IDI_STUBPROGRAM pelo nome do novo ícone. Para obter mais detalhes, consulte [Walkthrough: Criando um aplicativo de shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>O logotipo da linha de comando  
 Você pode personalizar o logotipo da linha de comando, que é o texto que aparece quando o aplicativo é iniciado na linha de comando, alterando o valor da linha "CommandLineLogo" no *SolutionName*. Arquivo Application. pkgdef. Para obter mais detalhes, consulte [Walkthrough: Criando um aplicativo de shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>O nome da subpasta arquivos de usuário  
 Você pode alterar o nome da pasta que seu aplicativo mantém para os arquivos do usuário, alterando o valor da linha "UserFilesSubFolderName" em *SolutionName*. Arquivo Application. pkgdef.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>O título do nó da árvore de solução na caixa de diálogo novo projeto  
 Você pode personalizar o título do nó da solução na caixa de diálogo novo projeto alterando o valor da linha "NewProjDlgSlnTreeNodeTitle" no *SolutionName*. Arquivo Application. pkgdef.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>O cabeçalho de modelos instalados na caixa de diálogo novo projeto  
 Você pode alterar o cabeçalho de modelos instalados na caixa de diálogo novo projeto alterando o valor da linha "NewProjDlgInstalledTemplatesHdr" no *SolutionName*. Arquivo Application. pkgdef.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Se deseja ou não ocultar arquivos diversos por padrão  
 Você pode especificar se deseja ou não ocultar arquivos diversos por padrão, alterando o valor da linha "HideMiscellaneousFilesByDefault" no *SolutionName*. Arquivo Application. pkgdef. Para ocultar arquivos diversos, defina o valor `dword:00000001` e, para mostrar os arquivos, defina o valor `dword:00000000` .  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Se deseja ou não desabilitar a janela de saída  
 Você pode especificar se deseja ou não desabilitar a janela de saída em seu aplicativo alterando o valor da linha "DisableOutputWindow" no *SolutionName*. Arquivo Application. pkgdef. Para desabilitar a janela de saída, defina o valor `dword:00000001` e para mostrar a janela saída, defina o valor `dword:00000000` .  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Se deseja ou não permitir arquivos descartados na janela principal  
 Você pode especificar se deseja ou não permitir arquivos descartados na janela principal em seu aplicativo alterando o valor da linha "AllowsDroppedFilesOnMainWindow" no *SolutionName*. Arquivo Application. pkgdef. Para permitir arquivos descartados, defina o valor `dword:00000001` e para não permitir arquivos ignorados, defina o valor `dword:00000000` .  
  
##### <a name="the-default-search-page"></a>A página de pesquisa padrão  
 Você pode personalizar a página do navegador da Web, que é a página que é exibida quando a janela do navegador da Web é aberta, alterando o valor da linha "DefaultSearchPage" no *SolutionName*. Arquivo Application. pkgdef.  
  
##### <a name="the-default-home-page"></a>O home page padrão  
 Você pode personalizar o home page alterando o valor da linha "defaulthomepage" no *SolutionName*. Arquivo Application. pkgdef. Para obter mais detalhes, consulte [Walkthrough: Criando um aplicativo de shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Se deseja ou não ocultar o conceito da solução  
 Você pode especificar se deseja ou não ocultar a solução em seu aplicativo alterando o valor da linha "HideSolutionConcept" no *SolutionName*. Arquivo Application. pkgdef. Para ocultar a solução, defina o valor `dword:00000001` e para mostrar a solução, defina o valor `dword:00000000` .  
  
##### <a name="the-default-debug-engine"></a>O mecanismo de depuração padrão  
 Você pode alterar o mecanismo de depuração que seu aplicativo usa alterando o valor da linha "DefaultDebugEngine" no *SolutionName*. Arquivo Application. pkgdef para o GUID do mecanismo de depuração.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>A extensão de arquivo do arquivo de opções de usuário  
 Você pode alterar o nome da pasta que seu aplicativo mantém para os arquivos do usuário, alterando o valor da linha "UserOptsFileExt" em *SolutionName*. Arquivo Application. pkgdef.  
  
##### <a name="the-solution-file-extension"></a>A extensão do arquivo da solução  
 Você pode alterar a extensão usada para os arquivos da solução alterando o valor da linha "SolutionFileExt" no *SolutionName*. Arquivo Application. pkgdef.  
  
##### <a name="the-default-user-files-folder-root"></a>A raiz da pasta de arquivos de usuário padrão  
 Você pode alterar o nome da pasta raiz dos arquivos de usuário para seu aplicativo alterando o valor da linha "UserFilesSubFolderName" no *SolutionName*. Arquivo Application. pkgdef.  
  
##### <a name="the-solution-file-creator-identifier"></a>O identificador do criador do arquivo de solução  
 Você pode alterar o identificador usado para os arquivos da solução alterando o valor da linha "SolutionFileCreatorIdentifier" no *SolutionName*. Arquivo Application. pkgdef.  
  
##### <a name="the-default-projects-location"></a>O local dos projetos padrão  
 Você pode alterar o nome do local dos projetos padrão alterando o valor da linha "DefaultProjectsLocation" no *SolutionName*. Arquivo Application. pkgdef.  
  
##### <a name="the-application-localization-package"></a>O pacote de localização do aplicativo  
 Você pode alterar o pacote de localização usado para seu aplicativo alterando o valor da linha "AppLocalizationPackage" no *SolutionName*. Arquivo Application. pkgdef.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Se deseja ou não mostrar a raiz da hierarquia no título  
 Você pode especificar se deseja ou não mostrar a raiz da hierarquia na barra de título em seu aplicativo alterando o valor da linha "ShowHierarchyRootInTitle" no *SolutionName*. Arquivo Application. pkgdef. Para mostrar a raiz da hierarquia, defina o valor `dword:00000001` e para ocultar a raiz da hierarquia, defina o valor `dword:00000000` .  
  
##### <a name="specifying-a-start-page"></a>Especificando uma página inicial  
 Para especificar uma página inicial para seu aplicativo personalizado, no *SolutionName*. Arquivo Application. pkgdef, defina o valor "DisableStartPage" como `dword:00000000` e, em `[$RootKey$\StartPage\Default]` defina o URI para o local do arquivo. XAML:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 No arquivo ApplicationCommands. vsct no projeto de interface do usuário do *SolutionName*, comente a entrada "No_ShellPkg_startPageCommand":  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Você deve adicionar o arquivo. XAML e todos os arquivos gráficos necessários para o projeto *SolutionName* . Esses arquivos devem realmente ser copiados para o diretório do projeto *SolutionName* , não adicionados de outro diretório.  
  
 Em todos os arquivos, defina a propriedade **tipo de item** como arquivo de **shell isolado** para que os arquivos sejam copiados para o diretório *$RootFolder $* . (Para definir a propriedade **tipo de item** , clique com o botão direito do mouse no arquivo e selecione **Propriedades**. Essa propriedade é encontrada em **Propriedades de configuração**, **geral**.)  
  
 Para obter mais informações sobre como personalizar páginas iniciais, consulte [Personalizando a página inicial](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Usando outros elementos do Shell isolado  
 Você pode usar outros arquivos e projetos que estão incluídos no modelo de solução de shell isolado para personalizar ainda mais seu aplicativo.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Habilitar/desabilitar pacotes do Visual Studio  
 O arquivo *SolutionName*. pkgundef permite que você desabilite determinados tipos de funcionalidade do Visual Studio excluindo determinados pacotes. Por exemplo, a seguinte linha:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Remove o projeto de arquivos diversos do conjunto de modelos de projeto exibido na caixa de diálogo **novo projeto** . Para obter mais detalhes, consulte [Walkthrough: Criando um aplicativo de shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Habilitar/desabilitar comandos de menu  
 O arquivo *SolutionName*UI. vsct inclui uma lista comentada de todos os comandos de menu disponíveis para o Shell isolado. Para desabilitar um determinado comando, remova a marca de comentário da linha correspondente. Por exemplo, para desabilitar o comentário da janela/divisão, remova a marca de comentário da `<Define name="No_SplitCommand"/>` linha. Para obter mais detalhes, consulte [Walkthrough: Criando um aplicativo de shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>O bitmap usado na tela inicial  
 Você pode personalizar o bitmap usado na tela inicial, que é a janela que é exibida quando o aplicativo é iniciado, alterando o valor da linha "SplashScreenBitmap" no *SolutionName*. Arquivo Application. pkgdef. Para obter mais detalhes, consulte [Walkthrough: Criando um aplicativo de shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>A janela ajuda/sobre  
 No modelo de shell isolado, há um projeto separado que você pode usar para personalizar a caixa de ajuda/sobre para seu aplicativo. Para obter mais detalhes, consulte [Walkthrough: Criando um aplicativo de shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).
