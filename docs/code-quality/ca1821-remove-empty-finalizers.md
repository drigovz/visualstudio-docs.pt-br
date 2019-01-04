---
title: 'CA1821: Remover finalizadores vazios'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d155d8846828d8806fb4927d39120bfad2b01f33
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53937329"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Remover finalizadores vazios

|||
|-|-|
|NomeDoTipo|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Um tipo implementa um finalizador que está vazia, chama apenas o finalizador do tipo base ou chama somente emitidos condicionalmente métodos.

## <a name="rule-description"></a>Descrição da regra
 Sempre que possível, evite finalizadores por conta da sobrecarga adicional no desempenho envolvida no acompanhamento do tempo de vida do objeto. O coletor de lixo executará o finalizador antes que ele coleta o objeto. Isso significa que as duas coleções será necessárias para coletar o objeto. Um finalizador vazio incorre essa sobrecarga agregada sem nenhum benefício.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Remova o finalizador vazio. Se um finalizador é necessário para a depuração, coloque o finalizador todo `#if DEBUG / #endif` diretivas.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima uma mensagem a partir dessa regra. Falha ao suprimir a finalização reduz o desempenho e não oferece nenhum benefício.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um finalizador vazio que deve ser removido, um finalizador que deve ser colocado entre `#if DEBUG / #endif` diretivas e um finalizador que usa o `#if DEBUG / #endif` diretivas corretamente.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]