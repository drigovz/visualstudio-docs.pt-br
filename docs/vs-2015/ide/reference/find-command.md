---
title: Comando Find | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ce0e4a3aaca752cbdeda0a83e469977306c3404
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657677"
---
# <a name="find-command"></a>Comando Localizar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pesquisa arquivos usando um subconjunto das opções disponíveis na guia **Localizar nos Arquivos** da janela **Localizar e Substituir**.

## <a name="syntax"></a>Sintaxe

```
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Argumentos
 `findwhat` Necessário. O texto a ser correspondido.

## <a name="switches"></a>Comutadores
 /case ou /c Opcional. As correspondências ocorrerão somente se os caracteres maiúsculos e minúsculos corresponderem exatamente aos especificados no argumento `findwhat`.

 /doc ou /d Opcional. Pesquisa apenas o documento atual. Especifique apenas um dos escopos de pesquisa disponíveis, `/doc`, `/proc`, `/open` ou `/sel`.

 /markall ou /m Opcional. Insere um gráfico em cada linha que contém uma correspondência de pesquisa no documento atual.

 /open ou /o Opcional. Pesquisa todos os documentos abertos como se fossem um documento. Especifique apenas um dos escopos de pesquisa disponíveis, `/doc`, `/proc`, `/open` ou `/sel`.

 /options ou /t Opcional. Exibe uma lista das configurações atuais da opção de localização e não realiza uma pesquisa.

 /proc ou /p Opcional. Pesquisa apenas o procedimento atual. Especifique apenas um dos escopos de pesquisa disponíveis, `/doc`, `/proc`, `/open` ou `/sel`.

 /reset ou /e Opcional. Retorna as opções de localização para suas configurações padrão e não realiza uma pesquisa.

 /sel ou /s Opcional. Pesquisa apenas a seleção atual. Especifique apenas um dos escopos de pesquisa disponíveis, `/doc`, `/proc`, `/open` ou `/sel`.

 /up ou /u Opcional. Pesquisa desde o local atual no arquivo até o início do arquivo. Por padrão, as pesquisas iniciam-se no local atual no arquivo e vão até o final do arquivo.

 /regex ou /r Opcional. Usa caracteres especiais predefinidos no argumento `findwhat` como notações que representam padrões de texto, em vez de caracteres literais. Para obter uma lista completa de caracteres de expressão regular, consulte [Expressões Regulares](../../ide/using-regular-expressions-in-visual-studio.md).

 /wild ou /l Opcional. Usa caracteres especiais predefinidos no argumento `findwhat` como notações para representar um caractere ou uma sequência de caracteres.

 /word ou /w Opcional. Pesquisa somente palavras inteiras.

## <a name="example"></a>Exemplo
 Este exemplo realiza uma pesquisa que diferencia maiúsculas de minúsculas para a palavra "somestring" na seção de código selecionada no momento.

```
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Consulte Também
 [Janela de comando](../../ide/reference/command-window.md) [localização/comando](../../ide/find-command-box.md) [comandos do Visual Studio](../../ide/reference/visual-studio-commands.md) Command [aliases do comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
