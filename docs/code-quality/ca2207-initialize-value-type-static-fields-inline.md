---
title: 'CA2207: Inicializar campos estáticos de tipo de valor em linha'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b00403af731439ecef4667c632e53b52670afff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796686"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Inicializar campos estáticos de tipo de valor em linha

|||
|-|-|
|NomeDoTipo|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Um tipo de valor declara um construtor estático explícito.

## <a name="rule-description"></a>Descrição da regra
 Quando um tipo de valor é declarado, ele passa por uma inicialização padrão em que todos os campos de tipo de valor são definidos como zero e todos os campos de tipo de referência são definidos como `null` (`Nothing` no Visual Basic). Um construtor estático explícito é garantido somente para executar antes de um construtor de instância ou um membro estático do tipo é chamado. Portanto, se o tipo é criado sem chamar um construtor de instância, o construtor estático não é garantido para ser executado.

 Se todos os dados estáticos é inicializado embutido e nenhum construtor estático explícito é declarado, os compiladores c# e Visual Basic, adicione o `beforefieldinit` sinalizador à definição de classe MSIL. Os compiladores também adicionar um construtor estático privado que contém o código de inicialização estática. Este construtor estático privado é garantido para ser executado antes de qualquer campo estático do tipo é acessado.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra inicializar todos os dados estáticos quando ele é declarado e remova o construtor estático.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima um aviso nessa regra.

## <a name="related-rules"></a>Regras relacionadas
 [CA1810: Inicializar campos estáticos de tipo de referência embutido](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)