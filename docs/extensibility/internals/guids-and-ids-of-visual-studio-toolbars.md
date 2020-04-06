---
title: GUIDs e IDs de barras de ferramentas do Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe42821cdacc038d767e52373d45ddd7b8954323
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708223"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>GUIDs e IDs de barras de ferramentas do Visual Studio
Este tópico enumera os valores GUID e ID das barras de ferramentas que estão incluídas no ambiente de desenvolvimento integrado do Visual Studio (IDE) e dos grupos que contêm. Esses valores são definidos em arquivos *.vsct* que são instalados como parte do Visual Studio SDK. Para obter mais informações, consulte [comandos, menus e grupos definidos pelo IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

> [!NOTE]
> Muitas das barras de ferramentas disponíveis para o Visual Studio não são definidas pelo Visual Studio, e seus valores DE GUID e ID não são públicos. Este tópico lista apenas barras de ferramentas definidas em arquivos Visual Studio SDK *.vsct.*

 Para obter mais informações sobre como trabalhar com objetos IDE definidos em arquivos *.vsct,* consulte [Estender menus e comandos](../../extensibility/extending-menus-and-commands.md).

 As barras de ferramentas padrão fornecidas pelo `guidSHLMainMenu`Visual Studio IDE usam `GUID:ID` o GUID, exceto quando especificado de outra forma usando sintaxe.

## <a name="ide-toolbars"></a>Barras de ferramentas do IDE
 As seguintes barras de ferramentas são fornecidas pelo Visual Studio IDE. As barras de ferramentas podem ser exibidas selecionando-as no submenu Barras de **ferramentas** do menu **Ferramentas.** As barras de ferramentas nas janelas das ferramentas não estão incluídas nesta seção.

 Apenas grupos podem descer diretamente das barras de ferramentas. Para adicionar um grupo, defina seu pai no GUID e ID da barra de ferramentas. Para adicionar um botão a uma barra de ferramentas, defina seu pai em um grupo na barra de ferramentas.

|Barra de ferramentas|ID|
|-------------|--------|
|Standard|IDM_VS_TOOL_STANDARD|
|Build|IDM_VS_TOOL_BUILD|
|Editor de texto|IDM_VS_TOOL_TEXTEDITOR|
|Depurar|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|
|Localização da depuração|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>Barras de ferramentas especiais
 Essas barras de ferramentas são definidas pelo Visual Studio IDE, mas servem funções especializadas e não hospedam grupos de comando.

|Barra de ferramentas|ID|
|-------------|--------|
|Adicionar comando|IDM_VS_TOOL_ADDCOMMAND|
|Indefinido|IDM_VS_TOOL_UNDEFINED|
|esquema XML|IDM_VS_TOOL_SCHEMA|
|dados XML|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>Grupos nas barras de ferramentas do IDE
 Para adicionar um botão a uma barra de ferramentas padrão, defina um dos seguintes grupos como seu pai. Os grupos são classificados pela barra de ferramentas dos pais.

### <a name="standard-toolbar-groups"></a>Grupos de barras de ferramentas padrão

|Nome|ID|
|----------|--------|
|Salvar/Abrir|IDG_VS_TOOLSB_SAVEOPEN|
|Corte/cópia|IDG_VS_TOOLSB_CUTCOPY|
|Desfazer/refazer|IDG_VS_TOOLSB_UNDOREDO|
|Executar/construir|IDG_VS_TOOLSB_RUNBUILD|
|Search|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|Novas janelas|IDG_VS_TOOLSB_NEWWINDOWS|
|Carregar/salvar|IDG_VS_WINDOWUI_LOADSAVE|
|Medidor|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>Construir grupos de barras de ferramentas

|Nome|ID|
|----------|--------|
|Barra de construção|IDG_VS_BUILDBAR|
|Cancelar|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>Grupos de barras de ferramentas do editor de texto

|Nome|ID|
|----------|--------|
|Completion|IDM_VS_TOOL_TEXTEDITOR|
|Travessão|IDG_VS_EDITTOOLBAR_INDENT|
|Comentário|IDG_VS_EDITTOOLBAR_COMMENT|
|Indicadores|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>Grupos de barras de ferramentas de depuração

|Nome|ID|
|----------|--------|
|Execução|IDM_DEBUG_TOOLBAR|
|Depuração|IDG_DEBUG_TOOLBAR_STEPPING|
|Inspeção|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>Grupos de barras de ferramentas de localização de depuração

|Nome|ID|
|----------|--------|
|Localização da depuração|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>Barras de ferramentas da janela de ferramentas
 As barras de ferramentas podem aparecer diretamente no IDE ou nas janelas de ferramentas, como **o Solution Explorer**. Como as janelas de ferramenta não são definidas em arquivos *.vsct,* as barras de ferramentas da janela da ferramenta não têm pais definidos. Em vez disso, são colocados em código. A tabela a seguir mostra as barras de ferramentas que aparecem nas janelas das ferramentas no IDE e os grupos de comando que eles contêm.

> [!NOTE]
> Barras de ferramentas e `guidSHLMainMenu`grupos usam o GUID, exceto quando especificado de outra forma usando sintaxe GUID:ID. Quando um GUID é especificado para uma barra de ferramentas, ele também se aplica aos grupos que descem dessa barra de ferramentas.

|Janela da ferramenta|Barra de ferramentas|Grupos|
|-----------------|-------------|------------|
|Gerenciador de Soluções|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1. 5|
|Gerenciador de Servidores|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|Propriedades|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|Exibição de Classe|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|Exibição de Classe|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|Pesquisador de Objetos|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|Pesquisador de Objetos|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|Saída|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|Localizar e Substituir|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|Encontre resultados 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|Encontrar resultados 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|Snippet|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|Indicadores|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|Lista de Tarefas|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|Tarefas do usuário|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|Lista de Erros|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|Navegador de chamada de chamada|IDM_VS_TOOL_CALLBROWSER1. 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|Pontos de interrupção|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|Desmontagem|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|Memória 1-4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1. 4<br /><br /> IDG_MEMORY_COLUMNS1. 4|
|Processos|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>Confira também
- [Adicione um controlador de menu a uma barra de ferramentas](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)
- [Adicione uma barra de ferramentas a uma janela de ferramenta](../../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [GUIDs e IDs dos menus do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)
