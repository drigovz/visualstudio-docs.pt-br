---
title: Elemento Strings | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c91a8ea07daee77855017d641a569a892612c3e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719437"
---
# <a name="strings-element"></a>Elemento Strings
O elemento Strings deve conter pelo menos um elemento filho **ButtonText** . Todos os outros elementos filho são opcionais. Caracteres XML inválidos, como ' & ' e ' < ', devem ser codificados como entidades (' &amp; ' e ' &lt; ' e assim por diante).

 Um e comercial na cadeia de texto especifica o atalho de teclado para o comando.

## <a name="syntax"></a>Sintaxe

```
<Strings>
  <ButtonText>... </ButtonText>
  <CommandName>... </CommandName>
</Strings>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|linguagem|Opcional. Language = ".".|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|ButtonText|Esse campo e os cinco campos de texto a seguir em uma definição de comando permitem especificar o texto que aparece em vários menus. Por padrão, o campo `ButtonText` aparece em controladores de menu. O campo `ButtonText` também se tornará o padrão se os outros campos de texto estiverem em branco. O campo `ButtonText` não pode ficar em branco mesmo que os outros campos de texto sejam especificados.|
|ToolTipText|O campo `ToolTipText` especifica o texto que aparece na dica de ferramenta para um item de menu.<br /><br /> Se o campo `ToolTipText` estiver em branco, o campo `ButtonText` será usado.|
|MenuText|O campo `MenuText` especifica o texto que será exibido para um comando se ele estiver no menu principal, em uma barra de ferramentas, em um menu de atalho ou em um submenu. Se o campo `MenuText` estiver em branco, o ambiente de desenvolvimento integrado (IDE) usará o campo `ButtonText`. O campo `MenuText` também pode ser usado para localização.<br /><br /> Para menus de atalho, o campo `MenuText` é o nome exibido na barra de ferramentas menus de atalho, que permite a personalização de menus de atalho no IDE. Portanto, seja específico em nome do seu menu de atalho; por exemplo, use "menu de atalho do pacote de widget" em vez de "Shortcut".<br /><br /> Se o campo `MenuText` não for especificado, o campo `ButtonText` será usado.|
|CommandName|O campo `CommandName` especifica o texto que aparece na categoria teclado na guia **comandos** da caixa de diálogo **Personalizar** (disponível clicando em **Personalizar** no menu **ferramentas** ).|
|Canônicaname|O campo `CanonicalName` em inglês especifica o nome do comando em texto em inglês que pode ser inserido na janela de **comando** para executar o item de menu. O IDE remove os caracteres que não são letras, dígitos, sublinhados ou períodos inseridos. Esse texto é concatenado ao campo `ButtonText` para definir o comando. Por exemplo, **novo projeto** no menu **arquivo** torna-se o comando File. NewProject.<br /><br /> Se o campo de `CanonicalName` em inglês não for especificado, o IDE usará o campo `ButtonText` e exprime tudo, exceto letras, dígitos, sublinhados e períodos inseridos. Por exemplo, o texto do botão "& definir comandos..." torna-se DefineCommands, em que o e comercial, o espaço e as reticências são removidos.<br /><br /> Se o sinalizador de `TextChanges` for especificado e o texto do comando for alterado, o comando correspondente reconhecido pela janela de **comando** não será alterado; Ele continua sendo a forma canônica dos campos original de `CanonicalName` de `ButtonText` ou inglês.|
|LocCanonicalName|O campo `LocCanonicalName` se comporta de forma idêntica ao campo de `CanonicalName` em inglês, mas permite que o texto do comando localizado seja especificado. Ambos os campos canônicos podem ser especificados. Como o IDE apenas analisa o texto inserido na janela de **comando** e o associa a um comando, tanto o texto em inglês quanto o idioma não inglês podem ser associados ao mesmo comando.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento Button](../extensibility/button-element.md)|Define um elemento com o qual o usuário pode interagir.|
|[Elemento Menu](../extensibility/menu-element.md)|Define um único item de menu.|
|[Elemento Combo](../extensibility/combo-element.md)|Define os comandos que aparecem em uma caixa de combinação.|

## <a name="see-also"></a>Consulte também
- [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)