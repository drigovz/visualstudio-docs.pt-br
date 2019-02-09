---
title: 'CA1713: Eventos não devem ter o prefixo anterior ou posterior'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8dba144740a2a39494323a456cddf90131e35c6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920321"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: Eventos não devem ter o prefixo anterior ou posterior

|||
|-|-|
|NomeDoTipo|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O nome de um evento começa com 'Before' ou 'After'.

## <a name="rule-description"></a>Descrição da regra
 Nomes de evento devem descrever a ação que aciona o evento. Para nomear eventos relacionados acionados em uma sequência específica, use o presente ou o pretérito para indicar a posição relativa na sequência de ações. Por exemplo, quando um par de eventos de nomenclatura que é gerado ao fechar um recurso, você pode nomeá-lo 'De fechamento' e 'Fechado', em vez de 'BeforeClose' e 'AfterClose'.

 Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Remover o prefixo do nome do evento e considere alterar o nome para usar o presente ou o pretérito de um verbo.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima um aviso nessa regra.