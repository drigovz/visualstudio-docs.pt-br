---
title: Como impor código passível de manutenção com uma política de check-in de análise de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0d54ca9a31e8a1bbd2496bf8689a119e53580c79
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660213"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Como impor um código com facilidade de manutenção com uma política de check-in de análise do código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os desenvolvedores podem usar a ferramenta de métricas de código para medir a complexidade e a manutenção de seu código, mas não podem invocar as métricas de código como parte de uma política de check-in. No entanto, uma equipe pode habilitar regras de análise de código que verificam a conformidade de seus códigos com padrões de métricas de código e impõem as regras por meio de políticas de check-in. Para obter mais informações sobre métricas de código, consulte [valores de métricas de código](../code-quality/code-metrics-values.md).

 Os desenvolvedores podem habilitar a profundidade de herança, acoplamento de classes, índice de facilidade de manutenção e regras de complexidade para impor o código passível de manutenção por meio de políticas de check-in de análise de código. Todas as quatro regras são encontradas na categoria "regras de manutenção" no editor de política de análise de código.

 Os administradores do controle de versão para [!INCLUDE[esprfound](../includes/esprfound-md.md)] podem adicionar as regras de manutenção da análise de código aos requisitos da política de check-in. Essas políticas de check-in exigem que os desenvolvedores executem a análise de código com base nessas alterações de regra antes de iniciar um check-in.

### <a name="to-open-the-code-analysis-policy-editor"></a>Para abrir o editor de políticas de análise de código

1. Em **Team Explorer**, clique com o botão direito do mouse no projeto de equipe, clique em **configurações do projeto de equipe**e clique em controle do **código-fonte**.

     A caixa de diálogo **controle do código-fonte** é exibida.

2. Na guia **política de check-in** e clique em **Adicionar**.

     A caixa de diálogo **Adicionar política de check-in** é exibida.

3. Na lista **política de check-in** , marque a caixa de seleção **análise de código** e clique em **OK**.

     A caixa de diálogo **Editor de políticas de análise de código** é exibida.

### <a name="to-enable-code-analysis-maintainability-rules"></a>Para habilitar regras de manutenção da análise de código

1. Na caixa de diálogo **Editor de políticas de análise de código** , em configurações de **regra**, expanda o nó **regras de manutenção** .

2. Marque as caixas de seleção para as seguintes regras:

    - Profundidade de herança: **CA1501 AvoidExcessiveInheritance** -Threshold: aviso em mais de 5 níveis de profundidade

    - Complexidade: **CA1502 AvoidExcessiveComplexity** -Threshold: aviso em mais de 25

    - Índice de facilidade de manutenção: **CA1505 AvoidUnmaintainableCode** -Threshold: aviso em menos de 20

    - Acoplamento de classe: **CA1506 AvoidExcessiveClassCoupling** -Threshold: aviso em mais de 80 para uma classe e mais de 30 para um método

    - Além disso, se você quiser uma violação de regra para impedir uma compilação, marque a caixa de seleção **tratar aviso como um erro** ao lado da descrição da regra.

3. Clique em **OK**. A nova política de check-in agora se aplica a check-ins futuros.

## <a name="see-also"></a>Consulte também
 [Valores de métricas de código](../code-quality/code-metrics-values.md) [criando e usando políticas de check-in de análise de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
