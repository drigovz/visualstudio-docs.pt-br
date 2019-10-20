---
title: Como suprimir avisos usando o item de menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96b7433ff4f696989142aa2c2ce47982006b93b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610023"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Como suprimir avisos usando o item de menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[OBSERVAÇÃO]
> Na supressão da origem, não há suporte para projetos de site.

 Você pode usar a janela de análise de código para suprimir avisos de análise de código. Suprimir um aviso não é o mesmo que desabilitá-lo. Quando você suprimi um aviso, ele se aplica somente a uma determinada instância da violação. Outras violações do mesmo aviso ainda serão relatadas na janela de Lista de Erros.

 Depois de executar a análise de código, você pode determinar que um ou mais dos avisos de análise de código exibidos na janela de análise de código não são aplicáveis ao seu aplicativo. Por exemplo, você pode determinar que o código está correto como está. Ou, pode ser o caso em que algumas violações são de baixa prioridade e não serão corrigidas no ciclo de desenvolvimento atual. Independentemente do motivo, geralmente é útil indicar que o aviso não é aplicável para permitir que os membros da equipe saibam que o código foi revisado e que foi determinado que o aviso poderia ser suprimido. Na supressão de origem é útil porque permite que você coloque uma supressão próxima de onde o aviso é gerado.

 Você pode escolher se a supressão será exibida no código-fonte ou no arquivo de supressão global. Algumas supressões devem ser colocadas no arquivo de supressão global. Se esse for o caso, a opção **na fonte** será desabilitada.

### <a name="to-suppress-a-warning-by-using-menu-item"></a>Para suprimir um aviso usando o item de menu

1. No menu **analisar** , escolha **Windows** e, em seguida, escolha **análise de código**.

2. Na janela **análise de código** , selecione o aviso suprimir.

3. Escolha ações, escolha **suprimir mensagem (ns)** e, em seguida, escolha **na origem** ou **no arquivo de supressão do projeto**.

     O aviso específico é suprimido e o aviso é exibido na janela de análise de código com um tachado.

> [!NOTE]
> As supressões que não têm um destino aparecem no arquivo de supressão global.
