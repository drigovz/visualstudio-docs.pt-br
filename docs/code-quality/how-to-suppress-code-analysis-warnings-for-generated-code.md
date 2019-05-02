---
title: 'Como: Suprimir avisos de análise de código para código gerenciado'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a69d2006f5fbacd213f86f2091c019fcc468d10
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63403136"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Como: Suprimir avisos de análise de código para código gerenciado
Compiladores de código gerenciado com frequência geram código que é adicionado a um projeto para facilitar o desenvolvimento rápido de código. Além disso, os desenvolvedores normalmente usam ferramentas de terceiros para ajudar a desenvolver aplicativos rapidamente. Essas ferramentas também geram código que é adicionado ao projeto.

 Você talvez queira ver as violações de regra que detecta de análise de código no código gerado. No entanto, talvez você não queira vê-los se você não pode exibir e manter o código que contém a violação.

 O **Suprimir resultados do código gerado** caixa de seleção na página de propriedades de análise de código de um projeto permite que você selecione se deseja ver avisos de análise de código do código gerado por uma ferramenta de terceiros.

> [!NOTE]
> Essa opção não suprime erros de análise de código e avisos do código gerado quando os erros e avisos que aparecem em formulários e modelos. Você pode exibir e manter o código-fonte para um formulário ou um modelo.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Para suprimir avisos para código gerado em um projeto

1. Clique com botão direito no projeto no Gerenciador de soluções e, em seguida, clique em **propriedades**.

2. Clique em **análise de código**.

3. Selecione o **Suprimir resultados do código gerado** caixa de seleção.