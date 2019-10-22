---
title: Comando Substituir | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7ba633999925e86b753dbd815babe6e52c75ca53
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665625"
---
# <a name="replace-command"></a>Comando Substituir
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Substitui texto em arquivos usando um subconjunto das opções disponíveis na guia **Substituir nos Arquivos** da janela **Localizar e Substituir**.

## <a name="syntax"></a>Sintaxe

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
```

## <a name="arguments"></a>Arguments
 `findwhat` Necessário. O texto a ser correspondido.

 `replacewith` Necessário. O texto a ser substituído pelo texto correspondido.

## <a name="switches"></a>Opções
 /All ou/a opcional. Substitui todas as ocorrências do texto da pesquisa pelo texto de substituição.

 /case ou /c Opcional. As correspondências ocorrerão somente se os caracteres maiúsculos e minúsculos corresponderem exatamente aos especificados no argumento `findwhat`.

 /doc ou /d Opcional. Pesquisa apenas o documento atual. Especifique apenas um dos escopos de pesquisa disponíveis, `/doc`, `/proc`, `/open` ou `/sel`.

 /Hidden ou/h opcional. Pesquisa texto oculto e recolhido, como os metadados de um controle DTC, uma região oculta de um documento com estrutura de tópicos ou uma classe ou método recolhido.

 /open ou /o Opcional. Pesquisa todos os documentos abertos como se fossem um documento. Especifique apenas um dos escopos de pesquisa disponíveis, `/doc`, `/proc`, `/open` ou `/sel`.

 /options ou /t Opcional. Exibe uma lista das configurações atuais da opção de localização e não realiza uma pesquisa.

 /proc ou /p Opcional. Pesquisa apenas o procedimento atual. Especifique apenas um dos escopos de pesquisa disponíveis, `/doc`, `/proc`, `/open` ou `/sel`.

 /regex ou /r Opcional. Usa caracteres especiais predefinidos no argumento `findwhat` como notações que representam padrões de texto, em vez de caracteres literais. Para obter uma lista completa de caracteres de expressão regular, consulte [Expressões Regulares](../../ide/using-regular-expressions-in-visual-studio.md).

 /reset ou /e Opcional. Retorna as opções de localização para suas configurações padrão e não realiza uma pesquisa.

 /sel ou /s Opcional. Pesquisa apenas a seleção atual. Especifique apenas um dos escopos de pesquisa disponíveis, `/doc`, `/proc`, `/open` ou `/sel`.

 /up ou /u Opcional. Pesquisa desde o local atual em um arquivo até o topo do arquivo. Por padrão, as pesquisas têm início no local atual no arquivo e vão até a parte inferior do arquivo.

 /wild ou /l Opcional. Usa caracteres especiais predefinidos no argumento `findwhat` como notações para representar um caractere ou uma sequência de caracteres.

 /word ou /w Opcional. Pesquisa somente palavras inteiras.

## <a name="example"></a>Exemplo
 Este exemplo substitui `btnSend` por `btnSubmit` em todos os documentos abertos.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Veja também
 [Localizando e substituindo a janela de comando de texto](../../ide/finding-and-replacing-text.md) [](../../ide/reference/command-window.md) [pesquisa/comando caixa](../../ide/find-command-box.md) de comandos [Visual](../../ide/reference/visual-studio-commands.md) Studio [aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
