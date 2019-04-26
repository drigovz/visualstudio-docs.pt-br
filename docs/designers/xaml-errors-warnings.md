---
title: Avisos e Erros XAML
ms.date: 03/06/2018
ms.topic: conceptual
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: karann
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3ae795b464d8a693371b1ebb9238a897debbf02
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62892609"
---
# <a name="xaml-errors-and-warnings"></a>Avisos e erros de XAML

Ao criar XAML, o Visual Studio analisa o código conforme você digita. Um rabisco aparece em uma linha de código quando um erro é detectado. Se você passar o mouse sobre o rabisco, verá mais informações sobre o erro ou aviso. Em alguns erros e avisos, uma lâmpada de Ação rápida é exibida. Ela também aparece ao pressionar **Ctrl**+**.** o atalho de teclado exibe as opções para corrigir o problema.

## <a name="error-types"></a>Tipos de erro

Em segundo plano, várias ferramentas analisam o XAML em paralelo. Erros de XAML são categorizados em um dos três seguintes tipos, com base na ferramenta que detectou o erro:

|**Erro detectado por**|**Formato do código de erro**|
| - |-----------------|
|Serviço de linguagem XAML (Editor XAML)|XLSxxxx|
|XAML Designer|XDGxxxx|
|Editar e Continuar em XAML|XECxxxx|

> [!Note]
> Nem todos os erros ou avisos têm um código correspondente. Geralmente, esses erros são do XAML Designer.

## <a name="suppress-xaml-designer-errors"></a>Suprimir erros do XAML Designer

Abra a caixa de diálogo **Opções** selecionando **Ferramentas > Opções** e, em seguida, selecione **Editor de Texto > XAML > Diversos**.

Desmarque a caixa de seleção **Mostrar erros detectados pelo XAML Designer**.

![Suprimir erros do XAML Designer](../designers/media/suppress_xaml_designer_errors.png)
