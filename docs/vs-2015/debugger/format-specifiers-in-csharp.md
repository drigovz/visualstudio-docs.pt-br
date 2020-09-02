---
title: Especificadores de formato em C# | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- CSharp
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6085ba95d3880417e517530069734052741113e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682475"
---
# <a name="format-specifiers-in-c"></a>Especificadores de formato em C\#

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode alterar o formato no qual um valor é exibido na janela de **inspeção** usando especificadores de formato. Você também pode usar especificadores de formato na janela **imediata** , a janela de **comando** e até mesmo em janelas de origem. Se você pausar em uma expressão nessas janelas, o resultado aparecerá em uma DataTip. As DataTips refletirão o especificador de formato na tela DataTip.

Para usar um especificador de formato, digite a expressão seguida por uma vírgula. Após a vírgula, adicione o especificador apropriado.

## <a name="using-format-specifiers"></a>Usando especificadores de formato

Se você tiver o seguinte código:

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Adicione a `my_var1` variável ao janela inspeção (durante a depuração, **depuração/Windows/inspeção/inspeção 1**) e defina a exibição como hexadecimal (na janela **Watch** , clique com o botão direito do mouse na variável e selecione **exibição hexadecimal**). Agora, a janela **Watch** mostra que ela contém o valor 0x0065. Para ver esse valor expresso como um inteiro decimal em vez de um inteiro hexadecimal, na coluna Name, após o nome da variável, adicione o especificador de formato decimal: **, d**. A coluna valor agora exibe o valor decimal 101

![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")

## <a name="format-specifiers"></a>Especificadores de formato

A tabela a seguir exibe os especificadores de formato C# reconhecidos pelo depurador.

|Especificador|Formatar|Valor de inspeção original|Telas|
|---------------|------------|--------------------------|--------------|
|ac|Forçar avaliação de uma expressão. Isso pode ser útil quando a avaliação implícita das propriedades e das chamadas de função implícitas é desativada. Consulte [efeitos colaterais e expressões](https://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e).|Mensagem "a avaliação da função implícita está desativada pelo usuário"|\<value>|
|d|inteiro decimal|0x0065|101|
|dinâmico|Exibe o objeto especificado usando um Modo de Exibição Dinâmico|Exibe todos os membros do objeto, incluindo a exibição dinâmica|Exibe somente a exibição dinâmica|
|h|inteiro hexadecimal|61541|0x0000F065|
|nq|cadeia de caracteres sem aspas|"Minha cadeia de caracteres"|Minha cadeia de caracteres|
|oculto|Exibe todos os membros públicos e não públicos|Exibe membros públicos|Exibe todos os membros|
|raw|Exibe o item como aparece no nó bruto do item. Válido apenas em objetos proxy.|Dicionário\<T>|Exibição bruta do dicionário\<T>|
|results|Usado com uma variável de um tipo que implementa IEnumerable ou IEnumerable \<T> , geralmente o resultado de uma expressão de consulta. Exibe apenas os membros que contém o resultado da consulta.|Exibe todos os membros.|Exibe os membros que atendem às condições da consulta.|

## <a name="see-also"></a>Consulte Também

- [Janelas de Inspeção e QuickWatch](../debugger/watch-and-quickwatch-windows.md)
- [Janelas de Variáveis](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)
