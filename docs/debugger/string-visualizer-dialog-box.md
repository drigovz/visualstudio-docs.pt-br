---
title: Caixa de diálogo Visualizador de cadeia de caracteres | Microsoft Docs
ms.date: 10/10/2018
ms.custom: seoapril2019
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10e7e50ffc0cb61bd036bef65c554e8147eecc09
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430827"
---
# <a name="string-visualizer-dialog-box"></a>Caixa de diálogo Visualizador da Cadeia de Caracteres

Enquanto você estiver depurando no Visual Studio, você pode exibir cadeias de caracteres com o Visualizador de cadeias interno. O Visualizador de cadeia de caracteres mostra cadeias muito longas para uma janela de dica de dados ou depurador. Ele também pode ajudá-lo a identificar cadeias de caracteres malformadas.

O Visualizador de cadeia de caracteres interno inclui opções de texto sem formatação, XML, HTML e JSON. Você também pode abrir visualizadores internos para alguns outros tipos, como objetos [DataSet, DataTable e DataView](../debugger/dataset-visualizer-dialog-box.md) , das janelas **automáticas** ou de outro depurador.

> [!NOTE]
> Se você precisar inspecionar elementos de interface do usuário XAML ou WPF em um visualizador, consulte ou [inspecione as propriedades XAML durante a depuração](../xaml-tools/inspect-xaml-properties-while-debugging.md) ou [como usar o Visualizador de árvore do WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md).

Para abrir o Visualizador de cadeia de caracteres, você deve estar em pausa durante a depuração. Focalize uma variável que tenha um valor de cadeia de caracteres de texto sem formatação, XML, HTML ou JSON e selecione o ícone de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ícone do Visualizador").

## <a name="uielement-list"></a>Lista UIElement

O campo **expressão** mostra a variável ou expressão que você está focalizando.

O campo **valor** mostra o valor da cadeia de caracteres. Um **valor** em branco significa que o visualizador escolhido não pode reconhecer a cadeia de caracteres. Por exemplo, o **Visualizador de XML** mostra um **valor** em branco para uma cadeia de texto sem marcas XML ou uma cadeia de caracteres JSON. Para exibir as cadeias de caracteres que o visualizador escolhido não pode reconhecer, escolha o **Visualizador de texto** em vez disso. O **Visualizador de texto** mostra texto sem formatação.

### <a name="json-string-data"></a>Dados de cadeia de caracteres JSON

Uma cadeia de caracteres JSON bem formada é semelhante à ilustração a seguir no visualizador JSON. O JSON malformado pode exibir um ícone de erro (ou em branco, se não reconhecido). Para identificar o erro JSON, copie e cole a cadeia de caracteres em uma ferramenta de refiapoção JSON, como [JSLint](https://www.jslint.com/).

![Visualizador de cadeia de caracteres JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Visualizador de cadeia de caracteres JSON")

### <a name="xml-string-data"></a>Dados de cadeia de caracteres XML

Uma cadeia de caracteres XML bem formada é semelhante à ilustração a seguir no Visualizador de XML. XML malformado pode ser exibido sem as marcas XML, ou em branco, se não for reconhecido.

![Visualizador de cadeia de caracteres XML](../debugger/media/dbg-string-visualizers-xml.png "Visualizador de cadeia de caracteres XML")

### <a name="html-string-data"></a>Dados de cadeia de caracteres HTML

Uma cadeia de caracteres HTML bem formada aparece como se fosse renderizada em um navegador, conforme mostrado na ilustração a seguir. HTML malformado pode ser exibido como texto sem formatação.

![Visualizador de cadeia de caracteres HTML](../debugger/media/dbg-string-visualizers-html.png "Visualizador de cadeia de caracteres HTML")

## <a name="see-also"></a>Consulte também

- [Criar visualizadores personalizados (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Visualizações de dados no Visual Studio para Mac](/visualstudio/mac/data-visualizations)