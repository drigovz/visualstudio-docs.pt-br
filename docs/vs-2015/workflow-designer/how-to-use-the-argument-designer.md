---
title: 'Como: usar o designer de argumentos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a436d33bbb7c791f3f192357fded779fa77d148d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659108"
---
# <a name="how-to-use-the-argument-designer"></a>Como: Use o designer do argumento
Em comparação com versões anteriores de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], o designer do argumento facilita permitir que os dados e fluam fora de uma atividade. O designer é acessado clicando no botão **argumentos** no canto inferior esquerdo da tela de design. O designer contém uma lista de argumentos que aparecem em um formulário de tabela e podem ser classificados por cada um dos cabeçalhos de coluna, exceto para a coluna **valor padrão** . Cada argumento contiver um nome, a direção de in/out/in-out/property, o tipo, e o valor padrão de expressão (se houver). O nome e o valor padrão de expressão são campos editáveis de texto, e o tipo e direção são gota- suspensa. [!INCLUDE[crabout](../includes/crabout-md.md)] argumentos, consulte [variáveis e argumentos](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).

### <a name="to-create-a-new-argument"></a>Para criar um novo argumento

1. Abra uma solução de fluxo de trabalho ou de atividade em [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. Abra o designer de argumentos clicando no botão **argumentos** no canto inferior esquerdo da tela de design. O designer dos argumentos aparece.

3. Clique na linha vazia rotulada **criar argumento**. Isso adicionará uma nova linha com um novo argumento usando os seguintes valores padrão: argumentx para o **nome** em que x é um inteiro com um valor inicial de 1 que é incrementado automaticamente para criar nomes de argumentos exclusivos, **em** para a **direção**e **cadeia de caracteres** para o tipo de **argumento**. Nenhum valor é adicionado para o **valor padrão**. Você pode alterar esses valores a qualquer momento durante o processo de design de fluxo de trabalho.

    > [!NOTE]
    > Para excluir um argumento, selecione o argumento clicando nele e pressione a tecla **delete** .

## <a name="see-also"></a>Consulte Também
 [Usando o designer de fluxo de trabalho](../workflow-designer/using-the-workflow-designer.md) [variáveis e argumentos](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)