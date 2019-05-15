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
ms.openlocfilehash: 6a7990f5e9fa1893d8813b1307ab6a0a7fee46be
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65613563"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Como: Suprimir avisos de análise de código para código gerenciado

Código gerado inclui o código que é adicionado ao seu projeto por compiladores de código gerenciado ou ferramentas de terceiros. Você talvez queira ver as violações de regra que detecta de análise de código no código gerado. No entanto, desde que você não pode exibir e manter o código que contém as violações, talvez não queira vê-los.

O **Suprimir resultados do código gerado** caixa de seleção na página de propriedades de análise de código, de um projeto permite que você selecione se deseja mostrar código avisos da análise do código gerado por uma ferramenta de terceiros.

> [!NOTE]
> Essa opção não suprime erros de análise de código e avisos do código gerado quando os erros e avisos que aparecem em formulários e modelos. Você pode exibir e manter o código-fonte para um formulário ou um modelo.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Para suprimir avisos para código gerado em um projeto

1. Clique com botão direito no projeto no **Gerenciador de soluções** e, em seguida, clique em **propriedades**.

2. Escolha o **análise de código** guia.

3. Selecione o **Suprimir resultados do código gerado** caixa de seleção.

> [!NOTE]
> Você só pode suprimir avisos da análise de código estático. No momento, você não pode suprimir avisos da análise de código do [analisadores](roslyn-analyzers-overview.md).