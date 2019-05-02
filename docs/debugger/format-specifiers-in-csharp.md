---
title: Formatar especificadores no depurador (c#) | Microsoft Docs
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: caaf36e286f1bdc664ebdbb10e3baf7ed28183e7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62849824"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Especificadores de formato em c# no depurador do Visual Studio
Você pode alterar o formato no qual um valor é exibido na **inspeção** janela usando especificadores de formato. Você também pode usar especificadores de formato na **Immediate** janela, o **comando** janela, na [tracepoints](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)e em janelas de origem. Se você pausar em uma expressão nessas janelas, o resultado será exibido em uma [DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) na exibição do formato especificado.

Para usar um especificador de formato, insira a expressão variável, seguida por uma vírgula e o especificador apropriado.

## <a name="set-format-specifiers"></a>Especificadores de formato de conjunto
Vamos usar o código de exemplo a seguir:

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Adicione a `my_var1` variável para o **inspeção** janela durante a depuração, **depurar** > **Windows** > **Assista**  >  **Assista 1**. Em seguida, a variável com o botão direito e selecione **exibição Hexadecimal**. Agora o **inspeção** janela mostra o valor 0x0065. Para ver esse valor como um inteiro decimal em vez de um inteiro hexadecimal, adicione o especificador de formato decimal **, d** na **nome** coluna após o nome da variável. O **valor** coluna agora mostra **101**.

![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")

::: moniker range=">= vs-2019" 

Você pode exibir e selecionar em uma lista de especificadores de formato disponíveis, acrescentando uma vírgula (,) para o valor de **inspeção** janela. 

![FormatSpecCSharp](../debugger/media/vs-2019/format-specs-csharp.png "FormatSpecCSharp")

::: moniker-end

## <a name="format-specifiers"></a>Especificadores de formato
A tabela a seguir descreve o C# formatar os especificadores de depurador do Visual Studio.

|Especificador|Formatar|Valor original de inspeção|Telas|
|---------------|------------|--------------------------|--------------|
|CA|Forçar a avaliação de uma expressão, que pode ser útil quando a avaliação implícita das propriedades e chamadas de função implícitas é desativada.|"Avaliação da função implícita está desativada pelo usuário" da mensagem|\<valor>|
|d|inteiro decimal|0x0065|101|
|dinâmica|Exibe o objeto especificado usando um Modo de Exibição Dinâmico|Exibe todos os membros do objeto, incluindo o modo de exibição dinâmico|Exibe apenas o modo de exibição dinâmico|
|h|inteiro hexadecimal|61541|0x0000F065|
|nq|cadeia de caracteres sem aspas|"Minha cadeia de caracteres"|Minha cadeia de caracteres|
|nSe|Especifica o comportamento, não o formato. Avalia a expressão "Sem efeitos colaterais". Se a expressão não pode ser interpretada e só pode ser resolvida por uma avaliação (como uma chamada de função), você verá um erro em vez disso.|N/D|N/D|
|oculto|Exibe todos os membros públicos e não públicos|Exibe membros públicos|Exibe todos os membros|
|bruto|Exibe o item como aparece no nó bruto do item. Válido apenas em objetos proxy.|Dicionário\<T >|Modo de exibição bruto do dicionário\<T >|
|resultados|Usado com uma variável de um tipo que implementa IEnumerable ou IEnumerable\<T >, geralmente o resultado de uma expressão de consulta. Exibe apenas os membros que contém o resultado da consulta.|Exibe todos os membros|Exibe os membros que atendam as condições da consulta|

## <a name="see-also"></a>Consulte também
- [Janelas Inspeção e QuickWatch](../debugger/watch-and-quickwatch-windows.md)
- [Janelas automáticas e locais](../debugger/autos-and-locals-windows.md)
