---
title: Caixa Localizar – Comando | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b8bddc27eb4a59b65796c7837ae4561e5d56a5d5
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54801219"
---
# <a name="findcommand-box"></a>Localizar/caixa de comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

É possível pesquisar texto e executar comandos do Visual Studio usando a caixa **Localizar/Comando**. A caixa **Localizar/Comando** ainda está disponível como um controle de barra de ferramentas, mas não fica mais visível por padrão. Você pode exibir a caixa **Localizar/Comando** escolhendo **Adicionar ou Remover Botões** na barra de ferramentas **Padrão** e escolhendo **Localizar**.  
  
 Para executar um comando [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], preceda-o com um sinal de maior que (>).  
  
 A caixa **Localizar/Comando** retém os últimos 20 itens inseridos e os exibe em uma lista suspensa. É possível navegar pela lista escolhendo as teclas de direção.  
  
 ![Caixa Localizar&#47;Comando](../ide/media/findcommandbox.png "FindCommandBox")  
Localizar/caixa de comando  
  
## <a name="searching-for-text"></a>Pesquisando texto  
 Por padrão, quando você especifica um texto na caixa **Localizar/Comando** e pressiona a tecla ENTER, o Visual Studio pesquisa na janela de ferramentas ou documento atual usando as opções especificadas na caixa de diálogo **Localizar nos Arquivos**. Para obter mais informações, consulte [Localizando e substituindo texto](../ide/finding-and-replacing-text.md).  
  
## <a name="entering-commands"></a>Inserindo comandos  
 Para usar a caixa **Localizar/Comando** para emitir um único comando [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou alias, em vez de pesquisar texto, digite o comando [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], precedido por um símbolo de maior que (>). Por exemplo:  
  
```  
>File.NewFile c:\temp\MyFile /t:"General\Text File"  
```  
  
 Como alternativa, você também pode usar a janela Comando para inserir e executar um ou vários comandos. Alguns comandos ou aliases podem ser inseridos e executados sozinhos; outros têm argumentos obrigatórios em sua sintaxe. Para obter uma lista de comandos que têm argumentos, consulte [Comandos do Visual Studio](../ide/reference/visual-studio-commands.md).  
  
## <a name="escape-characters"></a>Caracteres de escape  
 Um caractere de acento circunflexo (^) em uma linha de comando significa que o caractere imediatamente a seguir é interpretado literalmente, em vez de como um caractere de controle. Isso pode ser usado para inserir aspas retas ("), espaços, barras iniciais, acentos circunflexos ou quaisquer outros caracteres literais em um parâmetro ou valor de opção, com a exceção de nomes de opção. Por exemplo,  
  
```  
>Edit.Find ^^t /regex  
```  
  
 Um acento circunflexo funciona da mesma forma tanto dentro quanto fora das aspas. Se um acento circunflexo for o último caractere na linha, ele será ignorado.  
  
## <a name="see-also"></a>Consulte também  
 [Janela Comando](../ide/reference/command-window.md)   
 [Localizando e substituindo texto](../ide/finding-and-replacing-text.md)
