---
title: Fazendo linting de código em R
description: Como trabalhar com o suporte de linting interno do Visual Studio para R, incluindo opções do linter.
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.text_editor.r.lint
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 1c32bffbd25a39ff2053dea22930365860ed04a7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873652"
---
# <a name="lint-r-code-in-visual-studio"></a>Fazer lint do código R no Visual Studio

O linter analisa o código para revelar possíveis erros, problemas de formatação e outros ruídos no código, como espaço em branco diferente. O uso de um linter também ajuda a incentivar determinadas convenções de codificação, como a maneira como os identificadores são nomeados. Essas convenções são úteis dentro das equipes e de outras situações colaborativas.

As RTVS (Ferramentas do R para Visual Studio) fornecem um linter interno para o R, cujo comportamento é controlado por meio de várias opções descritas neste artigo. Essas opções são encontradas em **ferramentas**  >  **Opções**  >  **Editor de texto**  >    >  **pano** de R.

O lint está desabilitado por padrão. Para habilitar o pano sem fiapos, defina a opção **todos**  >  **habilitar Panose** como **true**.

Quando estiver habilitado, o linter será executado no editor durante a digitação. Os problemas são exibidos como rabiscos verdes. No gráfico a seguir, por exemplo, as RTVS identificaram seis problemas de lint, incluindo o uso de `=` em vez de `<-` para uma atribuição, a falta de espaçamento em torno dos argumentos de função, o uso de identificadores em PascalCase e em maiúsculas e o uso de um ponto e vírgula. Passar o mouse sobre um problema fornece uma descrição.

![Exemplos de saída do linter para o código R](media/linting-01.png)

Geralmente, você altera as opções do linter dependendo das necessidades de um projeto ou um arquivo. Por exemplo, o código de exemplo de um curso online pode usar `=` em vez de `<-`, junto com identificadores de formatação Pascal. Esse código mostra avisos frequentes do linter, pois as opções padrão do linter sinalizam esses casos. Ao trabalhar com esse código, é possível desabilitar as opções em vez de gastar tempo corrigindo cada instância.

## <a name="assignment-group"></a>Grupo de atribuição

| Opção | Valor padrão | Efeito de lint |
| --- | --- | --- |
| **Fazer \<-** | **True** | Identifica quando `<-` não é usado para a atribuição. |

## <a name="naming-group"></a>Grupo de nomenclatura

Essas opções sinalizam identificadores que usam diferentes convenções de nomenclatura:

| Opção | Valor padrão | Efeito de lint |
| --- | --- | --- |
| **Sinalizar camelCase** | **Falso** | Sinaliza identificadores que usam camelCase. |
| **Sinalizar nomes longos** | **Falso** | Sinaliza os identificadores cujos nomes excedem a configuração de **Tamanho máximo do nome**. |
| **Sinalizar vários pontos** | **True** | Sinaliza identificadores que usam vários pontos. |
| **Sinalizar PascalCase** | **True** | Sinaliza identificadores que usam PascalCase. |
| **Sinalizar snake_case** | **Falso** | Sinaliza identificadores que usam sublinhados. |
| **Sinalizar MAIÚSCULAS** | **True** | Sinaliza identificadores que usam todas maiúsculas. |
| **Tamanho máximo do nome** | **32** | O tamanho aplicado com a configuração **Sinalizar nomes longos**. |

## <a name="spacing-group"></a>Grupo de espaçamento

Essas opções, definidas como **True** por padrão, controlam o local em que o linter identifica problemas de espaçamento: após nomes de função, em torno de vírgulas, em torno de operadores, posições da chave de abertura e de fechamento, espaço antes de ( e espaço dentro de ().

## <a name="statements-group"></a>Grupo de instruções

| Opção | Valor padrão | Efeito de lint |
| --- | --- | --- |
| **Vários** | **True** | Identifica quando várias instruções estão na mesma linha. |
| **Ponto e vírgulas** | **True** | Identifica os usos de ponto e vírgula. |

## <a name="text-group"></a>Grupo de texto

| Opção | Valor padrão | Efeito de lint |
| --- | --- | --- |
| **Limite de tamanho da linha** | **Falso** | Define se o linter sinaliza linhas maiores que a opção **Tamanho máximo da linha**. |
| **Comprimento máximo da linha** | **80** | Define o comprimento da linha aplicado pela opção de **limite de comprimento de linha** . |

## <a name="whitespace-group"></a>Grupo de espaços em branco

Essas opções, definidas como **True** por padrão, controlam o local em que o linter identifica problemas de espaço em branco: uso de tabulações, uso de aspas duplas, linhas vazias à direita e espaço em branco à direita.