---
title: Especificadores de formato no depurador (C#) | Microsoft Docs
description: Use um especificador de formato para alterar o formato no qual um valor é exibido na janela Inspeção. Este artigo fornece detalhes de uso.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: abc824cf5d0413f01ad5f3f4423b974aeca40b03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870578"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Especificadores de formato em C# no depurador do Visual Studio
Você pode alterar o formato no qual um valor é exibido na janela de **inspeção** usando especificadores de formato. Você também pode usar especificadores de formato na janela **imediata** , na janela de **comando** , em [tracepoints](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)e em janelas de origem. Se você pausar uma expressão nessas janelas, o resultado aparecerá em um  [DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) na exibição do formato especificado.

Para usar um especificador de formato, insira a expressão de variável seguida por uma vírgula e o especificador apropriado.

## <a name="set-format-specifiers"></a>Definir especificadores de formato
Usaremos o seguinte código de exemplo:

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Adicione a `my_var1` variável à janela **Watch** durante a depuração, **depure** o  >  **Windows**  >  **Watch**  >  **Watch 1**. Em seguida, clique com o botão direito do mouse na variável e selecione **exibição hexadecimal**. Agora, a janela **Watch** mostra o valor 0x0065. Para ver esse valor como um inteiro decimal em vez de um inteiro hexadecimal, adicione o especificador de formato decimal **, d** na coluna **nome** após o nome da variável. A coluna **valor** agora mostra **101**.

![Captura de tela do janela Inspeção do Visual Studio com uma linha que mostra my_var1, d com um valor de 101 e um tipo de int.](../debugger/media/watchformatcsharp.png)

::: moniker range=">= vs-2019" 

Você pode exibir e selecionar em uma lista de especificadores de formato disponíveis acrescentando uma vírgula (,) ao valor na janela de **inspeção** . 

![FormatSpecCSharp](../debugger/media/vs-2019/format-specs-csharp.png "FormatSpecCSharp")

::: moniker-end

## <a name="format-specifiers"></a>Especificadores de formato
A tabela a seguir descreve os especificadores de formato C# para o depurador do Visual Studio.

|Especificador|Formatar|Valor de inspeção original|Telas|
|---------------|------------|--------------------------|--------------|
|ac|Force a avaliação de uma expressão, que pode ser útil quando a avaliação implícita de propriedades e chamadas de função implícitas está desativada.|Mensagem "a avaliação da função implícita está desativada pelo usuário"|\<value>|
|d|inteiro decimal|0x0065|101|
|dinâmico|Exibe o objeto especificado usando um Modo de Exibição Dinâmico|Exibe todos os membros do objeto, incluindo a exibição dinâmica|Exibe somente a exibição dinâmica|
|h|inteiro hexadecimal|61541|0x0000F065|
|nq|cadeia de caracteres sem aspas|"Minha cadeia de caracteres"|Minha cadeia de caracteres|
|nse|Especifica o comportamento, não o formato. Avalia a expressão com "não há efeitos colaterais". Se a expressão não puder ser interpretada e só puder ser resolvida por uma avaliação (como uma chamada de função), você verá um erro em vez disso.|N/D|N/D|
|oculto|Exibe todos os membros públicos e não públicos|Exibe membros públicos|Exibe todos os membros|
|raw|Exibe o item como aparece no nó bruto do item. Válido apenas em objetos proxy.|Dicionário\<T>|Exibição bruta do dicionário\<T>|
|results|Usado com uma variável de um tipo que implementa IEnumerable ou IEnumerable \<T> , geralmente o resultado de uma expressão de consulta. Exibe apenas os membros que contém o resultado da consulta.|Exibe todos os membros|Exibe os membros que atendem às condições da consulta|

## <a name="see-also"></a>Confira também
- [Janelas Watch e QuickWatch](../debugger/watch-and-quickwatch-windows.md)
- [Janelas automáticas e locais](../debugger/autos-and-locals-windows.md)
