---
title: 'Como: suprimir avisos de análise de código para código gerado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 52caadd7f4dd9349eccb80a366a1458212aba5ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646271"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Como suprimir avisos de análise do código para código gerenciado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Compiladores de código gerenciado geralmente geram código que é adicionado a um projeto para facilitar o desenvolvimento rápido de código. Além disso, os desenvolvedores geralmente usam ferramentas de terceiros para ajudar a desenvolver aplicativos rapidamente. Essas ferramentas também geram código que é adicionado ao projeto.

 Talvez você queira ver as violações de regra que a análise de código descobre no código gerado. No entanto, talvez você não queira vê-los se não for possível exibir e manter o código que contém a violação.

 A caixa de seleção **suprimir resultados do código gerado** na página de propriedades análise de código de um projeto permite que você selecione se deseja ver avisos de análise de código do código gerado por uma ferramenta de terceiros.

> [!NOTE]
> Essa opção não suprimi erros de análise de código e avisos do código gerado quando os erros e avisos aparecem em formulários e modelos. Você pode exibir e manter o código-fonte de um formulário ou de um modelo.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Para suprimir avisos de código gerado em um projeto

1. Clique com o botão direito do mouse no projeto em Gerenciador de Soluções e clique em **Propriedades**.

2. Clique em **Análise de código**.

3. Marque a caixa de seleção **suprimir resultados do código gerado** .
