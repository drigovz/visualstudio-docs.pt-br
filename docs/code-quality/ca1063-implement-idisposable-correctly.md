---
title: 'CA1063: Implementar IDisposable corretamente'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 8b29c9ed644c223488261333e79f17229bd4b7a3
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235296"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Implementar IDisposable corretamente

|||
|-|-|
|NomeDoTipo|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Categoria|Microsoft.Design|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

A <xref:System.IDisposable?displayProperty=nameWithType> interface não está implementada corretamente. Os motivos possíveis para isso incluem:

- <xref:System.IDisposable>é reimplementado na classe.

- `Finalize`é substituído novamente.

- `Dispose()`é substituído.

- O `Dispose()` método não é público, [lacrado](/dotnet/csharp/language-reference/keywords/sealed)ou chamado **Dispose**.

- `Dispose(bool)`Não é protegido, virtual ou não lacrado.

- Em tipos sem lacre, `Dispose()` é necessário chamar. `Dispose(true)`

- Para tipos sem lacre, a `Finalize` implementação não chama um ou ambos `Dispose(bool)` ou o finalizador de classe base.

A violação de qualquer um desses padrões dispara CA1063 de aviso.

Todo tipo sem lacre que declara e implementa a <xref:System.IDisposable> interface deve fornecer seu próprio `protected virtual void Dispose(bool)` método. `Dispose()`deve chamar `Dispose(true)`, e o finalizador deve chamar `Dispose(false)`. Se você criar um tipo sem lacre que declare e implemente a <xref:System.IDisposable> interface, deverá defini `Dispose(bool)` -la e chamá-la. Para obter mais informações, consulte [limpar recursos não gerenciados (guia .net)](/dotnet/standard/garbage-collection/unmanaged) e [padrão Dispose](/dotnet/standard/design-guidelines/dispose-pattern).

Por padrão, essa regra só examina os tipos visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Todos <xref:System.IDisposable> os tipos devem implementar o [padrão Dispose](/dotnet/standard/design-guidelines/dispose-pattern) corretamente.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Examine seu código e determine quais das seguintes resoluções corrigirão essa violação:

- Remova <xref:System.IDisposable> da lista de interfaces que são implementadas pelo seu tipo e substitua a implementação de descarte de classe base em vez disso.

- Remova o finalizador do seu tipo, substitua Dispose (descarte bool) e coloque a lógica de finalização no caminho do código onde "descartar" é falso.

- Override Dispose (descarte de bool) e coloca a lógica de descarte no caminho de código onde ' disposição ' é true.

- Certifique-se de que Dispose () seja declarado como público e [lacrado](/dotnet/csharp/language-reference/keywords/sealed).

- Renomeie o método Dispose para **descartar** e certificar-se de que ele está declarado como público e [lacrado](/dotnet/csharp/language-reference/keywords/sealed).

- Certifique-se de que Dispose (bool) seja declarado como protegido, virtual e não lacrado.

- Modifique Dispose () para que ele chame Dispose (true) e, em <xref:System.GC.SuppressFinalize%2A> seguida, chame na instância do`this`objeto atual `Me` (ou em Visual Basic) e, em seguida, retorna.

- Modifique o finalizador para que ele chame Dispose (false) e, em seguida, retorne.

- Se você criar um tipo sem lacre que declare e implemente a <xref:System.IDisposable> interface, certifique-se de que a implementação de <xref:System.IDisposable> segue o padrão descrito anteriormente nesta seção.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.

## <a name="configurability"></a>Configurabilidade

Se você estiver executando essa regra por meio de [analisadores do FxCop](install-fxcop-analyzers.md) (e não com a análise herdada), poderá configurar em quais partes de sua base de código executar essa regra, com base em sua acessibilidade. Por exemplo, para especificar que a regra deve ser executada somente na superfície da API não pública, adicione o seguinte par chave-valor a um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1063.api_surface = private, internal
```

Você pode configurar essa opção apenas para essa regra, para todas as regras ou para todas as regras nesta categoria (Design). Para obter mais informações, consulte [Configurar analisadores de FxCop](configure-fxcop-analyzers.md).

## <a name="pseudo-code-example"></a>Exemplo de pseudo-código

O pseudocódigo a seguir fornece um exemplo geral de como Dispose (bool) deve ser implementado em uma classe que usa recursos gerenciados e nativos.

```csharp
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

    // Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }

    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }

    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```

## <a name="see-also"></a>Consulte também

- [Padrão Dispose (diretrizes de design de estrutura)](/dotnet/standard/design-guidelines/dispose-pattern)
- [Limpar recursos não gerenciados (guia .NET)](/dotnet/standard/garbage-collection/unmanaged)