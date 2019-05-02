---
title: 'CA1713: Eventos não devem ter antes ou depois do prefixo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6a36f9c8ce788b30f14d8ca0ce9d565ab45975a5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62535198"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: Eventos não devem ter o prefixo anterior ou posterior
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O nome de um evento começa com 'Before' ou 'After'.

## <a name="rule-description"></a>Descrição da Regra
 Nomes de evento devem descrever a ação que aciona o evento. Para nomear eventos relacionados acionados em uma sequência específica, use o presente ou o pretérito para indicar a posição relativa na sequência de ações. Por exemplo, quando um par de eventos de nomenclatura que é gerado ao fechar um recurso, você pode nomeá-lo 'De fechamento' e 'Fechado', em vez de 'BeforeClose' e 'AfterClose'.

 Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Remover o prefixo do nome do evento e considere alterar o nome para usar o presente ou o pretérito de um verbo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.
