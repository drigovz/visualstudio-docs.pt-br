---
title: 'CA1726: Use termos preferenciais | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e31c459d2d5ce8dc114605716c09f8360eca23d3
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2019
ms.locfileid: "59000344"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Usar termos preferenciais
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para a documentação mais recente do Visual Studio, consulte [CA1726: Use termos preferenciais](https://docs.microsoft.com/visualstudio/code-quality/ca1726-use-preferred-terms) em docs.microsoft.com.  
  
|||  
|-|-|  
|NomeDoTipo|UsePreferredTerms|  
|CheckId|CA1726|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Interrupção - quando acionado em assemblies<br /><br /> Separação de não - quando disparado em parâmetros de tipo|  
  
## <a name="cause"></a>Causa  
 O nome de um identificador visível externamente inclui um termo para o qual existe um termo preferido, alternativo. Como alternativa, o nome inclui o termo sinalizador ou sinalizadores.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Esta regra analisa um identificador em tokens. Cada token único e cada combinação contígua de token dupla é comparado com os termos que são criados para a regra e na seção preterido de dicionários personalizados. A tabela a seguir mostra os termos que são incorporados a regra e suas alternativas preferenciais.  
  
|Termo obsoleto|Termo preferencial|  
|-------------------|--------------------|  
|não são|AreNot|  
|Cancelada|Cancelado|  
|Não é possível|Não é possível|  
|ComPlus|EnterpriseServices|  
|Não foi possível|CouldNot|  
|Didnt|DidNot|  
|Doesnt|DoesNot|  
|Não|DoNot|  
|Sinalizador ou sinalizadores|Não há nenhum termo de substituição. Não use.|  
|não tinha|HadNot|  
|Ainda não|HasNot|  
|Havent|HaveNot|  
|Índices|Índices|  
|Isnt|IsNot|  
|LogIn|LogOn|  
|LogOut|Fazer LogOff|  
|Shouldnt|ShouldNot|  
|SignOn|SignIn|  
|SignOff|SignOut|  
|Wasnt|WasNot|  
|não foram|WereNot|  
|Wont|WillNot|  
|Wouldnt|WouldNot|  
|Gravável|Gravável|  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação dessa regra, substitua o termo com o termo preferencial de alternativo.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Suprima um aviso nessa regra somente se o nome do identificador é intencional e se relacionam especificamente a termo original em vez do termo preferencial.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [Avisos de Nomenclatura](../code-quality/naming-warnings.md)
