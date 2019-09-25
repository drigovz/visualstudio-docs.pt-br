---
title: 'CA2115: Chamar GC.KeepAlive ao usar recursos nativos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: eb6d28e15870907034479e698ba8e7464f4f5159
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232717"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: Chamar GC.KeepAlive ao usar recursos nativos

|||
|-|-|
|NomeDoTipo|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Categoria|Microsoft.Security|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um método declarado em um tipo com um finalizador faz referência <xref:System.IntPtr?displayProperty=fullName> a <xref:System.UIntPtr?displayProperty=fullName> um campo ou, mas não <xref:System.GC.KeepAlive%2A?displayProperty=fullName>chama.

## <a name="rule-description"></a>Descrição da regra

A coleta de lixo Finaliza um objeto se não houver mais referências a ele no código gerenciado. Referências não gerenciadas a objetos não impedem a coleta de lixo. Esta regra detecta erros que podem ocorrer porque um recurso não gerenciado está sendo finalizado, enquanto ainda está sendo usado em código não gerenciado.

Essa regra pressupõe que <xref:System.IntPtr> e <xref:System.UIntPtr> campos armazenem ponteiros para recursos não gerenciados. Como a finalidade de um finalizador é liberar recursos não gerenciados, a regra pressupõe que o finalizador liberará o recurso não gerenciado apontado pelos campos de ponteiro. Essa regra também pressupõe que o método está referenciando o campo ponteiro para passar o recurso não gerenciado para código não gerenciado.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, adicione <xref:System.GC.KeepAlive%2A> uma chamada para ao método, passando a instância atual (`this` no C# e C++) como o argumento. Posicione a chamada após a última linha de código em que o objeto deve ser protegido da coleta de lixo. Imediatamente após a chamada para <xref:System.GC.KeepAlive%2A>, o objeto é considerado novamente pronto para coleta de lixo, supondo que não haja nenhuma referência gerenciada a ele.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Essa regra faz algumas suposições que podem levar a falsos positivos. Você pode suprimir com segurança um aviso dessa regra se:

- O finalizador não libera o conteúdo do <xref:System.IntPtr> campo ou <xref:System.UIntPtr> referenciado pelo método.

- O método não passa o campo <xref:System.IntPtr> ou <xref:System.UIntPtr> para o código não gerenciado.

Revise cuidadosamente outras mensagens antes de exclui-las. Essa regra detecta erros que são difíceis de reproduzir e depurar.

## <a name="example"></a>Exemplo

No exemplo a seguir, `BadMethod` não inclui uma chamada para `GC.KeepAlive` e, portanto, viola a regra. `GoodMethod`contém o código corrigido.

> [!NOTE]
> Este exemplo é pseudocódigo. Embora o código seja compilado e executado, o aviso não é acionado porque um recurso não gerenciado não é criado ou liberado.

[!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]

## <a name="see-also"></a>Consulte também

- <xref:System.GC.KeepAlive%2A?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- [Padrão de descarte](/dotnet/standard/design-guidelines/dispose-pattern)