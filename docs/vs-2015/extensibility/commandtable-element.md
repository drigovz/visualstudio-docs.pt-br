---
title: Elemento commandtable | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bb2b874f7bbe94e383e9e7fba755dcc373a93150
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77477042"
---
# <a name="commandtable-element"></a>Elemento CommandTable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Commandtable é o elemento raiz do arquivo. vsct. Esse é o arquivo que define o layout real e o tipo dos comandos que um VSPackage fornece para o IDE. Os comandos podem incluir itens de menu, menus, barras de ferramentas e caixas de combinação. Para obter mais informações, consulte [tabela de comandos do Visual Studio (. Vsct) arquivos](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >  
  <Extern>... </Extern>  
  <Include>... </Include>  
  <Define>... </Define>  
  <Commands>... </Commands>  
  <CommandPlacements>... </CommandPlacements>  
  <VisibilityConstraints>... </VisibilityConstraints>  
  <KeyBindings>... </KeyBindings>  
  <UsedCommands... </UsedCommands>  
  <Symbols>... </Symbols>  
</CommandTable>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
| Atributo |                                                                                                                   Descrição                                                                                                                   |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   xmlns   |                                   Obrigatórios. Namespaces XML:<br /><br /> `xmlns="<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"`<br /><br /> `xmlns:xs="<http://www.w3.org/2001/XMLSchema>"`                                   |
| Linguagem  | Opcional. O atributo language pode ser usado para especificar o idioma padrão de todos os \<Strings> elementos na tabela de comandos.  Se o idioma não for especificado, o idioma do processo atual será usado:<br /><br /> Language = "en-US" |
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento Extern](../extensibility/extern-element.md)|Opcional. Contém diretivas de pré-processador para o compilador.|  
|[Elemento include](../extensibility/include-element.md)|Opcional. Contém caminhos para todos os arquivos a serem incluídos na compilação.|  
|[Elemento Define](../extensibility/define-element.md)|Opcional. Define um símbolo de acordo com seu nome e valor.|  
|[Elemento Commands](../extensibility/commands-element.md)|Opcional. O elemento pai que define todos os comandos para o VSPackage que contém todos os outros elementos.|  
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Opcional. Define onde na barra de comandos os comandos devem ser colocados.|  
|[Element VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Opcional. Determina a visibilidade estática de comandos e barras de ferramentas.|  
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Opcional. Especifica as combinações de teclas de atalho, se houver, para os comandos.|  
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Opcional. Permite que um VSPackage implemente opcionalmente sua própria versão de funcionalidade originalmente suportada por outros VSPackages.|  
|[Elemento Symbols](https://msdn.microsoft.com/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Opcional. Contém quaisquer dados de símbolo--GUIDs, IDs e assim por diante – para o compilador.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Nenhum||  
  
## <a name="see-also"></a>Consulte Também  
 [Arquivos .Vsct (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
