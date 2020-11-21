---
title: Caixa Localizar/Comando
description: Saiba mais sobre a caixa Localizar/comando e como você pode usá-la para Pesquisar texto e executar comandos do Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 341362fe74d4d8a6edbf10afec1a0d49998e857d
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006595"
---
# <a name="findcommand-box"></a>Caixa Localizar/Comando

É possível pesquisar texto e executar comandos do Visual Studio usando a caixa **Localizar/Comando**. A caixa **Localizar/Comando** ainda está disponível como um controle de barra de ferramentas, mas não fica mais visível por padrão. Você pode exibir a caixa **Localizar/Comando** escolhendo **Adicionar ou Remover Botões** na barra de ferramentas **Padrão** e escolhendo **Localizar**.

Para executar um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] comando, preceda-o com um sinal de maior que ( **>** ).

A caixa **Localizar/Comando** retém os últimos 20 itens inseridos e os exibe em uma lista suspensa. É possível navegar pela lista escolhendo as **teclas de direção**.

![Caixa Localizar&#47;Comando](../ide/media/findcommandbox.png)

## <a name="searching-for-text"></a>Pesquisando texto

Por padrão, quando você especifica um texto na caixa **Localizar/Comando** e pressiona a tecla **Enter**, o Visual Studio pesquisa na janela de ferramentas ou documento atual usando as opções especificadas na caixa de diálogo **Localizar nos Arquivos**. Para obter mais informações, consulte [Localizando e substituindo texto](../ide/finding-and-replacing-text.md).

## <a name="entering-commands"></a>Inserindo comandos

Para usar a caixa **Localizar/Comando** para emitir um único comando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou alias, em vez de pesquisar texto, preceda o comando com um símbolo de maior que (**>**). Por exemplo:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

Como alternativa, você também pode usar a janela **Comando** para inserir e executar um ou vários comandos. Alguns comandos ou aliases podem ser inseridos e executados sozinhos; outros têm argumentos obrigatórios em sua sintaxe. Para obter uma lista de comandos que têm argumentos, consulte [Comandos do Visual Studio](../ide/reference/visual-studio-commands.md).

## <a name="escape-characters"></a>Caracteres de escape

Um caractere de acento circunflexo ( **^** ) em um comando significa que o caractere imediatamente após ele é interpretado literalmente, em vez de um caractere de controle. Isso pode ser usado para inserir aspas retas (**"**), espaços, barras iniciais, acentos circunflexos ou quaisquer outros caracteres literais em um parâmetro ou valor de opção, com a exceção de nomes de opção. Por exemplo:

```
>Edit.Find ^^t /regex
```

Um acento circunflexo funciona da mesma forma tanto dentro quanto fora das aspas. Se um acento circunflexo for o último caractere na linha, ele será ignorado.

## <a name="see-also"></a>Confira também

- [Janela Comando](../ide/reference/command-window.md)
- [Localizando e substituindo texto](../ide/finding-and-replacing-text.md)
