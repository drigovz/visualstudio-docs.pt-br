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
ms.openlocfilehash: 5f50be12f4d601161ec20659bbb6b710e5a7cf24
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235172"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Evitar aceleradores duplicados

|||
|-|-|
|NomeDoTipo|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Categoria|Microsoft. Globalization|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa
Um tipo estende <xref:System.Windows.Forms.Control?displayProperty=fullName> e contém dois ou mais controles de nível superior que têm chaves de acesso idênticas que são armazenadas em um arquivo de recurso.

## <a name="rule-description"></a>Descrição da regra

Uma chave de acesso, também conhecida como acelerador, permite o acesso ao teclado para um controle usando a tecla **ALT** . Quando vários controles têm a mesma chave de acesso, o comportamento da tecla de acesso não é bem definido. O usuário pode não conseguir acessar o controle pretendido usando a chave de acesso, e um controle diferente daquele que se destina pode ser habilitado.

A implementação atual dessa regra ignora itens de menu. No entanto, os itens de menu no mesmo submenu não devem ter chaves de acesso idênticas.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, defina chaves de acesso exclusivas para todos os controles.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra uma forma mínima que contém dois controles que têm chaves de acesso idênticas. As chaves são armazenadas em um arquivo de recurso, que não é mostrado. No entanto, seus valores aparecem nas `checkBox.Text` linhas comentadas. O comportamento de aceleradores duplicados pode ser examinado pela troca `checkBox.Text` de linhas com suas contrapartes comentadas. No entanto, nesse caso, o exemplo não gerará um aviso da regra.

[!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>Consulte também

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Recursos em aplicativos de área de trabalho](/dotnet/framework/resources/index)