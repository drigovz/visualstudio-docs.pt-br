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
ms.openlocfilehash: d2caeb78af5fed0c74c02c6e3f578fa34e765355
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920368"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Inicializar campos estáticos de tipo de valor em linha

|||
|-|-|
|NomeDoTipo|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
Um tipo de valor declara um construtor estático explícito.

## <a name="rule-description"></a>Descrição da regra
Quando um valor tipo é declarado, ele passa por uma inicialização padrão onde todos os campos de tipo de valor são definidos como zero e todos os campos de tipo de referência `null` são`Nothing` definidos como (em Visual Basic). Um construtor estático explícito só é garantido para execução antes de um construtor de instância ou membro estático do tipo ser chamado. Portanto, se o tipo for criado sem chamar um construtor de instância, não haverá garantia de que o construtor estático seja executado.

Se todos os dados estáticos forem inicializados em linha e nenhum construtor estático explícito C# for declarado, os compiladores `beforefieldinit` e Visual Basic adicionarão o sinalizador à definição de classe MSIL. Os compiladores também adicionam um construtor estático privado que contém o código de inicialização estático. Esse construtor estático privado tem a garantia de ser executado antes que qualquer campo estático do tipo seja acessado.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, inicialize todos os dados estáticos quando ele estiver declarado e remova o construtor estático.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="related-rules"></a>Regras relacionadas
[CA1810: Inicializar campos estáticos de tipo de referência embutidos](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)