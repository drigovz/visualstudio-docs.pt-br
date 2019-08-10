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
ms.openlocfilehash: e4e068fee014d767b7afcdf8183ac6611b299f36
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921582"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Usar termos preferenciais

|||
|-|-|
|NomeDoTipo|UsePreferredTerms|
|CheckId|CA1726|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra-quando acionado em assemblies<br /><br /> Não separável-quando acionado em parâmetros de tipo|

## <a name="cause"></a>Causa

O nome de um identificador visível externamente inclui um termo para o qual existe um termo preferido, alternativo. Ou, o nome inclui o sinalizador de termo ou sinalizadores.

## <a name="rule-description"></a>Descrição da regra

Essa regra analisa um identificador em tokens. Cada único token e uma combinação de token duplo contígua é comparada com os termos criados na regra e na seção preterida de quaisquer dicionários personalizados. A tabela a seguir mostra os termos que são criados na regra e suas alternativas preferenciais.

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
Para corrigir uma violação dessa regra, substitua o termo pelo termo alternativo preferido.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Suprimir um aviso dessa regra somente se o nome do identificador for intencional e estiver relacionado especificamente ao termo original em vez do termo preferido.

## <a name="related-rules"></a>Regras relacionadas
[Avisos de Nomenclatura](../code-quality/naming-warnings.md)