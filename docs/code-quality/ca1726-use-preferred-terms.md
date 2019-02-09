---
title: 'CA1726: Usar termos preferenciais'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 469025e5856f284f4d8887b351865a0304e4d35c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55917305"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Usar termos preferenciais

|||
|-|-|
|NomeDoTipo|UsePreferredTerms|
|CheckId|CA1726|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Interrupção - quando acionado em assemblies<br /><br /> Separação de não - quando disparado em parâmetros de tipo|

## <a name="cause"></a>Causa

O nome de um identificador visível externamente inclui um termo para o qual existe um termo preferido, alternativo. Ou, o nome inclui o termo sinalizador ou sinalizadores.

## <a name="rule-description"></a>Descrição da regra

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

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, substitua o termo com o termo preferencial de alternativo.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Suprima um aviso nessa regra somente se o nome do identificador é intencional e se relacionam especificamente a termo original em vez do termo preferencial.

## <a name="related-rules"></a>Regras relacionadas
 [Avisos de Nomenclatura](../code-quality/naming-warnings.md)