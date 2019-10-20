---
title: 'CA1030: usar eventos quando apropriado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7ab3a576b5014799e470260567a4942b5c3ef9de
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661917"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: usar eventos quando apropriado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Categoria|Microsoft. Design|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um nome de método público, protegido ou privado começa com um dos seguintes:

- Complemento

- RemoveOn

- Ativar

- Gera

## <a name="rule-description"></a>Descrição da Regra
 Essa regra detecta métodos que têm nomes que seriam usados normalmente em eventos. Eventos seguem o observador ou o padrão de design de publicação/assinatura; Eles são usados quando uma alteração de estado em um objeto deve ser comunicada a outros objetos. Se um método é chamado em resposta a uma alteração de estado claramente definida, o método deve ser invocado por um manipulador de eventos. Os objetos que chamam o método devem acionar eventos, em vez de chamar o método diretamente.

 Alguns exemplos comuns de eventos são encontrados em aplicativos de interface do usuário em que uma ação do usuário, como clicar em um botão, faz com que um segmento de código seja executado. O modelo de evento [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] não está limitado às interfaces do usuário; Ele deve ser usado em qualquer lugar em que você deve comunicar alterações de estado em um ou mais objetos.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Se o método for chamado quando o estado de um objeto for alterado, considere alterar o design para usar o modelo de evento [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprimir um aviso dessa regra se o método não funcionar com o modelo de evento [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].
