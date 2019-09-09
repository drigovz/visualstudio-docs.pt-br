---
title: Suprimir violações de análise de código para código gerado
ms.date: 05/13/2019
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ee4e3df94e46b4d3cc996a23fc1e40401195e21
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551126"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Como: Suprimir avisos de análise de código para código gerenciado

O código gerado inclui o código que é adicionado ao seu projeto por compiladores de código gerenciado ou por ferramentas de terceiros. Talvez você queira ver as violações de regra que a análise de código descobre no código gerado. No entanto, como não é possível exibir e manter o código que contém as violações, talvez você não queira vê-las.

A caixa de seleção **suprimir resultados do código gerado** na página de propriedades análise de código de um projeto permite que você selecione se deseja mostrar avisos de análise de código do código gerado por uma ferramenta de terceiros.

> [!NOTE]
> Essa opção não suprime erros de análise de código e avisos do código gerado quando os erros e avisos que aparecem em formulários e modelos. Você pode exibir e manter o código-fonte de um formulário ou de um modelo.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Para suprimir avisos de código gerado em um projeto

1. Clique com o botão direito do mouse no projeto em **Gerenciador de soluções** e clique em **Propriedades**.

2. Escolha a guia **análise de código** .

3. Marque a caixa de seleção **suprimir resultados do código gerado** .

> [!NOTE]
> Você só pode suprimir avisos da análise herdada. No momento, não é possível suprimir avisos de análise de código de [analisadores](roslyn-analyzers-overview.md).