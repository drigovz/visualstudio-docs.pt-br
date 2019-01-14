---
title: 'DA0010: Função GetHashCode dispendiosa | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ddf59bdf6ad356a36a730982b7ac0b681bd66d3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53932334"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Função GetHashCode dispendiosa

|||  
|-|-|  
|ID de regra|DA0010|  
|Categoria|Uso do .NET Framework|  
|Métodos de criação de perfil|Amostragem<br /><br /> Memória do .NET|  
|Mensagem|As funções de GetHashCode devem ser baratas e não podem alocar nenhuma memória. Se for possível, reduza a complexidade da função de código de hash.|  
|Tipo de mensagem|Aviso|  

## <a name="cause"></a>Causa  
 As chamadas para o método GetHashCode do tipo são uma parte significativa dos dados de criação de perfil ou do método de alocação de memória.  

## <a name="rule-description"></a>Descrição da regra  
 O hash é uma técnica para localizar rapidamente um item específico em uma coleção grande. As tabelas de hash podem ser grandes e dão suporte às altas taxas de acesso e, por isso, devem ser eficientes. No entanto, uma implicação desse requisito é que os métodos GetHashCode no .NET Framework não devem alocar memória. A alocação de memória aumentará a carga no coletor de lixo e exporá o método a possíveis atrasos se for necessário executar de uma coleta de lixo como um resultado da solicitação de alocação.  

## <a name="how-to-fix-violations"></a>Como corrigir violações  
 Reduza a complexidade do método.