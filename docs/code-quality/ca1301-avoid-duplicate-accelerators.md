---
title: 'CA1301: Evitar aceleradores duplicados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f82163b1c377df4c8c7fcbba07672312153dad9b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55916538"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Evitar aceleradores duplicados

|||
|-|-|
|NomeDoTipo|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Categoria|Microsoft.Globalization|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Estende um tipo <xref:System.Windows.Forms.Control?displayProperty=fullName> e contém duas ou mais controles de nível superior que têm chaves de acesso idêntico que são armazenadas em um arquivo de recurso.

## <a name="rule-description"></a>Descrição da regra

Uma chave de acesso, também conhecido como um acelerador, dá ao teclado acesso a um controle usando o **Alt** chave. Quando vários controles têm a mesma chave de acesso, o comportamento da tecla de acesso não é bem definido. O usuário pode não ser capaz de acessar o controle desejado usando a chave de acesso e um controle diferente daquele que destina-se deve estar habilitado.

A implementação atual desta regra ignora os itens de menu. No entanto, os itens de menu no mesmo submenu não devem ter as chaves de acesso idênticos.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, defina chaves de acesso exclusivo para todos os controles.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um formulário mínimo que contém dois controles que têm chaves de acesso idênticos. As chaves são armazenadas em um arquivo de recurso, que não é exibido. No entanto, seus valores aparecerão no comentado out `checkBox.Text` linhas. O comportamento de aceleradores duplicados pode ser examinado por meio da troca de `checkBox.Text` linhas com suas contrapartes comentadas. No entanto, nesse caso, o exemplo não irá gerar um aviso da regra.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>Consulte também

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Recursos em aplicativos de área de trabalho](/dotnet/framework/resources/index)