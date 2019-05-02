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
ms.openlocfilehash: 67dab4c732faa04af44800f740d78c4ce4f9dc80
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59664106"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Usar termos preferenciais
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para a documentação mais recente do Visual Studio, consulte [CA1726: Use termos preferenciais](https://docs.microsoft.com/visualstudio/code-quality/ca1726-use-preferred-terms).  
  
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
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` ou `Flags`|Não há nenhum termo de substituição. Não use.|
|`Hadnt`|`HadNot`|
|`Hasnt`|`HasNot`|
|`Havent`|`HaveNot`|
|`Indices`|`Indexes`|
|`Isnt`|`IsNot`|
|`LogIn`|`LogOn`|
|`LogOut`|`LogOff`|
|`Shouldnt`|`ShouldNot`|
|`SignOn`|`SignIn`|
|`SignOff`|`SignOut`|
|`Wasnt`|`WasNot`|
|`Werent`|`WereNot`|
|`Wont`|`WillNot`|
|`Wouldnt`|`WouldNot`|
|`Writeable`|`Writable`|
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação dessa regra, substitua o termo com o termo preferencial de alternativo.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Suprima um aviso nessa regra somente se o nome do identificador é intencional e se relacionam especificamente a termo original em vez do termo preferencial.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [Avisos de Nomenclatura](../code-quality/naming-warnings.md)
