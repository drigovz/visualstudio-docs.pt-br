---
title: Elemento de Tabela de Comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a362763d34335b9a18c4114a7c35b23f0efee020
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739651"
---
# <a name="commandtable-element"></a>Elemento CommandTable
CommandTable é o elemento raiz do arquivo *.vsct.* Este é o arquivo que define o layout real e o tipo dos comandos que um VSPackage fornece ao IDE. Os comandos podem incluir itens de menu, menus, barras de ferramentas e caixas de combinação. Para obter mais informações, consulte [arquivos da tabela de comando visual Studio (.vsct).](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

## <a name="syntax"></a>Sintaxe

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

| Atributo | Descrição |
|-----------| - |
| xmlns | Obrigatórios. Espaços de nomes XML:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns:xs="<http://www.w3.org/2001/XMLSchema>" |
| Linguagem | Opcional. O atributo de idioma pode ser \<usado para especificar a linguagem padrão de todos os elementos de> strings na tabela de comando.  Se o idioma não for especificado, o idioma do processo atual será usado:<br /><br /> linguagem="en-us" |

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento extern](../extensibility/extern-element.md)|Opcional. Contém diretivas de pré-processador para o compilador.|
|[Incluir elemento](../extensibility/include-element.md)|Opcional. Contém caminhos para quaisquer arquivos a serem insodados na compilação.|
|[Definir elemento](../extensibility/define-element.md)|Opcional. Define um símbolo dado seu nome e valor.|
|[Elemento comandos](../extensibility/commands-element.md)|Opcional. O elemento pai que define todos os comandos para o VSPackage que contém todos os outros elementos.|
|[Elemento ComandosDe posicionamento](../extensibility/commandplacements-element.md)|Opcional. Define onde na barra de comando os comandos devem ser colocados.|
|[Elemento de restrições de visibilidade](../extensibility/visibilityconstraints-element.md)|Opcional. Determina a visibilidade estática dos comandos e barras de ferramentas.|
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Opcional. Especifica as combinações de teclas de atalho, se houver, para os comandos.|
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Opcional. Permite que um VSPackage implemente opcionalmente sua própria versão de funcionalidade originalmente suportada por outros VSPackages.|
|[Elemento símbolos](https://www.microsoft.com/download/details.aspx?id=55984)|Opcional. Contém qualquer dado de símbolo - GUIDs, IDs, e assim por diante - para o compilador.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|Nenhum||

## <a name="see-also"></a>Confira também
- [Arquivos da tabela de comando do Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
