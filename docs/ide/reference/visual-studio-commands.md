---
title: Comandos
description: Saiba mais sobre os vários comandos aos quais você tem acesso no Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio, commands
- commands, Visual Studio
- command syntax
ms.assetid: 76ffa394-ee89-4629-aba9-1a62b72e6cc1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7928c03e52e4a72fb354bd7202e041ec2264fcd6
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560948"
---
# <a name="visual-studio-commands"></a>Comandos do Visual Studio

Você pode inserir comandos do Visual Studio na janela **Comando**, na janela **Imediato** ou na caixa **Localizar/Comando**. Em cada caso, o sinal maior que (`>`) indica que um comando é seguido, em vez de uma operação de pesquisa ou depuração.

É possível encontrar uma lista completa de comandos e sua sintaxe na página **Teclado** em **Ferramentas** > **Opções** > **Ambiente**.

Em versões localizadas do IDE, os nomes de comando podem ser inseridos na linguagem nativa do IDE ou em inglês. Por exemplo, é possível digitar `File.NewFile` ou `Fichier.NouveauFichier` no IDE francês para executar o mesmo comando.

Muitos comandos têm aliases. Para obter uma lista de aliases de comando, confira [Aliases de comando](../../ide/reference/visual-studio-command-aliases.md). Para obter atalhos de teclado de comando, confira [Atalhos de teclado padrão no Visual Studio](../default-keyboard-shortcuts-in-visual-studio.md).

## <a name="escape-character"></a>Caractere de escape

O caractere de escape para comandos do Visual Studio é um acento circunflexo (^). O caractere de escape significa que o caractere imediatamente a seguir é interpretado literalmente, e não como um caractere de controle. Isso pode ser usado para inserir aspas retas ("), espaços, barras iniciais, acentos circunflexos ou quaisquer outros caracteres literais em um parâmetro ou valor de opção, com a exceção de nomes de opção. Por exemplo:

```
>Edit.Find ^^t /regex
```

Um acento circunflexo funciona da mesma forma tanto dentro quanto fora das aspas. Se um acento circunflexo for o último caractere na linha, ele será ignorado.

## <a name="commands-with-arguments"></a>Comandos com argumentos

Os seguintes comandos usam argumentos ou opções:

| Nome do comando | Descrição |
| - | - |
| [Add Existing Item](../../ide/reference/add-existing-item-command.md) | Adiciona um arquivo existente à solução atual e abre-o. |
| [Add Existing Project](../../ide/reference/add-existing-project-command.md) | Adiciona um projeto existente à solução atual. |
| [Adicionar novo item](../../ide/reference/add-new-item-command.md) | Adiciona um novo item de solução, como um .htm, .css, .txt ou conjunto de quadros à solução atual e a abre. |
| [Alias](../../ide/reference/alias-command.md) | Cria um novo alias para um comando completo, comando e argumentos completos ou até mesmo outro alias. |
| [Evaluate Statement](../../ide/reference/evaluate-statement-command.md) | Avalia e exibe a instrução fornecida. |
| [Localizar](../../ide/reference/find-command.md) | Pesquisa arquivos usando um subconjunto das opções disponíveis no controle **Localizar e Substituir**. |
| [Localizar em arquivos](../../ide/reference/find-in-files-command.md) | Pesquisa arquivos usando um subconjunto das opções disponíveis em [Localizar e Substituir](../../ide/find-in-files.md). |
| [Ir para](../../ide/reference/go-to-command.md) | Move o cursor para a linha especificada. |
| [List Call Stack](../../ide/reference/list-call-stack-command.md) | Exibe a pilha de chamadas atual. |
| [List Disassembly](../../ide/reference/list-disassembly-command.md) | Inicia o processo de depuração e permite que você especifique como os erros são tratados. |
| [List Memory](../../ide/reference/list-memory-command.md) | Exibe o conteúdo do intervalo de memória especificado. |
| [Listar módulos](../../ide/reference/list-modules-command.md) | Lista os módulos do processo atual. |
| [List Registers](../../ide/reference/list-registers-command.md) | Exibe uma lista de registros. |
| [List Source](../../ide/reference/list-source-command.md) | Exibe as linhas de código-fonte especificadas. |
| [List Threads](../../ide/reference/list-threads-command.md) | Exibe uma lista dos threads no programa atual. |
| [Log Command Window Output](../../ide/reference/log-command-window-output-command.md) | Copia todas as entradas e saídas da janela Comando para um arquivo. |
| [Novo arquivo](../../ide/reference/new-file-command.md) | Cria um novo arquivo e o adiciona ao projeto atualmente selecionado. |
| [Abrir arquivo](../../ide/reference/open-file-command.md) | Abre um arquivo existente e permite que você especifique um editor. |
| [Abrir projeto](../../ide/reference/open-project-command.md) | Abre um projeto existente e permite que você o adicione à solução atual. |
| [Imprimir](../../ide/reference/print-command.md) | Avalia a expressão e exibe os resultados ou o texto especificado. |
| [Comando de inspeção rápida](../../ide/reference/quick-watch-command.md) | Exibe o texto selecionado ou especificado no campo **Expressão** da caixa de diálogo **Inspeção Rápida**. |
| [Substituir](../../ide/reference/replace-command.md) | Substitui texto em arquivos usando um subconjunto das opções disponíveis no controle **Localizar e Substituir**. |
| [Substituir em arquivos](../../ide/reference/replace-in-files-command.md) | Substitui texto em arquivos usando um subconjunto das opções disponíveis em [Substituir nos Arquivos](../../ide/replace-in-files.md). |
| [Set Current Stack Frame](../../ide/reference/set-current-stack-frame-command.md) | Permite que você exiba um registro de ativação específico. |
| [Set Current Thread](../../ide/reference/set-current-thread-command.md) | Permite que você exiba um thread específico. |
| [Set Radix](../../ide/reference/set-radix-command.md) | Determina o número de bytes a ser exibido. |
| [Shell](../../ide/reference/shell-command.md) | Inicia programas de dentro do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] como se o comando tivesse sido executado no prompt de comando. |
| [Comando de createwebbrowser](../../ide/reference/showwebbrowser-command.md) | Exibe a URL especificada em uma janela de navegador da Web, tanto dentro do IDE (ambiente de desenvolvimento integrado) ou externa ao IDE. |
| [Iniciar](../../ide/reference/start-command.md) | Inicia o processo de depuração e permite que você especifique como os erros são tratados. |
| [Caminho](../../ide/reference/symbol-path-command.md) | Define a lista de diretórios para o depurador pesquisar símbolos. |
| [Alternar ponto de interrupção](../../ide/reference/toggle-breakpoint-command.md) | Ativa ou desativa o ponto de interrupção dependendo de seu estado atual, no local atual do arquivo. |
| [Comando Watch](../../ide/reference/watch-command.md) | Cria e abre uma instância especificada de uma janela **Inspeção**. |

## <a name="see-also"></a>Confira também

- [Janela Comando](../../ide/reference/command-window.md)
- [Caixa Localizar/comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
