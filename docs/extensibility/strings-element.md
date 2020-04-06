---
title: Elemento cordas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db44db8926b523665a21c00b710dcee55749ab89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699725"
---
# <a name="strings-element"></a>Elemento Strings
O elemento Strings deve conter pelo menos um elemento **criança ButtonText.** Todos os outros elementos infantis são opcionais. Caracteres XML inválidos como '&' e '<' devem&amp;ser&lt;codificados como entidades (' ' e ' e assim por diante).

 Uma ampersand na seqüência de texto especifica o atalho do teclado para o comando.

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
|Linguagem|Opcional. Linguagem=".".".|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|Buttontext|Este campo e os cinco campos de texto a seguir em uma definição de comando permitem especificar o texto que aparece em vários menus. Por padrão, `ButtonText` o campo aparece nos controladores de menu. O `ButtonText` campo também se torna padrão se os outros campos de texto estiverem em branco. O `ButtonText` campo não pode estar em branco mesmo se os outros campos de texto forem especificados.|
|Tooltiptext|O `ToolTipText` campo especifica o texto que aparece na dica de ferramenta para um item do menu.<br /><br /> Se `ToolTipText` o campo estiver `ButtonText` em branco, o campo é usado.|
|Menutext|O `MenuText` campo especifica o texto exibido para um comando se estiver no menu principal, em uma barra de ferramentas, em um menu de atalho ou em um submenu. Se `MenuText` o campo estiver em branco, o ambiente `ButtonText` de desenvolvimento integrado (IDE) usará o campo. O `MenuText` campo também pode ser usado para localização.<br /><br /> Para menus de `MenuText` atalho, o campo é o nome exibido na barra de ferramentas Menus de atalho, que permite a personalização de menus de atalho no IDE. Portanto, seja específico no que você nomeia seu menu de atalho; por exemplo, use "Menu de atalho do pacote widget" em vez de "Atalho".<br /><br /> Se `MenuText` o campo não for `ButtonText` especificado, o campo será usado.|
|CommandName|O `CommandName` campo especifica o texto que aparece na categoria teclado na guia **Comandos** na caixa de diálogo **Personalizar** (disponível clicando em **Personalizar** no menu **Ferramentas).**|
|Canonicalname|O `CanonicalName` campo Inglês especifica o nome do comando em texto em inglês que pode ser inserido na janela **Comando** para executar o item do menu. O IDE elimina todos os caracteres que não são letras, dígitos, sublinhados ou períodos incorporados. Este texto é então concatenado para o `ButtonText` campo para definir o comando. Por exemplo, **Novo projeto** no menu **Arquivo** torna-se o comando File.NewProject.<br /><br /> Se o `CanonicalName` campo inglês não for especificado, o IDE usará o `ButtonText` campo e removerá todas, exceto letras, dígitos, sublinhados e períodos incorporados. Por exemplo, o texto de botão "&definir comandos..." torna-se DefineCommands, onde a ampersand, o espaço e as elipses são removidos.<br /><br /> Se `TextChanges` a bandeira for especificada e o texto do comando for alterado, o comando correspondente reconhecido pela janela **Comando** não será alterado; continua sendo a forma canônica `ButtonText` dos `CanonicalName` campos originais ou ingleses.|
|LocCanonicalNome|O `LocCanonicalName` campo se comporta de `CanonicalName` forma idêntica ao campo inglês, mas permite que o texto de comando localizado seja especificado. Ambos os campos canônicos podem ser especificados. Como o IDE apenas analisa o texto inserido na janela **comando** e o associa a um comando, tanto o texto em inglês quanto o não-inglês podem ser associados ao mesmo comando.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento Button](../extensibility/button-element.md)|Define um elemento com o qual o usuário pode interagir.|
|[Elemento Menu](../extensibility/menu-element.md)|Define um único item do menu.|
|[Elemento Combo](../extensibility/combo-element.md)|Define comandos que aparecem em uma caixa de combinação.|

## <a name="see-also"></a>Confira também
- [Arquivos .Vsct (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
